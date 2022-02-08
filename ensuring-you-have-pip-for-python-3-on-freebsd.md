Title: Ensuring you have pip for Python 3 on FreeBSD
Date: 2016-12-13 03:01
Author: L.J. Hanson
Tags: FreeBSD, Python, Pip
Slug: ensuring-you-have-pip-for-python-3-on-freebsd

By default pip doesn't get installed with the python35 port. To fix this as root execute the following:

```shell
python3 -m ensurepip
```
