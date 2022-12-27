---
title: Ensuring you have pip for Python 3 on FreeBSD
date: 2016-12-13
author: L.J. Hanson
tags:
- FreeBSD
- Python
- Pip
slug: ensuring-you-have-pip-for-python-3-on-freebsd
---
By default pip doesn't get installed with the python35 port. To fix this as root execute the following:

```shell
python3 -m ensurepip
```
