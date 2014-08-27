---
layout: post
title: "Deterministic Builds Part Two: Technical Details"
permalink: deterministic-builds-part-two-technical-details
date: 2013-10-04
author: mikeperry
category: blog
tags: ["cyberpeace", "decentralization", "deterministic builds", "gitian", "National Insecurity Agency", "security"]
---

This is the second post in a two-part series on the build security improvements in the [Tor Browser Bundle 3.0 release cycle](https://blog.torproject.org/category/tags/tbb-30).

The [first post](https://blog.torproject.org/blog/deterministic-builds-part-one-cyberwar-and-global-compromise) described why such security is necessary. This post is meant to describe the technical details with respect to how such builds are produced.

We achieve our build security through a reproducible build process that enables anyone to produce byte-for-byte identical binaries to the ones we release. Elsewhere on the Internet, this process is varyingly called "deterministic builds", "reproducible builds", "idempotent builds", and probably a few other terms, too.

To produce byte-for-byte identical packages, we use [Gitian](http://gitian.org/) to build Tor Browser Bundle 3.0 and above, but that isn't the only option for achieving reproducible builds. We will first describe how we use Gitian, and then go on to enumerate the individual issues that Gitian solves for us, and that we had to solve ourselves through either wrapper scripts, hacks, build process patches, and (in one esoteric case for Windows) direct binary patching.

# Gitian: What is it?

[Gitian](http://gitian.org/howto.html) is a thin wrapper around the Ubuntu virtualization tools written in a combination of Ruby and bash. It was originally developed by Bitcoin developers to ensure the build security and integrity of the Bitcoin software.

Gitian uses Ubuntu's python-vmbuilder to create a qcow2 base image for an Ubuntu version and architecture combination and a set of git and tarball inputs that you specify in a ' [descriptor](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/descriptors/linux/gitian-firefox.yml)', and then proceeds to run a shell script that you provide to build a component inside that controlled environment. This build process produces an output set that includes the compiled result and another "output descriptor" that captures the versions and hashes of all packages present on the machine during compilation.

Gitian requires either Intel VT support (for qemu-kvm), or LXC support, and currently only supports launching Ubuntu build environments from Ubuntu itself.

# Gitian: How Tor Uses It

[Tor's use of Gitian](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/README.build) is slightly more automated and also slightly different than how Bitcoin uses it.

First of all, because Gitian supports only Ubuntu hosts and targets, we must cross compile everything for Windows and MacOS. Luckily, Mozilla [provides support](https://developer.mozilla.org/en-US/docs/Cross_Compile_Mozilla_for_Mingw32) for [MinGW-w64](http://mingw-w64.sourceforge.net/) as a "third tier" compiler, and does endeavor to work with the MinGW team to fix issues as they arise.

To our further good fortune, we were able to use a MacOS cross compiler created by [Ray Donnelly](https://github.com/mingwandroid) based on a [fork of "Toolchain4"](https://github.com/mingwandroid/toolchain4). We owe Ray a great deal for providing his compilers to the public, and he has been most excellent in terms of helping us through any issues we encountered with them. Ray is also working to [merge his patches](https://github.com/diorcety/crosstool-ng.git) into the [crosstools-ng project](http://crosstool-ng.org/), to provide a more seamless build process to create rebuilds of his compilers. As of this writing, we are still using [his binaries](https://mingw-and-ndk.googlecode.com/files/multiarch-darwin11-cctools127.2-gcc42-5666.3-llvmgcc42-2336.1-Linux-120724.tar.xz) in combination with the [flosoft MacOS10.X SDK](https://launchpad.net/~flosoft/+archive/cross-apple/+packages).

For each platform, we build the components of Tor Browser Bundle in 3 stages, with one descriptor per stage. The [first descriptor](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/descriptors/linux/gitian-tor.yml) builds Tor and its core dependency libraries (OpenSSL, libevent, and zlib) and produces one output zip file. The [second descriptor](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/descriptors/linux/gitian-firefox.yml) builds Firefox. The [third descriptor](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/descriptors/linux/gitian-bundle.yml) combines the previous two outputs along with our included Firefox addons and localization files to produce the actual localized bundle files.

We [provide a Makefile and shellscript-based wrapper](https://gitweb.torproject.org/builders/tor-browser-bundle.git/tree/HEAD:/gitian/) around Gitian to automate the download and authentication of our source inputs prior to build, and to perform a final step that creates a sha256sums.txt file that lists all of the bundle hashes, and can be signed by any number of detached signatures, one for each builder.

It is important to distribute multiple cryptographic signatures to prevent targeted attacks against stealing a single build signing key (because the signing key itself is of course another single point of failure). Unfortunately, GPG currently lacks support for verifying multiple signatures of the same document. Users must manually copy each detached signature they wish to verify into its proper .asc filename suffix. Eventually, we hope to create a stub installer or wrapper script of some kind to simplify this step, as well as add multi-signature support to the Firefox update process. We are also investigating adding a URL and a hash of the package list the [Tor Consensus](https://gitweb.torproject.org/torspec.git/blob/master:/dir-spec.txt), so that the Tor Consensus document itself authenticates our binary packages.

We do not use the Gitian output descriptors or the Gitian signing tools, because the tools are used to sign Gitian's output descriptors. We found that Ubuntu's individual packages (which are listed in the output descriptors) varied too frequently to allow this mechanism to be reproducible for very long. However, we do include a [list of input versions and hashes](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/versions) used to produce each bundle in the bundle itself. The format of this versions file is the same that we use as input to download the sources. This means it should remain possible to re-build an arbitrary bundle for verification at a later date, assuming that any later updates to Ubuntu's toolchain packages do not change the output.

# Gitian: Pain Points

Gitian is not perfect. In fact, many who have tried our build system have remarked that it is not even close to deterministic (and that for this and other reasons 'Reproducible Builds' is a better term). In fact, it seems to experience build failures for quite unpredictible reasons related to bugs in one or more of qemu-kvm/LXC, make, qcow copy-on-write image support. These bugs are often intermittent, and simply restarting the build process often causes things to proceed smoothly. This has made the bugs exceedingly tricky to pinpoint and diagnose.

Gitian's use of tags (especially signed tags) has some bugs and flaws. For this reason, we verify signatures ourselves after input fetching, and provide gitian only with explicit commit hashes for the input source repositories.

We maintain a list of the most common issues in the [build instructions](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/README.build).

# Remaining Build Reproducibility Issues

By default, the Gitian VM environment controls the following aspects of the build platform that normally vary and often leak into compiled software: hostname, build path, uname output, toolchain version, and time.

However, Gitian is not enough by itself to magically produce reproducible builds. Beyond what Gitian provides, we had to patch a number of reproducibility issues in Firefox and some of the supporting tools on each platform. These include:

1. **Reordering due to inode ordering differences (exposed via Python's os.walk())**

Several places in the Firefox build process use python scripts to repackage both compiled library archives and zip files. In particular, they tend to obtain directory listings using os.walk(), which is dependent upon the inode ordering of the filesystem. We fix this by sorting those file lists in the applicable places.

2. **LC\_ALL localizations alter sorting order**

Sorting only gets you so far, though, if someone from a different locale is trying to reproduce your build. Differences in your character sets will cause these sort orders to differ. For this reason, we set the LC\_ALL environment variable to 'C' at the top of our Gitian descriptors.

3. **Hostname and other OS info leaks in LXC mode**

For these cases, we simply patch the pieces of Firefox that include the hostname (primarily for [about:buildconfig](about:buildconfig)).

4. **Millisecond and below timestamps are not fixed by libfaketime**

Gitian relies on [libfaketime](http://www.code-wizards.com/projects/libfaketime/) to set the clock to a fixed value to deal with embedded timestamps in archives and in the build process. However, in some places, Firefox inserts millisecond timestamps into its supporting libraries as part of an informational structure. We simply zero these fields.

5. **FIPS-140 mode generates throwaway signing keys**

A rather insane subsection of the [FIPS-140](https://en.wikipedia.org/wiki/FIPS_140) certification standard requires that you distribute signatures for all of your cryptographic libraries. The Firefox build process meets this requirement by generating a temporary key, using it to sign the libraries, and discarding the private portion of that key. Because there are many other ways to intercept the crypto outside of modifying the actual DLL images, we opted to simply remove these signature files from distribution. There simply is no way to verify code integrity on a running system without both OS and coprocessor assistance. Download package signatures make sense of course, but we handle those another way (as mentioned above).

6. **On Windows builds, something mysterious causes 3 bytes to randomly vary  
in the binary.**

Unable to determine the source of this, we just bitstomp the binary and regenerate the PE header checksums using strip... Seems fine so far! ;)

7. **umask leaks into LXC mode in some cases**

We fix this by manually setting umask at the top of our Gitian descriptors. Additionally, we found that we had to reset the permissions inside of tar and zip files, as the umask didn't affect them on some builds (but not others...)

8. **Zip and Tar reordering and attribute issues**

To aid with this and other issues with reproducibility, we created simple shell wrappers for [zip](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/build-helpers/dzip.sh) and [tar](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/build-helpers/dtar.sh) to eliminate the sources of non-determinism.

9. **Timezone leaks**

To deal with these, we set TZ=UTC at the top of our descriptors.

# Future Work

The most common question we've been asked about this build process is: What can be done to prevent the adversary from compromising the (substantially weaker) Ubuntu build and packaging processes, and further, what about the [Trusting Trust attack](http://cm.bell-labs.com/who/ken/trust.html)?

In terms of eliminating the remaining single points of compromise, the first order of business is to build all of our compilers and toolchain directly from sources via their own Gitian descriptors.

Once this is accomplished, we can begin the process of building identical binaries from multiple different Linux distributions. This would require the adversary to compromise multiple Linux distributions in order to compromise the Tor software distribution.

If we can support reproducible builds through cross compiling from multiple architectures (Intel, ARM, MIPS, PowerPC, etc), this also reduces the likelihood of a Trusting Trust attack surviving unnoticed in the toolchain (because the machine code that injects the payload would have to be pre-compiled and present for all copies of the cross-compiled executable code in a way that is still not visible in the sources).

If those Linux distributions also support reproducible builds of the full build and toolchain environment (both [Debian](https://wiki.debian.org/ReproducibleBuilds) and [Fedora](http://securityblog.redhat.com/2013/09/18/reproducible-builds-for-fedora/) have started this), we can eliminate Trusting Trust attacks entirely by using [Diverse Double Compilation](http://www.schneier.com/blog/archives/2006/01/countering_trus.html) between multiple independent distribution toolchains, and/or assembly audited compilers. In other words, we could use the distributions' deterministic build processes to [verify](https://lwn.net/Articles/555902/) that identical build environments are produced through Diverse Double Compilation.

As can be seen, much work remains before the system is fully resistant against all forms of malware injection, but even in their current state, reproducible builds are a huge step forward in software build security. We hope this information helps other software distributors to follow the example set by Bitcoin and Tor.

