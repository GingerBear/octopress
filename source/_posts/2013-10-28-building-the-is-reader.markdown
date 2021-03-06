---
layout: post
title: "Building the IS Reader"
date: 2013-10-28 02:16
comments: true
categories: [project, dev, JavaScript]
---

It has been a few weeks that I am thinking about writing a blog on the IS Reader project. In this post, I will try to answer:

*	Why did I start the project? 
*	What will the product be functioning like? 
*	How did I or will I deal with it? 
*	What are the design rules that I am following? 

## Why did I start the project?

There are a lot of reasons that finally lead me to build this reader. First and most importantly, When I reading some long documents, like a book, I found myself need a sample tool that can store a pdf document online, and everytime you open it on different devices, it will restore the previous page you read. I went throught a series of search but didn't find a sample solution. Kindle App may work but not allow pdf uploads. Dropbox and Google Drive show pdf cross device but cannot restore the progress, no need to say annoating or sharing. Foxit reader can restore but only work locally. 

The secend reason is that, I was happened to take an independent study with Peter's, our program head, phd student Julio, who took me to the ReadingCycle project. It is also a reader project, but only work for picture format books. So it is a good change to do it along with the IS Reader. (Actually IS Reader the name came with the inital of School of *Information Science*, but not limit to that.)

Thirdly, I am on my way finding a job, this project will be a great enhancement of my experience and CV. I will try a lot of new technologies that could be written on my CV.

Finally, there is no such a product on the web and it is not that hard to build, so why don't I create one. Maybe it will grow into a real deal.

## What will the product be functioning and look like?

On the first thought, the product is pretty sample. I can upload pdf documents on it, read it, restore the page on other devices and continue reading. By further thinking, it should support multi-user, not just me alone. Then it should provide a certain management page that can CRUD those documents. Next, it should allow user to annotate on the document. Finally, social stuff. User can share documents, notes with each other. They can track their progross. Product can even provide some kind of stratagy that my drive user to reader more, like comparing, gamification. 

At this moment of my typing, I am thinking the goal of the product should be to **make people more like to read**, or to learn, since I read for learn. 

## How did I or will I deal with it?

As I mentioned, the article should be typed several weeks ago, which means I have started working on it for several weeks (19 days since its github inital commit). I choosed all those new technology from the begining. At the begining scaffolding stage, I user Yeomen to genate a express project and a webapp (merged in the middle of developing, cover later).

I use pdf.js for the JavaScript-based pdf rendering. Although its rendering is a bit not that sharp on windows, it is good enough for long time reading. Not surprisingly, it renders perfectly on MacBook Pro with Retina display (need to fix the scale issue), the one I just bought, and better on mac with no-Retina than windows.

For the server, I use Express on Node.js, Mongoose and MongoDB for the database, Jade for the template engine. In fact, I tried to build a pure RESTful for the server, so I didn't use Jade at the first time. But met a lot of issues. First I came across some cross-domain issue on the cross ajax call from the client. I tried jsonp and cors to fix it. Then I didn't find a way to validate user session in a rapid way except cookies (I don't have experience with OAuth). So I gave up the RESTful option, in order for the quick shipping.

For the client side, most code I wrote is about the reader page. The logic is sample and old-fashion, just some event binding and ajax call, store data in the dom. What's new is that I try to use some new JavaScript techniques. I use event delegation of those massive event bindings. I wrap the whole reader JavaScript logic in a constructor, which construct the JavaScript by parameters, hide internal private parameters and methods, and get inited by init(); Some progress was made, but way not enough. The code is close to spaghetti, dom bindings are hard coded inside. I am extremely want to make it modular and less coupled, maybe after a big release. 

Now, basic funcitons till making note are made. Next thing should be involved with some social, with OAuth bulid in, and books management with one-page app style (AngularJS or BackboneJS).

## What are the design rules that I am following? 

It is too late now, let me be short. For the design, 3 rules:

*	Rule 1: As easy to use as possible
*	Rule 2: As less reading interuption as possible
*	Rule 3: As clean and sample as possible


## Summary

Use the most quoted facebook works:

> Keep Focus and Keep Shipping

That is all I need to do, no need to think to far. No matter what will the product be in the future, it has a good start, namely I build it for myself use.