---
layout: post
title: How to enable SSH on Raspberry Pi Zero W
published: true
---

In the previous post I have described how to quickly connect and start using your brand new [Raspberry Pi Zero W](https://amzn.to/2Urs28p){: target="_blank"}&nbsp;(Melopero).

Today it is time to enable the SSH, so lets get to work!

* Power up Rasp
* Open the terminal on Rasp
* Run the following command:

> sudo raspi-config

The following screen should pop up, so please choose option number 5:&nbsp;

*"Interfacing Options"*

![](/upload/pi-ssh/IMG_20190128_162053.jpg)Then choose:&nbsp;*"P2 SSH"*![](/upload/pi-ssh/IMG_20190128_162059.jpg)

Answer *"Yes"* when asked: *"Would you like the SSH server to be enabled?"*![](/upload/pi-ssh/IMG_20190128_162107.jpg)

And finally you should see the following confirmation: *"The SSH server is enabled"*:![](/upload/pi-ssh/IMG_20190128_162115.jpg)

Select: *"Ok",&nbsp;*and that's it! SSH service should be up and running.

* Now, run the following command:

> ifconfig

to check the IP of our Rasp:

![](/upload/pi-config/img-20190128-144917.jpg)

* So you can finally connect to your Rasp via SSH 🙌

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQYV2P4////fwAJ+wP9BUNFygAAAABJRU5ErkJggg==){: .cms-image-placeholder}![](/upload/pi-hole/_20x9-0x-R_at_x8.x9.55.png)

That's all!

*Source:&nbsp;[https://www.raspberrypi.org/documentation/remote-access/ssh/](https://www.raspberrypi.org/documentation/remote-access/ssh/){: target="_blank"}*