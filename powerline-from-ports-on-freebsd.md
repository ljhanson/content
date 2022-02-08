Title: Powerline from ports on FreeBSD
Date: 2017-02-02 01:59
Author: L.J. Hanson
Tags: Python, FreeBSD, tmux, bash
Slug: powerline-from-ports-on-freebsd

In your .profile add the following:

```
/usr/local/bin/powerline-daemon -q
POWERLINE_BASH_CONTINUATION=1POWERLINE_BASH_SELECT=1
source /usr/local/lib/python2.7/site-packages/powerline/bindings/bash/powerline.sh
```

Partly from [here](https://www.unix-experience.fr/2016/installer-et-utiliser-powerline-sur-archlinux-et-freebsd/).
