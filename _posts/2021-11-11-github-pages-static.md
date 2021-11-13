---
layout: post
title:  "Jekyll, 1 of [redacted]"
date: 2021-11-11 14:58:00 -0400
---
How did [Abdullah Ameen](https://github.com/AbdullahAmeen) do this?
&nbsp;

[![screenshot of Abdullah Ameen's web portfolio](/assets/21-11-11-abdullah-ameen-screenshot.png)](https://abdullahameen.github.io/)
&nbsp;

tl;dr _it's not always Jekyll..._

Lately, when I've had some spare time to work on projects, I've been trying to get this website up and running. I wanted to have a portfolio-type space while I'm looking for jobs, and also just a space to work through what I'm learning. That means I've been spending a lot of time with Jekyll. So far so good, as a Jekyll newbie it's been pretty smooth.

I have some experience with web frameworks, particularly Django, and so this workflow made sense to me. Write your little markdown files, make sure they have the right names and live in the right folders, and Jekyll will hand you a set of nicely formatted static web pages.

I came to Jekyll in the same way I imagine a lot of people do, through Github Pages. After I realized that Github will host a small home page and blog for free, and that they had deputized Jekyll as the go-to web framework to get that done, I jumped in and got to work.

After I got the website up and running through Github Pages, I started to think about getting that sort of portfolio space working. From the beginning, I'd been looking for examples of GIS portfolios that people have created and hosted in the same way. Abdullah Ameen's website that I linked to above is one of the first that appears in search results.

I have my [Projects](/projects/) page set up, but in my mind it's only a first draft. The single-column setup is overwhelming already, and I only have two of my previous projects up there. I'm aiming to have probably more like a dozen, and it's going to be borderline unreadable unless I figure something else out.

The way Abdullah designed it, by contrast, is awesome. The design style looks dated, but I love the tidiness of the grid layout. Each project link is a small version of the project it links to. It's like a menu in the restaurant sense, it gives you a teaser of each item without overwhelming you with detail.

Since Abdullah's site, just like mine, is also hosted through Github Pages, I thought I would pull a "great artists steal" and try to emulate their portfolio menu. Though, admittedly, I haven't gone deep on this yet, I pretty quickly noticed that Jekyll, or at least the Minima theme that I'm using, doesn't immediately lend itself to doing this.

Jekyll/Minima is really good at taking the content of markdown files, like the one I'm writing right now, resolving all the image links and hyperlinks, dusting off whatever formatting I've written in, and generating a static web page that kind of just reads from top to bottom. Here's a screenshot of my current Projects page setup for posterity:
&nbsp;

![a screenshot of my Projects page](/assets/21-11-11-projects-screenshot.png)
&nbsp;

It looks fine, right, but the point of this page is to really display all of my projects in a way that lets the user have a zoomed-out sense of what's going on, and pick and choose which projects to look at further. From this screenshot, you can't even tell that there are two other maps on the Projects page, they just get buried and you have to scroll. I don't love it.

The beauty of open source is that you can really have a look at different programs' guts, if you want to. So I headed over to the Github page for Abdullah's website to just literally see how they implemented the website menu in Jekyll. Here's this post's punchline: turns out that Github Pages will host your site and __you don't even need to use Jekyll at all__.

Abdullah's whole site is written in HTML and Javascript! I'm laughing at myself a bit now, but for a while I was really scratching my head. My assumption was that, in order to have your site hosted on Github Pages, you needed to use Jekyll. Turns out it's not that tightly coupled. I haven't tried it yet, but from this experience my guess is that if you set up a repository for Github Pages, it will host whatever content you put in there and it will work properly as long as it's a static website.

Is this useful to me? I guess on one hand it's just kind of interesting, it seems like Jekyll is the only way you can get your website automatically built within the Github pages setup, but that you can really host anything you want as long as its static, down to the old-school HTML-CSS-javascript way of doing things. Beyond that, it tells me---assuming I can't find a Jekyll theme that will do what I want---that I may have to get more into writing the HTML that will give me the portfolio menu layout I'm after.

Far as I understand, that's possible even inside of Jekyll using Liquid, but that's for another day.
