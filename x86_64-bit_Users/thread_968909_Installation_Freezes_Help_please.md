---
title: "Installation Freezes Help please"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by fattymatty on 2008-11-03
Hi I downloaded today 8.1 desktop 64bit edition and it wont let me get thru installation. it will freeze at one point or another. i used partition magic to format the drive to cut down on the work it had to do but that just allowed me to get farther along once i got to 57% but most times will freeze long before that. any ideas

also i am currently using the live cd to type this so its wierd that this works and not install

---

### Post by dabl on 2008-11-03
That's the classic symptom of a bad CD burn.

Review:

1. Check downloaded ISO file's md5sum, make sure it matches the md5sum for that file on the download site.

2. Burn the CD at 4X speed, DAO mode.

3. Sometimes you end up with a coaster anyway.  Alternatives: use a different brand blank media, use a different PC and burner.

---

### Post by amgalitz on 2008-11-04
verify the MD5 checksum of the iso before burning: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
here are the checksums: [http://whyamistilltyping.wordpress.com/2008/11/01/ubuntu-810-intrepid-ibex-md5-checksums/?referer=sphere_related_content/](http://whyamistilltyping.wordpress.com/2008/11/01/ubuntu-810-intrepid-ibex-md5-checksums/?referer=sphere_related_content/)
use the install livecd session menu option to verify the burned CD before starting the install.

Don't use partition magic for linux installation. It can screw up the partition table. I've used it for years but read this and switched to the linux tools this summer after a partition table corruption.
The partitioner on the livecd for Ubuntu install is actually pretty good. It lets you add labels to your partitions at creation which helps when ubuntu automounts your partitions in /Media. 
You can label existing partions without damage using tools for the file system on them:
For ext2 and 3, it is e2label
the others, reiser, xfs all have there labelers, just google.

GParted is the Gnome Partition Editor application: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
this is the livecd (bootable version): [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

cheers

---

