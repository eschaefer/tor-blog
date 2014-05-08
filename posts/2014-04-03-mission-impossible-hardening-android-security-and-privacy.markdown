---
layout: post
title: "Mission Impossible: Hardening Android for Security and Privacy"
permalink: mission-impossible-hardening-android-security-and-privacy
date: 04/03/2014
author: mikeperry
category: blog
tags: ["android", "orbot", "security", "tor"]
---

 **Updates:** See the Changes section for a list of changes since initial posting.

# Executive Summary

The future is here, and ahead of schedule. Come join us, the weather's nice.

This blog post describes the installation and configuration of a prototype of a secure, full-featured, Android telecommunications device with full Tor support, individual application firewalling, true cell network baseband isolation, and optional [ZRTP](https://en.wikipedia.org/wiki/ZRTP) encrypted voice and video support. ZRTP does run over UDP which is not yet possible to send over Tor, but we are able to send SIP account login and call setup over Tor independently.

The SIP client we recommend also supports dialing normal telephone numbers, but that is also UDP+ZRTP, and the normal telephone network side of the connection is obviously not encrypted.

Aside from a handful of binary blobs to manage the device firmware and graphics acceleration, the entire system can be assembled (and recompiled) using only FOSS components. However, as an added bonus, we will describe how to handle the Google Play store as well, to mitigate [the](http://nakedsecurity.sophos.com/2011/02/04/android-market-web-store-backdoor-phone-hackers/) [two](http://www.forbes.com/sites/andygreenberg/2014/03/19/android-upgrades-open-a-backdoor-to-malware-researchers-show/) infamous Google Play Backdoors.

# Introduction

Android is the most popular mobile platform in the world, with a wide variety of applications, including many applications that aid in communications security, censorship circumvention, and activist organization. Moreover, the core of the Android platform is Open Source, auditable, and modifiable by anyone.

Unfortunately though, mobile devices in general and Android devices in particular have not been designed with privacy in mind. In fact, they've seemingly been designed with nearly the opposite goal: to make it easy for third parties, telecommunications companies, sophisticated state-sized adversaries, and even random hackers to extract all manner of personal information from the user. This includes the full content of personal communications with business partners and loved ones. Worse still, by default, the user is given very little in the way of control or even informed consent about what information is being collected and how.

This post aims to address this, but we must first admit we stand on the shoulders of giants. Organizations like [Cyanogen](http://www.cyanogenmod.org/), [F-Droid](https://f-droid.org/), the [Guardian Project](https://guardianproject.info/), and many others have done a great deal of work to try to improve this situation by restoring control of Android devices to the user, and to ensure the integrity of our personal communications. However, all of these projects have shortcomings and often leave gaps in what they provide and protect. Even in cases where proper security and privacy features exist, they typically require extensive configuration to use safely, securely, and correctly.

This blog post enumerates and documents these gaps, describes workarounds for serious shortcomings, and provides suggestions for future work.

It is also meant to serve as a HOWTO to walk interested, technically capable people through the end-to-end installation and configuration of a prototype of a secure and private Android device, where access to the network is restricted to an approved list of applications, and all traffic is routed through the Tor network.

It is our hope that this work can be replicated and eventually fully automated, given a good UI, and rolled into a single ROM or ROM addon package for ease of use. Ultimately, there is no reason why this system could not become a full fledged off the shelf product, given proper hardware support and good UI for the more technical bits.

The remainder of this document is divided into the following sections:

1. Hardware Selection
2. Installation and Setup
3. Google Apps Setup
4. Recommended Software
5. Device Backup Procedure
6. Removing the Built-in Microphone
7. Removing Baseband Remnants
8. Future Work
9. Changes Since Initial Posting

# Hardware Selection

If you truly wish to secure your mobile device from remote compromise, it is necessary to carefully select your hardware. First and foremost, it is [absolutely essential](http://www.osnews.com/story/27416/The_second_operating_system_hiding_in_every_mobile_phone) that the carrier's baseband firmware is completely isolated from the rest of the platform. Because your cell phone baseband does not authenticate the network (in part to allow roaming), any random hacker with [their own cell network](http://www.openbts.org/) can exploit these backdoors and use them to install malware on your device.

While there are projects underway to determine which handsets actually provide true hardware baseband isolation, at the time of this writing there is very little public information available on this topic. Hence, the only safe option remains a device with no cell network support at all (though cell network connectivity can still be provided by a separate device). For the purposes of this post, the reference device is the WiFi-only version of the [2013 Google Nexus 7 tablet](https://en.wikipedia.org/wiki/Nexus_7_%282013_version%29).

For users who wish to retain full mobile access, we recommend obtaining a cell modem device that provides a WiFi access point for data services only. These devices do not have microphones and in some cases do not even have fine-grained GPS units (because they are not able to make emergency calls). They are also available with prepaid plans, for rates around $20-30 USD per month, for about 2GB/month of 4G data. If coverage and reliability is important to you though, you may want to go with a slightly more expensive carrier. In the US, T-Mobile isn't bad, but Verizon is superb.

To increase battery life of your cell connection, you can connect this access point to an external mobile USB battery pack, which typically will provide 36-48 hours of continuous use with a 6000mAh battery.

The total cost of a Wifi-only tablet with cell modem and battery pack is only roughly USD $50 more than the 4G LTE version of the same device.

In this way, you achieve true baseband isolation, with no risk of [audio](http://news.cnet.com/2100-1029-6140191.html) or [network](http://www.globalresearch.ca/new-hi-tech-police-surveillance-the-stingray-cell-phone-spying-device/5331165) surveillance, [baseband exploits](https://www.usenix.org/system/files/conference/woot12/woot12-final24.pdf), or [provider backdoors](https://www.fsf.org/blogs/community/replicant-developers-find-and-close-samsung-galaxy-backdoor). Effectively, this cell modem is just another untrusted router in a long, long chain of untrustworthy Internet infrastructure.

However, do note though that even if the cell unit does not contain a fine-grained GPS, you still sacrifice location privacy while using it. Over an extended period of time, it will be possible to make inferences about your physical activity, behavior and personal preferences, and your identity, based on cell tower use alone.

# Installation and Setup

We will focus on the installation of Cyanogenmod 11 using Team Win Recovery Project, both to give this HOWTO some shelf life, and because Cyanogenmod 11 features full SELinux support (Dear NSA: What happened to you guys? You used to be cool. Well, some of you. Some of the time. Maybe. [Or maybe not](http://www.reuters.com/article/2014/03/31/us-usa-security-nsa-rsa-idUSBREA2U0TY20140331)).

The use of Google Apps and Google Play services is not recommended due to security issues with Google Play. However, we do provide workarounds for mitigating those issues, if Google Play is required for your use case.

## Installation and Setup: ROM and Core App Installation

With the 2013 Google Nexus 7 tablet, installation is fairly straight-forward. In fact, it is actually possible to install and use the device before associating it with a Google Account in any way. This is a desirable property, because by default, the otherwise mandatory initial setup process of the stock Google ROM sends your device MAC address directly to Google and links it to your Google account (all without using Tor, of course).

The [official Cyanogenmod installation instructions](http://wiki.cyanogenmod.org/w/Install_CM_for_flo) are available online, but with a fresh out of the box device, here are the key steps for installation without activating the default ROM code at all (using Team Win Recovery Project instead of ClockWorkMod).

First, on your desktop/laptop computer (preferably Linux), perform the following:

1. [Download](http://download.cyanogenmod.org/?device=flo) the latest CyanogenMod 11 release (we used cm-11-20140308-SNAPSHOT-M4)
2. [Download](http://teamw.in/project/twrp2/193) the latest Team Win Recovery Project image (we used 2.7.0.0)
3. [Download](https://f-droid.org/FDroid.apk) the F-Droid package (we used 0.63)
4. [Download](https://f-droid.org/repository/browse/?fdfilter=orbot&fdid=org.torproject.android) the Orbot package from F-Droid (we used 13.0.5)
5. [Download](https://f-droid.org/repository/browse/?fdfilter=droidwall&fdid=com.googlecode.droidwall) the Droidwall package from F-Droid (we used 1.5.7)
6. [Download](https://people.torproject.org/~mikeperry/android-hardening/android-firewall.zip) the Droidwall Firewall Scripts attached to this blogpost
7. [Download](http://wiki.cyanogenmod.org/w/Google_Apps) the Google Apps for Cyanogenmod 11 (optional)

Because the download integrity for all of these packages is abysmal, here is a [signed set of SHA256 hashes](https://people.torproject.org/~mikeperry/android-hardening/sha256sums-cm11.txt.asc) I've observed for those packages.

Once you have all of those packages, boot your tablet into fastboot mode by holding the Power button and the Volume Down button during a cold boot. Then, attach it to your desktop/laptop machine with a USB cable and run the following commands, as root:

    apt-get install android-tools-adb android-tools-fastboot
     fastboot devices
     fastboot oem unlock
     fastboot flash recovery openrecovery-twrp-2.7.0.0-flo.img

After the recovery firmware is flashed successfully, use the volume keys to select _Recovery_ and hit the power button to reboot the device (or power it off, and then boot holding Power and Volume Up).

Once Team Win boots, go into _Wipe_ and select _Advanced Wipe_. Select all checkboxes except for USB-OTG, and slide to wipe. Once the wipe is done, click _Format Data_. After the format completes, issue these commands from your Linux root shell:

    adb server start
     adb push cm-11-20140308-SNAPSHOT-M4-flo.zip /sdcard/
     adb push gapps-kk-20140105-signed.zip /sdcard/ # Optional

After this push process completes, go to the _Install_ menu, and select the Cyanogen zip, and optionally the gapps zip for installation. Then click Reboot, and select System.

After rebooting into your new installation, skip all CyanogenMod and Google setup, disable location reporting, and immediately disable WiFi and turn on Airplane mode.

Then, go into _Settings -> About Tablet_ and scroll to the bottom and click the greyed out Build number 5 times until developer mode is enabled. Then go into _Settings -> Developer Options_ and turn on _USB Debugging_.

After that, run the following commands from your Linux root shell:

    adb install FDroid.apk
     adb install org.torproject.android_70.apk
     adb install com.googlecode.droidwall_157.apk

You will need to approve the ADB connection for the first package, and then they should install normally.

**VERY IMPORTANT:** Whenever you finish using adb, **always remember** to disable _USB Debugging_ and restore _Root Access_ to _Apps only_. While Android 4.2+ ROMs now prompt you to authorize an RSA key fingerprint before allowing a debugging connection (thus mitigating adb exploit tools that bypass screen lock and can install root apps), you still risk additional vulnerability surface by leaving debugging enabled.

## Installation and Setup: Initial Configuration

After the base packages are installed, go into the Settings app, and make the following changes:

1. Location Access -> Off
2. Language & Input =>

- Spell Checker -> Android Spell Checker -> Disable Contact Names
- Disable Google Voice Typing
- Android Keyboard (AOSP) =>
  - Disable AOSP next-word suggestion (do this first!)
  - Auto-correction -> Off

- Backup & reset =>

- Enable _Back up my data_ (just temporarily, for the next step)
- Uncheck _Automatic restore_
- Disable _Backup my data_
- About Tablet -> Cyanogenmod Statistics -> Disable reporting
- Developer Options -> Device Hostname -> localhost
- SuperUser -> Settings (three dots) -> Notifications -> Notification (not toast)
- Privacy -> Privacy Guard =>
- Enabled by default
- Settings (three dots) -> Show Built In Apps
- Enable Privacy Guard for every app with the following exceptions:
  - Calendar
  - Config Updater
  - Google Account Manager (long press)

    - Modify Settings -> Off
    - Wifi Change -> Off
    - Data Change -> Off
  - Google Play Services (long press)

    - Location -> Off
    - Modify Settings -> Off
    - Draw on top -> Off
    - Record Audio -> Off
    - Wifi Change -> Off
  - Google Play Store (long press)

    - Location -> Off
    - Send SMS -> Off
    - Modify Settings -> Off
    - Data change -> Off
  - Google Services Framework (long press)

    - Modify Settings -> Off
    - Wifi Change -> Off
    - Data Change -> Off
  - Trebuchet

- Security =>
- PIN screen Lock
- Allow Unknown Sources (For F-Droid)
- Encrypt Tablet 

After that last step, your tablet will reboot and encrypt itself. It is important to do this step early, as I have noticed additional apps and configuration tweaks can make this process fail later on. You can and should also change the boot password to be different from the screen unlock PIN later on, to mitigate compromise of this password from shoulder surfers, and to allow the use of a much longer (and non-numeric) password that you would prefer not to type every time you unlock the screen.

To do this, open the Terminal app, and type the following commands:

    su
    vdc cryptfs changepw NewMoreSecurePassword

Watch for typos! That command does not ask you to re-type that password for confirmation.

## Installation and Setup: Disabling Invasive Apps and Services

Before you configure the Firewall or enable the network, you likely want to disable at least a subset of the following built-in apps and services, by using _Settings -> Apps -> All_, and then clicking on each app and hitting the _Disable_ button:

- com.android.smspush
- com.google.android.voicesearch
- Face Unlock
- Google Backup Transport
- Google Calendar Sync
- Google One Time Init
- Google Partner Setup
- Google Contacts Sync
- Google Search
- Hangouts
- Market Feedback Agent
- News & Weather
- One Time Init
- Picasa Updater
- Sound Search for Google Play
- TalkBack

## Installation and Setup: Tor and Firewall configuration

Ok, now let's install the firewall and tor support scripts. Go back into _Settings -> Developer Options_ and enable _USB Debugging_ and change _Root Access_ to _Apps and ADB_. Then, unzip the [android-firewall.zip](https://people.torproject.org/~mikeperry/android-hardening/android-firewall.zip) on your laptop, and run the [installation script](https://people.torproject.org/~mikeperry/android-hardening/android-firewall/install-firewall.sh):

    ./install-firewall.sh

That firewall installation provides several key scripts that provide functionality that is currently impossible to achieve with any app (including Orbot):

1. It installs a [userinit script](https://people.torproject.org/~mikeperry/android-hardening/android-firewall/userinit.sh) to block all network access during boot.
2. It disables "Google Captive Portal Detection", which involves connection attempts to Google servers upon Wifi assocation (these requests are made by the Android _Settings_ UID, which should normally be blocked from the network, unless you are first registering for Google Play).
3. It contains a [Droidwall script](https://people.torproject.org/~mikeperry/android-hardening/android-firewall/firewall-tor.sh) that configures Tor transproxy rules to send all of your traffic through Tor. These rules include a fix for a Linux kernel [Tor transproxy packet leak issue](https://lists.torproject.org/pipermail/tor-talk/2014-March/032503.html).
4. The main firewall-tor.sh Droidwall script also includes an input firewall, to block all inbound connections to the device. It also fixes a Droidwall [permissions vulnerability](https://code.google.com/p/droidwall/issues/detail?id=260)
5. It installs an [optional script](https://people.torproject.org/~mikeperry/android-hardening/android-firewall/firewall-capportal.sh) to allow the Browser app to bypass Tor for logging into WiFi captive portals.
6. It installs an [optional script](https://people.torproject.org/~mikeperry/android-hardening/android-firewall/firewall-adb.sh) to temporarily allow network adb access when you need it (if you are paranoid about USB exploits, which you should be).
7. It provides an [optional script](https://people.torproject.org/~mikeperry/android-hardening/android-firewall/firewall-linphone.sh) to allow the UDP activity of LinPhone to bypass Tor, to allow ZRTP-encrypted Voice and Video SIP/VoIP calls. SIP account login/registration and call setup/signaling can be done over TCP, and Linphone's TCP activity is still sent through Tor with this script. 

Note that with the exception of the userinit network blocking script, installing these scripts does not activate them. You still need to configure Droidwall to use them.

We use Droidwall instead of Orbot or AFPWall+ for five reasons:

1. Droidwall's app-based firewall and Orbot's transproxy are known to conflict and reset one another.
2. Droidwall does not randomly drop transproxy rules when switching networks (Orbot has had several of these types of bugs).
3. Unlike AFWall+, Droidwall is able to auto-launch at "boot" (though still not before the network and Android Services come online and make connections).
4. AFWall+'s "fix" for this startup data leak problem does not work on Cyanogenmod (hence our userinit script instead).
5. Aside from the permissions issue fixed by our firewall-tor.sh script, AFWall+ provides no additional security fixes over the stock Droidwall.

To make use of the firewall scripts, open up Droidwall and hit the config button (the vertical three dots), go to _More -> Set Custom Script_. Enter the following:

    . /data/local/firewall-tor.sh
    #. /data/local/firewall-adb.sh
    #. /data/local/firewall-linphone.sh
    #. /data/local/firewall-capportal.sh

Note that these scripts have been installed into a readonly root directory. Because they are run as root, installing them to a world-writable location like /sdcard/ is extremely unwise.

Later, if you want to enable one of network adb, LinPhone UDP, or captive portal login, go back into this window and remove the leading comment ('#') from the appropriate lines (this is obviously one of the many aspects of this prototype that could benefit from real UI).

Then, configure the apps you want to allow to access the network. Note that the only Android system apps that must access the network are:

- CM Updater
- Downloads, Media Storage, Download Manager
- F-Droid

Orbot's network access is handled via the main firewall-tor.sh script. You do not need to enable full network access to Orbot in Droidwall.

The rest of the apps you can enable at your discretion. They will all be routed through Tor automatically.

Once the Droidwall is configured, you can enable Orbot. **Do not** grant Orbot superuser access. It still opens the transproxy ports you need without root, and Droidwall is managing installation of the transproxy rules, not Orbot.

You are now ready to enable Wifi and network access on your device. For vulnerability surface reduction, you may want to use the _Advanced Options -> Static IP_ to manually enter an IP address for your device to avoid using dhclient. You do not need a DNS server, and can safely set it to 127.0.0.1.

# Google Apps Setup

If you installed the Google Apps zip, you need to do a few things now to set it up, and to further harden your device. If you opted out of Google Apps, you can skip to the next section.

## Google Apps Setup: Initializing Google Play

The first time you use Google Play, you will need to enable three apps in Droidwall: "_Google Account Manager, Google Play Services..._", "_Settings, Dev Tools, Fused Location..._", and "_Google Play_" itself.

If you do not have a Google account, your best bet is to find open wifi to create one, as Google will often block accounts created through Tor, even if you use an Android device.

After you log in for the first time, you should be able to disable the "_Google Account Manager, Google Play Services..._" and the "_Settings..._" apps in Droidwall, but your authentication tokens in Google Play may expire periodically. If this happens, you should only need to temporarily enable the "_Google Account Manager, Google Play Services..._" app in Droidwall to obtain new ones.

## Google Apps Setup: Mitigating the Google Play Backdoors

If you do choose to use Google Play, you need to be very careful about how you allow it to access the network. In addition to the risks associated with using a proprietary App Store that can send you targeted malware-infected packages based on your Google Account, it has at least two major user experience flaws:

1. Anyone who is able to gain access to your Google account can [silently install](http://nakedsecurity.sophos.com/2011/02/04/android-market-web-store-backdoor-phone-hackers/) root or full permission apps without any user interaction what-so-ever. Once installed, these apps can retroactively clear what little installation notification and UI-based evidence of their existence there was in the first place.
2. The Android Update Process does not inform the user of [changes in permissions](http://www.forbes.com/sites/andygreenberg/2014/03/19/android-upgrades-open-a-backdoor-to-malware-researchers-show/) of pending update apps that happen to get installed after an Android upgrade.

The first issue can be mitigated by ensuring that Google Play does not have access to the network when not in use, by disabling it in Droidwall. If you do not do this, apps can be installed silently behind your back. Welcome to the Google Experience.

For the second issue, you can install the [SecCheck](https://play.google.com/store/apps/details?id=com.iu.seccheck) utility, to monitor your apps for changes in permissions during a device upgrade.

## Google Apps Setup: Disabling Google Cloud Messaging

If you have installed the Google Apps zip, you have also enabled a feature called [Google Cloud Messaging>.](https://en.wikipedia.org/wiki/Google_Cloud_Messaging)

The [Google Cloud Messaging Service](https://developer.android.com/google/gcm/index.html) allows apps to register for asynchronous remote push notifications from Google, as well as send outbound messages through Google.

Notification registration and outbound messages are sent via the app's own UID, so using Droidwall to disable network access by an app is enough to prevent outbound data, and notification registration. However, if you ever allow network access to an app, and it does successfully register for notifications, these notifications can be delivered even when the app is once again blocked from accessing the network by Droidwall.

These inbound notifications can be blocked by disabling network access to the "_Google Account Manager, Google Play Services, Google Services Framework, Google Contacts Sync_" in Droidwall. In fact, the only reason you should ever need to enable network access by this service is if you need to log in to Google Play again if your authentication tokens ever expire.

If you would like to test your ability to control Google Cloud Messaging, there are two apps in the Google Play store than can help with this. [GCM Test](https://play.google.com/store/apps/details?id=com.iapplize.gcm.test) allows for simple send and receive pings through GCM. [Push Notification Tester](https://play.google.com/store/apps/details?id=com.firstrowria.pushnotificationtester) will allow you to test registration and asynchronous GCM notification.

## Recommended Privacy and Auditing Software

Ok, so now that we have locked down our Android device, now for the fun bit: secure communications!

We recommend the following apps from [F-Droid](https://f-droid.org):

1. [Xabber](https://f-droid.org/repository/browse/?fdfilter=xabber&fdid=com.xabber.androiddev)

Xabber is a full Java implementation of XMPP, and supports both OTR and Tor. Its UI is a bit more streamlined than Guardian Project's [ChatSecure](https://f-droid.org/repository/browse/?fdid=info.guardianproject.otr.app.im), and it does not make use of any native code components (which are more vulnerable to code execution exploits than pure Java code). Unfortunately, this means it lacks some of ChatSecure's nicer features, such as push-to-talk voice and file transfer.

Despite better protection against code execution, it does have several insecure default settings. In particular, you want to make the following changes:

- Notifications -> Message text in Notifications -> Off (notifications can be read by other apps!)
- Accounts -> Integration into system accounts -> Off
- Accounts -> Store message history -> Don't Store
- Security -> Store History -> Off
- Security -> Check Server Certificate
- Chat -> Show Typing Notifications -> Off
- Connection Settings -> Auto-away -> disabled
- Connection Settings -> Extended away when idle -> Disabled
- Keep Wifi Awake -> On
- Prevent sleep Mode -> On

- [Offline Calendar](https://f-droid.org/repository/browse/?fdfilter=offline%20calendar&fdid=org.sufficientlysecure.localcalendar)

Offline Calendar is a hack to allow you to create a fake local Google account that does not sync to Google. This allows you to use the Calendar App without risk of leaking your activities to Google. Note that you must exempt both this app and Calendar from Privacy Guard for it to function properly.

- [LinPhone](https://f-droid.org/repository/browse/?fdfilter=Linphone&fdid=org.linphone)

LinPhone is a FOSS SIP client that supports TCP TLS signaling and ZRTP. **Note that neither TLS nor ZRTP are enabled by default.** You must manually enable them in _Settings -> Network -> Transport and Settings -> Network -> Media Encryption_.

[ostel.co](https://ostel.co/) is a free SIP service run by the Guardian Project that supports only TLS and ZRTP, but does not allow outdialing to normal PSTN telephone numbers. While Bitcoin has many privacy issues of its own, the Bitcoin community maintains a [couple](http://www.thebitcoinreview.com/sites.php?catid=2&subcatid=12) [lists](http://www.bitcoiney.com/listings/category/voip-sms) of "trunking" providers that allow you to obtain a PSTN phone number in exchange for Bitcoin payment.  
<!---</p>
<li><a href="https://f-droid.org/repository/browse/?fdfilter=mumble&amp;fdid=com.morlunk.mumbleclient">Plumble</a>
<p>
Plumble is a Mumble client that will route voice traffic over Tor. However, unlike Linphone, voice traffic is not end-to-end encrypted, so the Mumble server can listen to your conversations. Moreover, Plumble does depend on several native code components, including the Opus audio codec, which has had multiple code execution and memory safety hazard vulnerabilities this year. Proceed with caution, or just use Linphone.
 </p>
<p>-->

- [OSMAnd~](https://f-droid.org/repository/browse/?fdfilter=osmand&fdid=net.osmand.plus)

A free offline mapping tool. While the UI is a little clunky, it does support voice navigation and driving directions, and is a handy, private alternative to Google Maps.

- [VLC](https://f-droid.org/repository/browse/?fdfilter=vlc&fdid=org.videolan.vlc)

The VLC port in F-Droid is a fully capable media player. It can play mp3s and most video formats in use today. It is a handy, private alternative to Google Music and other closed-source players that often report your activity to third party advertisers. VLC does not need network access to function.

- [Firefox](https://f-droid.org/repository/browse/?fdfilter=firefox&fdid=org.mozilla.firefox)

We do not yet have a port of Tor Browser for Android (though one is underway -- see the Future Work section). Unless you want to use Google Play to get Chrome, Firefox is your best bet for a web browser that receives regular updates (the built in Browser app does not). [HTTPS-Everywhere](https://www.eff.org/https-everywhere) and [NoScript](http://noscript.net/nsa/) are available, at least.

- [Bitcoin](https://f-droid.org/repository/browse/?fdfilter=bitcoin&fdid=de.schildbach.wallet)

Bitcoin might not be the most private currency in the world. In fact, you might even say it's the least private currency in the world. But, it is a neat toy.

- [Launch App Ops](https://f-droid.org/repository/browse/?fdfilter=permissions&fdid=com.adstrosoftware.launchappops)

The Launch App Ops app is a simple shortcut into the hidden application permissions editor in Android. A similar interface is available through _Settings -> Privacy -> Privacy Guard_, but a direct shortcut to edit permissions is handy. It also displays some additional system apps that Privacy Guard omits.

- [Permissions](https://f-droid.org/repository/browse/?fdfilter=permissions&fdid=com.FireFart.Permissions2)

The Permissions app gives you a view of all Android permissions, and shows you which apps have requested a given permission. This is particularly useful to disable the _record audio_ permission for apps that you don't want to suddenly decide to listen to you. (Interestingly, the Record Audio permission disable feature was broken in all Android ROMs I tested, aside from Cyanogenmod 11. You can test this yourself by revoking the permission from the Sound Recorder app, and verifying that it cannot record.)

- [CatLog](https://f-droid.org/repository/browse/?fdfilter=catlog&fdid=com.nolanlawson.logcat)

In addition to being supercute, CatLog is an excellent Android monitoring and debugging tool. It allows you to monitor and record the full set of Android log events, which can be helpful in diagnosing issues with apps.

- [OS Monitor](https://f-droid.org/repository/browse/?fdfilter=os%20monitor&fdid=com.eolwral.osmonitor)

OS Monitor is an excellent Android process and connection monitoring app, that can help you watch for CPU usage and connection attempts by your apps.

- [Intent Intercept](https://f-droid.org/repository/browse/?fdfilter=intent%20intercept&fdid=uk.co.ashtonbrsc.android.intentintercept)

Intent Intercept allows you to inspect and extract [Android Intent](https://stackoverflow.com/questions/6578051/what-is-intent-in-android) content without allowing it to get forwarded to an actual app. This is useful for monitoring how apps attempt to communicate with eachother, though be aware it only covers one of the [mechanisms of inter-app communication](https://developer.android.com/training/articles/security-tips.html#IPC) in Android.

# Backing up Your Device Without Google

Now that your device is fully configured and installed, you probably want to know how to back it up without sending all of your private information directly to Google. While the Team Win Recovery Project will back up all of your system settings and apps (even if your device is encrypted), it currently does not back up the contents of your virtualized /sdcard. Remembering to do a couple adb pulls of key directories can save you a lot of heartache should you suffer some kind of data loss or hardware failure (or simply drop your tablet on a bridge while in a rush to catch a train).

The [backup.sh script](https://people.torproject.org/~mikeperry/android-hardening/backup.sh) uses adb to pull your Download and Pictures directories from the /sdcard, as well as pulls the entire TWRP backup directory.

Before you use that script, you probably want to delete old TWRP backup folders so as to only pull one backup, to reduce pull time. These live in **/sdcard/TWRP/BACKUPS/** , which is also known as **/storage/emulated/0/TWRP/BACKUPS** in the File Manager app.

To use this script over the network without a usb cable, enable both USB Debugging and ADB Over Network in your developer settings. The script does not require you to enable root access from adb, and you should not enable root because it takes quite a while to run a backup, especially if you are using network adb.

Prior to using network adb, you must edit your Droidwall custom scripts to allow it (by removing the '#' in the **#. /data/local/firewall-adb.sh** line you entered earlier), and then run the following commands from a non-root Linux shell on your desktop/laptop (the _ADB Over Network_ setting will tell you the IP and port):

    killall adb
    adb connect ip:5555

Network adb also has the advantage of not requiring root on your desktop/Laptop.

**VERY IMPORTANT** : Don't forget to disable _USB Debugging_, as well as the Droidwall adb exemption when you are done with the backup!

# Removing the Built-in Microphone

If you would really like to ensure that your device cannot listen to you even if it is exploited, it turns out it is very straight-forward to remove the built-in microphone in the Nexus 7. There is only one mic on the 2013 model, and it is located just below the volume buttons (the tiny hole).

To remove it, all you need to do is pop off the the back panel (this can be done with your fingernails, or a tiny screwdriver), and then you can shave the microphone right off that circuit board, and reattach the panel. I have done this to one of my devices, and it was subsequently unable to record audio at all, without otherwise affecting functionality.

You can still use apps that require a microphone by plugging in headphone headset that contains a mic built in (these cost around $20 and you can get them from nearly any consumer electronics store). I have also tested this, and was still able to make a Linphone call from a device with the built in microphone removed, but with an external headset. Note that the 2012 Nexus 7 does **not** support these combination microphone+headphone jacks (and it has a secondary microphone as well). You must have the 2013 model.

The [2013 Nexus 7 Teardown video](https://www.youtube.com/watch?v=IG6A_RBX-v0&html5=1) can give you an idea of what this looks like before you try it. Again you do not need to fully disassemble the device - you only need to remove the back cover.

**Pro-Tip:** Before you go too crazy and start ripping out the cameras too, remember that you can cover the cameras with a sticker or tape when not in use. I have found that regular old black electrical tape applies seamlessly, is non-obvious to casual onlookers, and is easy to remove without smudging or gunking up the lenses. Better still, it can be removed and reapplied many times without losing its adhesive.

# Removing the Remnants of the Baseband

There is one more semi-hardware mod you may want to make, though.

It turns out that the 2013 Wifi Nexus 7 does actually have a partition that contains a cell network baseband firmware on it, located on the filesystem as the block device **/dev/block/platform/msm\_sdcc.1/by-name/radio** . If you run **strings** on that block device from the shell, you can see all manner of CDMA and GSM log messages, comments, and symbols are present in that partition.

According to ADB logs, Cyanogenmod 11 actually does try to bring up a cell network radio at boot on my Wifi-only Nexus 7, but fails due to it being disabled. There is also a strong economic incentive for Asus and Google to make it extremely difficult to activate the baseband even if the hardware is otherwise identical for manufacturing reasons, since they sell the WiFi-only version for $100 less. If it were easy to re-enable the baseband, HOWTOs would exist (which they do not seem to, at least not yet), and they would cut into their LTE device sales.

Even so, since we lack public schematics for the Nexus 7 to verify that cell components are actually missing or hardware-disabled, it may be wise to wipe this radio firmware as well, as defense in depth.

To do this, open the Terminal app, and run:

    su
    cd /dev/block/platform/msm_sdcc.1/by-name
    dd if=/dev/zero of=./radio

I have wiped that partition while the device was running without any issue, or any additional errors from ADB logs.

Note that an anonymous commenter also suggested it is [possible to disable the baseband](https://blog.torproject.org/blog/mission-impossible-hardening-android-security-and-privacy#comment-55280) of a cell-enabled device using a series of Android service disable commands, and by wiping that radio block device. I have not tested this on a device other than the WiFI-only Nexus 7, though, so proceed with caution. If you try those steps on a cell-enabled device, you should archive a copy of your radio firmware first by doing something like the following from that dev directory that contains the radio firmware block device.

    dd if=./radio of=/sdcard/radio.img

If anything goes wrong, you can restore that image with:

    dd if=/sdcard/radio.img of=./radio

# Future Work

In addition to streamlining the contents of this post into a single additional Cyanogenmod installation zip or alternative ROM, the following problems remain unsolved.

## Future Work: Better Usability

While arguably very secure, this system is obviously nowhere near usable. Here are some potential improvements to the user interface, based on a brainstorming session I had with another interested developer.

First of all, the AFWall+/Droidwall UI should be changed to be a tri-state: It should allow you to send app traffic over Tor, over your normal internet connection, or block it entirely.

Next, during app installation from either F-Droid or Google Play (this is an Intent another addon app can actually listen for), the user should be given the chance to decide if they would like that app's traffic to be routed over Tor, use the normal Internet connection, or be blocked entirely from accessing the network. Currently, the Droidwall default for new apps is "no network", which is a great default, but it would be nice to ask users what they would like to do during actual app installation.

Moreover, users should also be given a chance to edit the app's permissions upon installation as well, should they desire to do so.

The Google Play situation could also be vastly improved, should Google itself still prove unwilling to improve the situation. Google Play could be wrapped in a launcher app that automatically grants it network access prior to launch, and then disables it upon leaving the window.

A similar UI could be added to LinPhone. Because the actual voice and video transport for LinPhone does not use Tor, it is possible for an adversary to learn your SIP ID or phone number, and then call you just for the purposes of learning your IP. Because we handle call setup over Tor, we can prevent LinPhone from performing any UDP activity, or divulging your IP to the calling party prior to user approval of the call. Ideally, we would also want to inform the user of the fact that incoming calls can be used to obtain information about them, at least prior to accepting their first call from an unknown party.

## Future Work: Find Hardware with Actual Isolated Basebands

Related to usability, it would be nice if we could have a serious community effort to audit the baseband isolation properties of existing cell phones, so we all don't have to carry around these ridiculous battery packs and sketch-ass wifi bridges. There is no engineering reason why this prototype could not be just as secure if it were a single piece of hardware. We just need to find the right hardware.

A [random commenter claimed that the Galaxy Nexus](https://blog.torproject.org/blog/mission-impossible-hardening-android-security-and-privacy#comment-55372) might actually have exactly the type of baseband isolation we want, but the comment was from memory, and based on software reverse engineering efforts that were not publicly documented. We need to do better than this.

## Future Work: Bug Bounty Program

If there is sufficient interest in this prototype, and/or if it gets transformed into a usable addon package or ROM, we may consider running a bug bounty program where we accept donations to a dedicated Bitcoin address, and award the contents of that wallet to anyone who discovers a Tor proxy bypass issue or remote code execution vulnerability in any of the network-enabled apps mentioned in this post (except for the Browser app, which does not receive security updates).

## Future Work: Port Tor Browser to Android

The Guardian Project is undertaking [a port of Tor Browser to Android](https://github.com/guardianproject/orfox) as part of their [OrFox project](https://dev.guardianproject.info/projects/google-summer-of-code/wiki/Orfox_-_Firefox-based_Privacy_Enhanced_Browser/1). This will greatly improve the privacy of your web browsing experience on the Android device over both Firefox and Chrome. We look forward to helping them in any way we can with this effort.

## Future Work: WiFi MAC Address Randomization

It is actually possible to randomize the WiFi MAC address on the Google Nexus 7. The closed-source root app [Mac Spoofer](https://play.google.com/store/apps/details?id=com.jworksbr.macspoofer) is able to modify the device MAC address using Qualcomm-specific methods in such a way that the entire Android OS becomes convinced that this is your actual MAC.

However, doing this requires installation of a root-enabled, closed-source application from the Google Play Store, which we believe is extremely unwise on a device you need to be able to trust. Moreover, this app cannot be autorun on boot, and your MAC address will also reset every time you disable the WiFi interface (which is easy to do accidentally). It also supports using only a single, manually entered MAC address.

Hardware-independent techniques (such as a the Terminal command **busybox ifconfig wlan0 hw ether <mac>** ) appear to interfere with the WiFi management system and prevent it from associating. Moreover, they do not cause the Android system to report the new MAC address, either (visible under _Settings -> About Tablet -> Status_).

Obviously, an Open Source F-Droid app that properly resets (and automatically randomizes) the MAC every time the WiFi interface is brought up is badly needed.

## Future Work: Disable Probes for Configured Wifi Networks

The Android OS currently probes for all of your configured WiFi networks while looking for open wifi to connect to. Configured networks should not be probed for explictly unless activity for their BSSID is seen. The xda-developers forum has a [limited fix to change scanning behavior](http://forum.xda-developers.com/showthread.php?t=2683858), but [users report](http://forum.xda-developers.com/showpost.php?s=5172139ce1f8c5a99e3ef4bfa471042a&p=51268001&postcount=4) that it does not disable the active probing behavior for any "hidden" networks that you have configured.

## Future Work: Recovery ROM Password Protection

An unlocked recovery ROM is a huge vulnerability surface for Android. While disk encryption protects your applications and data, it does not protect many key system binaries and boot programs. With physical access, it is possible to modify these binaries through your recovery ROM.

The ability to set a password for the Team Win recovery ROM in such a way that a simple "_fastboot flash recovery_" would overwrite would go a long way to improving device security. At least it would become evident to you if your recovery ROM has been replaced, in this case (due to the absence of the password).

It may also be possible to [restore your bootloader lock](https://android.stackexchange.com/questions/36830/whats-the-security-implication-of-having-an-unlocked-boot-loader) as an alternative, but then you lose the ability to make backups of your system using Team Win.

## Future Work: Disk Encryption via TPM or Clever Hacks

Unfortunately, even disk encryption and a secure recovery firmware is not enough to fully defend against an adversary with an extended period of physical access to your device.

[Cold Boot Attacks](http://www.extremetech.com/computing/150536-how-to-bypass-an-android-smartphones-encryption-and-security-put-it-in-the-freezer) are still very much a reality against any form of disk encryption, and the best way to eliminate them is through hardware-assisted secure key storage, such as through a [TPM chip](https://en.wikipedia.org/wiki/Trusted_Platform_Module) on the device itself.

It may also be possible to mitigate these attacks by placing key material in SRAM memory locations that will be overwritten as part of the [ARM boot process](http://rhombus-tech.net/allwinner_a10/a10_boot_process/). If these physical memory locations are stable (and for ARM systems that use the SoC SRAM to boot, they will be), rebooting the device to extract key material will always end up overwriting it. Similar ARM CPU-based encryption defenses have also been [explored in the research literature](http://www1.informatik.uni-erlangen.de/filepool/projects/armored/armored.paper.pdf).

## Future Work: Download and Build Process Integrity

Beyond the download integrity issues mentioned above, better build security is also [deeply needed](https://blog.torproject.org/blog/deterministic-builds-part-one-cyberwar-and-global-compromise) by all of these projects. A [Gitian descriptor](http://gitian.org/) that is capable of building Cyanogenmod and arbitrary F-Droid packages in a reproducible fashion is one way to go about [achieving this property](https://blog.torproject.org/blog/deterministic-builds-part-two-technical-details).

## Future Work: Removing Binary Blobs

If you read the [Cyanogenmod build instructions](http://wiki.cyanogenmod.org/w/Build_for_flo) closely, you can see that it requires extracting the binary blobs from some random phone, and shipping them out. This is the case with most ROMs. In fact, only the [Replicant Project](https://en.wikipedia.org/wiki/Replicant_%28operating_system%29) seems concerned with this practice, but regrettably they do not support any wifi-only devices. This is rather unfortunate, because no matter what they do with the Android OS on existing cell-enabled devices, they will always be stuck with a closed source, backdoored baseband that has direct access to the microphone, if not the RAM and the entire Android OS.

Kudos to them for [finding one of the backdoors](http://redmine.replicant.us/projects/replicant/wiki/SamsungGalaxyBackdoor) though, at least.

# Changes Since Initial Posting

1. Updated [firewall scripts](https://people.torproject.org/~mikeperry/android-hardening/android-firewall.zip) to fix [Droidwall permissions vulnerability](https://code.google.com/p/droidwall/issues/detail?id=260).
2. Updated Applications List to recommend VLC as a free media player.
3. Mention the Guardian Project's planned Tor Browser port (called OrFox) as Future Work.
4. Mention disabling configured WiFi network auto-probing as Future Work
5. Updated the [firewall install script](https://people.torproject.org/~mikeperry/android-hardening/android-firewall/install-install.sh) (and the [android-firewall.zip](https://people.torproject.org/~mikeperry/android-hardening/android-firewall.zip) that contains it) to disable "Captive Portal detection" connections to Google upon WiFi association. These connections are made by the _Settings_ service user, which should normally be blocked unless you are Activating Google Play for the first time.
6. Updated the Executive Summary section to make it clear that our SIP client can actually also make normal phone calls, too.
7. Document removing the built-in microphone, for the truly paranoid folk out there.
8. Document removing the remnants of the baseband, or disabling an existing baseband.
9. Update SHA256SUM of FDroid.apk for 0.63
10. Remove multiport usage from firewall-tor.sh script (and update [android-firewall.zip](https://people.torproject.org/~mikeperry/android-hardening/android-firewall.zip)).
11. Add pro-tip to the microphone removal section: Don't remove your cameras. Black electrical tape works just fine, and can be removed and reapplied many times without smudges.
12. Update [android-firewall.zip](https://people.torproject.org/~mikeperry/android-hardening/android-firewall.zip) installation and documentation to use **/data/local** instead of **/etc** . CM updates will wipe /etc, of course. Woops. If this happened to you while updating to CM-11-M5, download that new android-firewall.zip and run **install-firewall.sh** again as per the instructions above, and update your Droidwall custom script locations to use **/data/local** .
13. Update the Future work section to describe some specific UI improvements.
14. Update the Future work section to mention that we need to find hardware with actual isolated basebands. Duh. This should have been in there much earlier.

