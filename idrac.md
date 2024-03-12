---
title: Idrac Notes
date: "2019-09-12"
author: L.J. Hanson
tags:
- Idrac
slug: Idrac Notes
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
