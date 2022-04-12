---
layout: post
title:  "Setting up with Jekyll and github pages"
date:   2017-08-17 12:40:40 -0400
categories: jekyll update
---

I'm testing using [jekyll](https://jekyllrb.com/) and [github pages ](https://help.github.com/articles/creating-a-github-pages-site-with-the-jekyll-theme-chooser/). Here are my install notes



* install ruby gems locally
```
cat ~/.gemrc
install: --user-install
uninstall: --user-install
```
```
gem install bundler
gem install jekyll
```

* set path for local gems
```
cat ~/.bash_profile | grep PATH
PATH=$PATH:$HOME/.gem/ruby/2.7.0/bin
```

* setup github pages
```
mkdir adanner.github.io
cd adanner.github.io
jekyll new ./
git init .
git remote add origin git@github.com:adanner/adanner.github.io.git
bundle install --path ~/.gem
git add .
git push -u origin master
```

* browse locally with `bundle exec jekyll serve`
* update as needed with `bundle update`
