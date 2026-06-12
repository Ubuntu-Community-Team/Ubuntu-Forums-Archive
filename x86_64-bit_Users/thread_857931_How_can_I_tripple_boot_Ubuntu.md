---
title: "How can I tripple boot Ubuntu?"
date: 2008-07-13
forum: x86 64-bit Users
---

### Post by thenetduck on 2008-07-13
Hi, 
I would like to triple boot ubuntu with Vista, Ubuntu Gusty, and Ubuntu Hardy. 

Right now my computer is dual booting Vista and Hardy. I want to keep vista for kicks. I think I have booted into it like 3 times, but still want to keep it because some times people that use my computer want to play games in it. 

Can I just install Gusty without it messing things up? I want to use Gusty because the kernel downgrade will work with Kismet. 

Thanks guys! 
The Net duck

---

### Post by cjm5229 on 2008-07-13
It should work OK, if Hardy won't boot after you install Gutsy, you will have to boot into your Hardy partition and make sure the UUID's in fstab are the same. Usually the new root partition will have a different # than the same partition in the old one. Either change the old one to match the new one, or just comment the old one out. I use a root file manager ```
gksudo nautilus
``` go to etc/fstab and open it with gedit. then navigate to the other root partition, and do the same thing. they will be in tabs in gedit change as necessary then save and exit. 
this is my fstab for Hardy
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=d05218ec-2619-40a3-80d2-05bc9b8fa403 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=56cdfb92-1fe3-40d5-b80a-90d98ad247f8 /home           ext3    relatime        0       2
# /dev/sda7
#UUID=020e0fd6-ffbd-4310-93fb-af67167be80d /media/sda7     ext3    relatime        0       2
# /dev/sda6
UUID=38253e08-83c8-4c50-bd3c-60f176e385d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

this is my fstab for Intrepid# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=ede22996-553b-40fa-89c9-80d7b71a2e78 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=56cdfb92-1fe3-40d5-b80a-90d98ad247f8 /home           ext3    relatime        0       2
# /dev/sda6
UUID=9659c41e-51a2-47c8-a42d-b5c8451789a5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

notice I commented out the sda7 partition in the Hardy one because it doesn't match the one for Intrepid.

---

