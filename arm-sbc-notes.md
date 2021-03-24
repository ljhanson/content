Title: ARM SBC Notes
Date: 2019-9-13 19:50
Author: L.J. Hanson
Tags: arm,sbc,notes,Fedora,docker
Slug: arm-sbc-notes

```bash
# Serial Console
screen /dev/ttyUSB0 115200
```

```bash
# Installing Fedora Images on host
sudo dnf -y install arm-image-installer
```

```bash
# Writing Image File
Usage: arm-image-installer <options>

 --addconsole    - Add system console to extlinux.conf
 --addkey=       - /path/to/ssh-public-key
 --image=IMAGE   - xz compressed image file name
 --media=DEVICE  - media device file (/dev/[sdX|mmcblkX])
 --norootpass    - Remove the root password
 --resizefs      - Resize root filesystem to fill media device
 --supported     - List of supported hardware
 --target=TARGET - target board
 --version       - Display version and exit
 -y              - Assumes yes, will not wait for confirmation

Example: arm-image-installer --image=Fedora-Rawhide.xz --target=Bananapi --media=/dev/mmcblk0
```

More help for Fedora is located at <https://fedoraproject.org/wiki/Architectures/ARM/Installation.>

Other OS, like FreeBSD or OpenBSD can be directly wrote to the minisd card assuming you pick the image for the specific SBC.
