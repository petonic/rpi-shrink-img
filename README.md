# rpi-shrink-img
Shellscript to shrink .iso images that contain Raspian SD card images (but not NOOBS since it has more than 2 partitions on
the SD card).

Because Mac's aren't good at ext4, this should be run on a Linux machine of some sort.  I personally use the RPI Pixel VM running under VMWware on my MBP.  It's a ton faster than running it on an actual RPI3.

This utility takes one parameter, which is the name of a .iso disk image
with a Raspian partition layout (#1=VFAT, #2=ext4).  It resizes the #2 partition to a minimal size, so that the output .ISO is easier to copy
and store.

Snarfed from
http://blog.osnz.co.nz/post/97106494057/shrinking-raspberry-pi-sd-card-images-for

Modified on 2017-02-02 by Mike Petonic to:

* Add a buffer of about 200M because "resize2fs -M" is a bit
    toooo aggressive and booting from the SD card left you
    with very little (0) space.  Can't even run bash...
* Modernized the commands to fdisk to reflect current Linux version
    of fdisk
* Prepended priveleged commands with sudo, because, well, lazy

This script is licensed under the [WTFP License ](http://www.wtfpl.net).

![WTFPL Logo](http://www.wtfpl.net/wp-content/uploads/2012/12/wtfpl-badge-1.png)
