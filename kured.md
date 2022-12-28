---
title: "Kured - Kubernetes Restart Daemon"
date: 2022-12-28
author: L.J. Hanson
tags:
- kubernetes
slug: kured-restart-daemon
description: "Kured (KUbernetes REboot Daemon) is a Kubernetes daemonset that performs safe automatic node reboots when the need to do so is indicated by the package management system of the underlying OS."
---

[Kured](https://github.com/kubereboot/kured) is a Kubernetes daemonset that performs safe automatic node reboots when the need to do so is indicated by the package management system of the underlying OS.
This should allow a full OS install, to be more like an appliance install like K3OS which is no longer being actively developed.
