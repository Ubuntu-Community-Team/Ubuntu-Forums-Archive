---
title: "No bootstrap?"
date: 2006-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by woopie49 on 2006-05-26
Downloaded Dapper nightly build (20062005) a week ago to try it out, booted from the burnt ISO file - live/install CD with no problems loading, everything works fine on my Dual 1.42 G4, however, when trying to do an install to HD from the CD, it only partitions ext3 and swap - no bootstrap partition, hence I cannot boot Ubuntu from the HD, I just get the ? folder on boot up.

I am a NewBee to Ubuntu/Linux thought I have checked out Breezy (I had Breezy installed on a HD to check it out and erased it to install Dapper).

Dapper install interface is a lot easier for NewBee's like myself except for when it comes to partitioning the HD, I took the easy way out and completely erased the (Breezy) HD and let Dapper do the automatic partitions for the OS, but only 2 partitions were partitioned.

Dapper is still loaded on the HD, I can see the HD when in Live CD mode but cannot mount it. I have loaded Dapper 3 times to HD with always the same result - no boot.

I would appreciate any comments about my situation and how to solve it.

Thank you

---

### Post by Rxke on 2006-05-27
Hm, that's weird. You could try a manual partitioning, if you can get the right info,  it's a bit of a hassle sometimes doing it right, but perfectly possible.

Do you only see two partitions? not the hfs ones that are mac-specific? Gparted shows my bootpartition as hfs formatted...

---

### Post by nkbj on 2006-05-27
Try it again with the latest daily build and file a bug report on [http://launchpad.net/malone](http://launchpad.net/malone) if it still fails. The installer has undergone a lot of changes the past week.

Regards,
Niels Kristian

---

### Post by woopie49 on 2006-05-27
Thanks for your replies guys, will download new nightly build and try again.  I'll do bug report if it still won't load.

---

### Post by jdp on 2006-05-27
Are you actually removing the old/failed partitions to have a large blank space, or are you just letting it reformat them over and over, and not re**partition** the space?

---

