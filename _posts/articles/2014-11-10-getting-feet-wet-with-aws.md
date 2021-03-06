---
layout: post
title:  "Getting feet wet with AWS"
date:   2014-11-10
categories: articles
tags: [data science, Amazon Web Services, AWS, EC2, S3, RDS, SimpleDB]
comments: true
share: true
---

I've been intrigued by **Amazon Web Services (AWS)** for a while now.  I spent some time this week exploring
the workhorse ([EC2](http://aws.amazon.com/ec2/)) and the warehouse ([S3](http://aws.amazon.com/s3/)) among a couple other more lightly used AWS offerings ([SimpleDB](http://aws.amazon.com/simledb/) and [RDS](http://aws.amazon.com/rds/)).

Here's [the presentation](http://slides.com/ajb073/web-scraping-and-persisting-data-in-the-cloud) I shared with my company during an internal tech-time with my fellow data geeks:

<iframe src="//slides.com/ajb073/web-scraping-and-persisting-data-in-the-cloud/embed" width="576" height="420" scrolling="no" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

### First impression

Admittedly, I don't have a slew of cloud computing experience for comparison, but I was thoroughly impressed with the capabilities and usability of AWS, especially EC2.  A data scientist with intermediate-ish command line skills, basic knowledge of technology, and a little bit of patience can be their own [Sysadmin](http://en.wikipedia.org/wiki/System_administrator) and [DBA](http://en.wikipedia.org/wiki/Database_administrator) pretty quickly.  

In the past, I always felt like I was walking on eggshells working on servers, usually just a partition of some bigger machine doing at least something important.  Usually some system or network admin would handle things my user role didn't have permissions to do in the background, which could be nice, or slow, or a total road block.  Not so with EC2.  They take care of all the hardware and give you the reins for everything else -- the fun stuff.  I found I learned a lot more with the license to be dangerous.  Worst case, terminate your instance and built it again.  Just don't do it on the beefy (and pricy) 8Xlarge 32 core instance...

### Getting started

I have to say I was thoroughly impressed with how easy it was to get started.  The great thing about getting started with AWS is that there are minimal environment-specific issues to bog you down, since you're really not working with your environment or your computer.  The chunk of polycarbonate in front of you is just the vessel.  And if you're like me, those simple 2 line installation READMEs that go something like 

{% highlight bash %}
get someNew.thing
install someNew.thing
{% endhighlight %}

work maybe 1 in 5 times without having to install some hidden environment-specific dependency, manage multiple versions of the same thing, modify your PATH, or scour StackOverflow hoping someone had the same issue requiring you to modify your specific environment somehow to accommodate the new thing.

### AWS is everywhere

I was doing some research on S3 vs. Dropbox... and then I discovered that [**Dropbox** actually uses (or at least used to use) S3 to host](http://www.datacenterknowledge.com/archives/2013/10/23/how-dropbox-stores-stuff-for-200-million-users/) all your favorite kitten photos and documents you save to Dropbox.

Curious to see how **slides.com**, which I used to generate my slides would handle images when I exported the presentation to HTML, I inspected the exported HTML code to find that the platform automatically saves and hosts your content to S3.  Each image (and other rich content, I expect) is available from a unique URL to an S3 bucket.  


### Making of the slides

I also took this opportunity to experiment with some new slide/presentation technologies.  Having used Powerpoint and LibreOffice Impress for most of my presentations in the past, I wanted to mess around with some of the web technologies/platforms.  [impress.js](http://bartaz.github.io/impress.js/#/bored) and [prezi](http://prezi.com/your/) seemed a little dramatic and flashy for my purpose.  I liked the simple style of [reveal.js](http://lab.hakim.se/reveal-js/#/), so I started there.  The framework seemed relative straightforward and even supports markdown which I use to write this here blog, so that was cool.

However, not writing HTML and JavaScript everyday, I was spending more time tweaking code than working on content.  For a more serious presentation, I definitely could have committed more time to this, but I was looking to throw together some casual slides together pretty quickly.  I ended up using [slides](http://slides.com) (the online graphical editor for reveal.js) which I found to be a simple yet useful and impressive solution.

##### Cool things about [slides](http://slides.com): 

* **name.** Seriously, no one thought of [slides.com](http://slides.com) before now?
* **free version** for public presentations.
* **export presentation to HTML**, albeit  messy HTML.  
* **images and content hosted on S3**, so HTML presentation can stand-alone (no zipping and emailing dozens of files around) if you want to share presentation via email.
* **simple features** I used almost all the features available, but didn't find myself desiring much more.  Good balance that kept me focused on content.
* **intuitive UI:** I enjoyed not having to navigate worlds of dropdowns, ahem Powerpoint.
* **code blocks:** scrollable code blocks embedded directly in the presentation.
* you get the code, so you can **customize with reveal.js** as much as you want after getting started with slides.  *Note: untested...this may or may not be a good idea.*


