Frontmatter-formatted blog posts from [https://blog.torproject.org/](https://blog.torproject.org).

This repo contains a reduced number of posts to shorten development compilation times. The full dump of post/comment/event data is available here: [http://github.com/jmtodaro/tor-blog-data](http://github.com/jmtodaro/tor-blog-data).

Linked with issue [10479](https://trac.torproject.org/projects/tor/ticket/10479)

```bash

cd ../tor-blog

gem install jekyll
bundle install
jekyll serve

```

Or build it to be served on any flat file server:

```bash

jekyll build

```
