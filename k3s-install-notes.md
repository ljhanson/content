---
title: K3s Install Notes
date: 2023-01-07T11:34:03-05:00
draft: false
tags:

- docker
- install
- kubernetes
- linux
- notes

categories:

- cloud infrastructure
- container orchestration
- DevOps
- K3s
- Kubernetes
- Linux administration
- server setup
- system upgrades

author: L.J. Hanson

---

# K3 Install Notes

## Pre-Setup

For 8Gb host use external mounts

```sh
ln -s /datadrive/k3s/ /run/k3s

ln -s /datadrive/k3s-pods/ /var/lib/kubelet/pods

ln -s /datadrive/k3s-rancher/ /var/lib/rancher

## Install

```sh
        '--disable' \
        'traefik' \
        '--disable' \
        'servicelb' \
        '--disable' \
        'metrics-server' \
        '--disable' \
        'local-storage' \
        '--write-kubeconfig-mode 644' \
        '--node-label "k3s-upgrade=true"' \
        '--flannel-backend=wireguard-native'
```

- For worker nodes need:
    - K3S_TOKEN is at /var/lib/rancher/k3s/server/node-token on server
    - K3S_URL is "https://<server host>:6443"

## Setting up upgrades
Install upgrade server

```sh

kubectl apply -f https://github.com/rancher/system-upgrade-controller/releases/latest/download/system-upgrade-controller.yaml

```

Need to label each node with "k3s-upgrade=true"

```sh

kubectl label nodes <your-node-name> <label>

```

Once completed need to add an upgrade [plan](https://raw.githubusercontent.com/rancher/system-upgrade-controller/master/examples/k3s-upgrade.yaml). Edit to suit, and apply.
