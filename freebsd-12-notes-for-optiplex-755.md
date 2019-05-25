Title: FreeBSD 12 notes for Optiplex 755
Date: 2019-01-12 21:40
Author: L.J. Hanson
Slug: freebsd-12-notes-for-optiplex-755

Things to remember for next FreeBSD 12  install.

-   To switch to current, as opposed to quarterly packages:
    </p>
    -   Create the file /usr/local/etc/pkg/repos/FreeBSD.conf with the folowing content

    </p>

</p>
      FreeBSD: {  url: "pkg+http://pkg.FreeBSD.org/${ABI}/latest"  }  

</p>
-   drm-kmod package from ports gets KMS to work.

</p>
