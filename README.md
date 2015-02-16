Development repo - [https://blog.torproject.org/](https://blog.torproject.org)
Linked with issue [10479](https://trac.torproject.org/projects/tor/ticket/10479)

A live copy of this repo can be found [here](http://tor.jmtodaro.com/blog/).

This repo contains a reduced number of posts to shorten development compilation times. Get the most recent full dump of post/comment/event data at: [http://github.com/jmtodaro/tor-blog-data](http://github.com/jmtodaro/tor-blog-data).


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
