---
layout: post
title: How to install cloudflared on Raspberry Pi Zero
published: false
---

How to Install and configure ["Cloudflared"](j.mp/dns-over-https){: target="_blank"} on Raspberry Pi Zero

| wget https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-arm.tgz<br>–2019-01-28 20:17:20– &nbsp;https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-arm.tgz<br>Resolving bin.equinox.io (bin.equinox.io)… 52.3.53.115, 52.4.95.48, 52.22.236.254, …<br>Connecting to bin.equinox.io (bin.equinox.io) | 52.3.53.115 | :443… connected.<br>HTTP request sent, awaiting response… 200 OK<br>Length: 8100930 (7.7M) [application/octet-stream]<br>Saving to: ‘cloudflared-stable-linux-arm.tgz’ |

cloudflared-stable-linux-arm.tgz &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;100%[==========================================================================================================&gt;] &nbsp; 7.73M &nbsp; 106KB/s &nbsp; &nbsp;in 58s

2019-01-28 20:18:19 (136 KB/s) - ‘cloudflared-stable-linux-arm.tgz’ saved [8100930/8100930]<br>&nbsp;

pi@raspberrypi:~ $ tar -xvzf cloudflared-stable-lin^C<br>pi@raspberrypi:~ $ cd /tmp/<br>pi@raspberrypi:/tmp $ clear<br>pi@raspberrypi:/tmp $ tar -xvzf cloudflared-stable-linux-arm.tgz<br>cloudflared<br>pi@raspberrypi:/tmp $ cp ./cloudflared /usr/local/bin<br>cp: cannot create regular file '/usr/local/bin/cloudflared': Permission denied<br>pi@raspberrypi:/tmp $ sudo cp ./cloudflared /usr/local/bin<br>pi@raspberrypi:/tmp $ chmod +x /usr/local/bin/cloudflared<br>chmod: changing permissions of '/usr/local/bin/cloudflared': Operation not permitted<br>pi@raspberrypi:/tmp $ sudo chmod +x /usr/local/bin/cloudflared<br>pi@raspberrypi:/tmp $ cloudflared -v<br>Segmentation fault<br>pi@raspberrypi:/tmp $ sudo cloudflared -v<br>Segmentation fault

j.mp/segmentation-fault-cloudflared-issues-38

sudo useradd -s /usr/sbin/nologin -r -M cloudflared

vi /etc/default/cloudflared

&nbsp;This file contains the command-line options that get passed to cloudflared on startup.

# Commandline args for cloudflared

Update the permissions for the configuration file and cloudflared binary to allow access for the cloudflared user

sudo chown cloudflared:cloudflared /etc/default/cloudflared sudo chown cloudflared:cloudflared /usr/local/bin/cloudflared

and add:

CLOUDFLARED\_OPTS=–port 5053 –upstream https://1.1.1.1/dns-query –upstream https://1.0.0.1/dns-query

Then create the systemd script by copying the following in to /lib/systemd/system/cloudflared.service. This will control the running of the service and allow it to run on startup.

[Unit] Description=cloudflared DNS over HTTPS proxy After=syslog.target network-online.target [Service] Type=simple User=cloudflared EnvironmentFile=/etc/default/cloudflared ExecStart=/usr/local/bin/cloudflared proxy-dns $CLOUDFLARED\_OPTS Restart=on-failure RestartSec=10 KillMode=process [Install] WantedBy=multi-user.target

Enable the systemd service to run on startup, then start the service and check its status.

sudo systemctl enable cloudflared

sudo systemctl start cloudflared

sudo systemctl status cloudflared

Configuring DNS

If you have gotten to this point, you now have a working DNS-over-HTTPS service. But unfortunately, it’s only running locally on the device. The next steps will cover how to implement the service for network-wide DNS lookups via PiHole

pi@raspberrypi:/tmp $ grep PIHOLE\_DNS /etc/pihole/setupVars.conf<br>PIHOLE\_DNS\_1=127.0.0.1#53

sudo systemctl restart cloudflared

You may also be required to open this port in the firewall.

A client device such as a laptop or phone can now be configured to use it as the primary DNS server. You can verify it is working correctly by visiting the internet.nl DNSSEC test service.