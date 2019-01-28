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

Once you’ve checked out on the new branches, &nbsp;you need to add this to /etc/pihole/pihole-FTL.conf(note you may need to create this file if it does not exist)

BLOCKINGMODE=NXDOMAIN

or

BLOCKINGMODE=NULL

depending on which method you prefer and then restart FTLDNS (pihole-FTL) to apply the change

sudo service pihole-FTL restart

![](/uploads/img-20190128-144917.jpg)

Once you’ve checked out on the new branches, &nbsp;you need to add this to /etc/pihole/pihole-FTL.conf(note you may need to create this file if it does not exist)

BLOCKINGMODE=NXDOMAIN

or

BLOCKINGMODE=NULL

depending on which method you prefer and then restart FTLDNS (pihole-FTL) to apply the change

sudo service pihole-FTL restart