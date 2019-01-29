---
layout: post
title: How to SSH using keys setup
published: true
---

Because people forget how to properly set permissions and name authoirized\_keys files ;)

cd ~

mkdir -pm 700 ~/.ssh;

chmod 600 ~/.ssh/authorized\_keys&gt;&gt;~/.ssh/authorized\_keys

Enable pubkey auth:

&nbsp;sudo sed -i 's/^#PubkeyAuthentication/PubkeyAuthentication/g' /etc/ssh/sshd\_config

restart ssh

sudo service restart ssh