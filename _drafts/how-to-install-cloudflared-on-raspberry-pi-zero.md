---
layout: post
title: How to install cloudflared on Raspberry Pi Zero
published: false
---

How to Install and configure ["Cloudflared"](j.mp/dns-over-https){: target="_blank"} on Raspberry Pi Zero

wget https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-arm.tgz<br>--2019-01-28 20:17:20-- &nbsp;https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-arm.tgz<br>Resolving bin.equinox.io (bin.equinox.io)... 52.3.53.115, 52.4.95.48, 52.22.236.254, ...<br>Connecting to bin.equinox.io (bin.equinox.io)|52.3.53.115|:443... connected.<br>HTTP request sent, awaiting response... 200 OK<br>Length: 8100930 (7.7M) [application/octet-stream]<br>Saving to: ‘cloudflared-stable-linux-arm.tgz’

cloudflared-stable-linux-arm.tgz &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;100%[==========================================================================================================&gt;] &nbsp; 7.73M &nbsp; 106KB/s &nbsp; &nbsp;in 58s

2019-01-28 20:18:19 (136 KB/s) - ‘cloudflared-stable-linux-arm.tgz’ saved [8100930/8100930]<br>&nbsp;

pi@raspberrypi:~ $ tar -xvzf cloudflared-stable-lin^C<br>pi@raspberrypi:~ $ cd /tmp/<br>pi@raspberrypi:/tmp $ clear<br>pi@raspberrypi:/tmp $ tar -xvzf cloudflared-stable-linux-arm.tgz<br>cloudflared<br>pi@raspberrypi:/tmp $ cp ./cloudflared /usr/local/bin<br>cp: cannot create regular file '/usr/local/bin/cloudflared': Permission denied<br>pi@raspberrypi:/tmp $ sudo cp ./cloudflared /usr/local/bin<br>pi@raspberrypi:/tmp $ chmod +x /usr/local/bin/cloudflared<br>chmod: changing permissions of '/usr/local/bin/cloudflared': Operation not permitted<br>pi@raspberrypi:/tmp $ sudo chmod +x /usr/local/bin/cloudflared<br>pi@raspberrypi:/tmp $ cloudflared -v<br>Segmentation fault<br>pi@raspberrypi:/tmp $ sudo cloudflared -v<br>Segmentation fault

j.mp/segmentation-fault-cloudflared-issues-38

&nbsp;

&nbsp;