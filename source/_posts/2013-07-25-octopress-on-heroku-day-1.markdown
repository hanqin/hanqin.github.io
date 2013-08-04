---
layout: post
title: "octopress on heroku - day 1"
date: 2013-07-25 23:10
comments: true
categories: [notes, octopress, octopress plugins]
keywords: octopress, octopress plugins
description: setup octopress on heroku
---

### Tasks

1. Setup [octopress](http://octopress.org/) according to the [documentation](http://octopress.org/docs/)
2. Update blog configuration, ruby version as well(required by heroku)
3. Created a [test blog](http://hanqin.herokuapp.com/blog/2013/07/25/this-is-a-test/)
4. Update google analytics
    * Thanks to this [article](http://stefanalfbo.github.io/blog/2013/04/17/octopress-google-analytics-github-pages/)
5. Markdown [cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#wiki-headers)

### Problems

1. Google analytics not working, solution as mentioned above
2. Slow connection to heroku

```
git push heroku master
```
but only got Operation/Connecting timed out error. To fix the issue, manually add ~/.ssh/config, and put following lines in it:
```
Host heroku.com
User freemember007
Hostname 107.21.95.3
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
port 22
```
Thanks to this [article](http://ruby-china.org/topics/10813)

### Next

1. Comment