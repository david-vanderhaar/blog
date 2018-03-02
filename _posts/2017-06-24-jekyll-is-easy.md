---
layout: post
title:  "Jekyll is Easy, Blogging is Hard"
date:   2017-06-24 14:26:30 -0400
categories: blog
---

## What is Jekyll?

So what is Jekyll anyway? It's a static website generator. It takes in your HTML, CSS, and Markdown files and it spits out a deployment-ready content for your personal, product or portfolio site.  

That's the most straight-forward answer. But the goodness of Jekyll isn't what it is, its what it can do for you as a developer.

## Why use Jekyll?

As a developer you may be familiar with GitHub. If not, you will be soon! One of the great things about Jekyll is that once you generate your simple website, you are offered free internet space on GitHub. No need for servers or databases. Jekyll and GitHub allow you to push content directly into your online repository, automatically updating your entire website.

The other Jekyll win is that the community has created an abundance of awesome themes ready to be used for your own content. Many of these themes are free, and interchangable allowing you to try on a ton of different looks. Look at these examples:

![Jekyll Example 1](http://xdesigns.net/wp-content/uploads/2016/04/w41Kgo3.jpg)
[See this one in action](http://thephuse.github.io/strange_case/)

![Jekyll Example 2](http://xdesigns.net/wp-content/uploads/2016/11/img_5829ccf728709-768x767.png)
[See this one in action](https://mmistakes.github.io/so-simple-theme/)

![Jekyll Example 3](http://xdesigns.net/wp-content/uploads/2016/04/Djui15f.jpg)
[See this one in action](http://themeforest.net/item/drava-multipurpose-theme-powered-by-jekyll/full_screen_preview/11383647?ref=gundoel007)

Still interested? Let's discuss how to get our own Jekyll sites up and running.

## How to use Jekyll?

Jekyll is a software. To get started let's download it in the command line. If you don't already of the Ruby Gem installer, grab that here [RubyGems Install](https://rubygems.org/pages/download) and then come back. Jekyll is much more fun to play with using gems.

#### Step 1: Install Jekyll

	gem install jekyll bundler

This command uses Ruby **gem**s to **install** the **jekyll bundler** as a software on your machine.

#### Step 2: Create a New Jekyll Site

	jekyll new my-new-website

This command uses **Jekyll** to create a **new** directory named **my-new-website** where jekyll will work its magic. You new directory will come with auto generated content to get you started. This is where you'll put all your awesome content.

#### Step 3: Run Your Site on Jekyll's Built-in Server

	cd my-new-website
	bundle exec jekyll serve

Using these commands we: **c**hange **d**irectories into your new folder. Then we **bundle** the auto-generated content that **jekyll** created, and throw onto a local **serve**r so we can view it in our browsers.

#### Step 4: Try it out

Go ahead and complete steps 1-3. After you've finished your new site should look similar to this:

![Screen shot of your new site](http://sitechop.com/images/posts/jekyll-guide/welcome.png)

Thanks for tracking with me! That's it for now, but next week we'll look at how to get our own content into Jekyll and looking nice.

In the mean time, check out [Jekyll's documentaion](https://jekyllrb.com/docs/home). It's amazing!

### Until Then

## Take it Easy
