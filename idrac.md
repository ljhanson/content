---
title: Idrac Notes
date: 2019-09-12
author: L.J. Hanson
tags:
    - bash
    - Idrac
    - linux
    - notes
    - server management
slug: Idrac Notes
categories:
    - Dell servers
    - iDRAC
    - IT infrastructure
    - power management
    - remote access
    - server management
---

How to restart/power off from idrac terminal

```bash
# power server off
racadm serveraction powerdown

# power server on
racadm serveraction powerup

# perform server power cycle
racadm serveraction powercycle

# force hard server power reset
racadm serveraction hardreset
```
