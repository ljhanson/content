---
title: Ubuntu unattended upgrades
date: 2021-01-21
category: Linux
tags:
- ubuntu
- linux
slug: ubuntu-unattended-upgradws
author: L.J. Hanson
summary: Unattended upgrades for Ubuntu
---

How to setup a Ubuntu install to do unattended upgrades.
Based off content available [here](https://libre-software.net/ubuntu-automatic-updates/)

```bash
sudo apt -y install unattended-upgrades
sudo vim /etc/apt/apt.conf.d/50unattended-upgrades
```

Add/Update the following:

> Unattended-Upgrade::Remove-Unused-Kernel-Packages "true";
>
> Unattended-Upgrade::Remove-Unused-Dependencies "true";
>
> Unattended-Upgrade::Automatic-Reboot-WithUsers "true";
>
> Unattended-Upgrade::Automatic-Reboot-Time "02:00";

```bash
sudo vim /etc/apt/apt.conf.d/20auto-upgrades
```

Add/Update the following:

> APT::Periodic::Update-Package-Lists "1";
>
> APT::Periodic::Download-Upgradeable-Packages "1";
>
> APT::Periodic::AutocleanInterval "7";
>
> APT::Periodic::Unattended-Upgrade "1";
