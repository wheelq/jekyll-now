---
layout: post
title: How to setup SSH passwordless access using keys
published: true
---

Because people forget how to properly set permissions and name authorized\_keys files ;)

cd ~

mkdir -pm 700 ~/.ssh;

chmod 600 ~/.ssh/authorized\_keys&gt;&gt;~/.ssh/authorized\_keys

copy your pub key into that file.

Enable pubkey auth:

&nbsp;sudo sed -i 's/^#PubkeyAuthentication/PubkeyAuthentication/g' /etc/ssh/sshd\_config

sudo sed -i 's/^#AuthorizedKeysFile/AuthorizedKeysFile/g' /etc/ssh/sshd\_config

restart ssh

sudo service restart ssh