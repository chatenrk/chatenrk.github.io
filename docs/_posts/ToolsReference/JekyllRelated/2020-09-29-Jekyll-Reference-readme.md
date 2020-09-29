---
layout: post
title: Jekyll Reference
categories: [Tools Reference]
tags: [jekyll,staticsite]
---

- [Prerequisites](#prerequisites)
- [Instructions](#instructions)

# Prerequisites
Jekyll requires the following:

Ruby version 2.5.0 or higher
RubyGems
GCC and Make
See [Requirements](https://jekyllrb.com/docs/installation/#requirements) for guides and details

# Instructions
1. Install all [prerequisites](#prerequisites).
2. Install the jekyll and bundler [gems](https://jekyllrb.com/docs/ruby-101/#gems).<br>
   `gem install jekyll bundler`
3. Create a new Jekyll site at `./myblog` <br>
   `jekyll new myblog`
4. Change into your new directory <br>
   `cd myblog`
5. Build the site and make it available on a local server <br>
   `bundle exec jekyll serve`
6. Browse to [http://localhost:4000](http://localhost:4000)