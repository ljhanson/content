---
title: Pi Install Notes
date: 2020-12-07
author: L.J. Hanson
tags:
- pi
- install
- vpn
- pihole
slug: Pi_Install_ Notes
---

#Inital Install
sudo apt update
sudo apt upgrade
sudo apt install avahi-daemon docker.io docker-compose
sudo dpkg-reconfigure tzdata
sudo adduser ljhanson
sudo usermod -G docker, sudo
sudo hostnamectl set-hostname pi
sudo sed -r -i.orig 's/#?DNSStubListener=yes/DNSStubListener=no/g' /etc/systemd/resolved.conf
Add hostname to /etc/hosts
curl -L https://install.pivpn.io | bash
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https

# Next two needed to keep DNS/DHCP on internal network only if using ipv6

tunnel
sudo ufw allow in on eth0 to any port 67
sudo ufw allow in on eth0 to any port 53

# Default policy

sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw enable
