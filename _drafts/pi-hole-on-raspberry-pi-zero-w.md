---
layout: post
title: Pi-hole on Raspberry Pi Zero W
published: true
---

In the previous post I have described how to quickly connect and start using your brand new [Raspberry Pi Zero W](https://amzn.to/2Urs28p){: target="_blank"}&nbsp;(Melopero).

Today it is time to install [Pi-hole](http://bit.ly/pi-hole-raspberry){: target="_blank"}. What is Pi-hole:

> Pi-hole&reg;&nbsp;<br>Network-wide Ad Blocking
>
>
> A black hole for Internet advertisements"

Lets get to work! First, check the IP of our raspberry pi:

![](/uploads/img-20190128-144917.jpg)

Write it down, we will need it later.

Now we have to enable SSH. Run:

> *sudo raspi-config*

And the following screen should pop up:

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQYV2P4////fwAJ+wP9BUNFygAAAABJRU5ErkJggg==){: .cms-image-placeholder}