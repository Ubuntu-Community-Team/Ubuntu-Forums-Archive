---
title: "mountx extension?"
date: 2006-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by erniewinner on 2006-04-03
:confused:  hi all,

i'm looking for the mountx extention or similar programs mentioned here. (linux tools, linuxdisks.)
[http://gdr.free.fr/linux.html](http://gdr.free.fr/linux.html)
thanks.

---

### Post by ssam on 2006-04-03
is this to mount ext2/3 on a mac? there is [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) for mac os x

---

### Post by erniewinner on 2006-04-03
[http://home.mindspring.com/~swezen/mklinux/MountX_1.0a1.sit](http://home.mindspring.com/~swezen/mklinux/MountX_1.0a1.sit) 
i've got it, i read it is a bit ropey... and dead hard to find! yeah it is for macos i suppose the version for x is newer and safer but i don't wont to go to the trouble of installing that as well. i   hope it works. if not any other suggestions out there. i've yet to try it. thanks. :KS

---

### Post by erniewinner on 2006-04-03
](*,)  damn! mountx was written for 8. i could install that if i knew it was going to work but... 
i reinstalled ubuntu as i had reiserfs and i thought that was the reason the disk icon was not on the desktop, it only works with ext2? anyway thats what i used.  i am currantly using os 9.2.2 the drive turns up in drive setup but its not accessable in any way.

ok next step boot from live cd with command... casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop -- (i would like to pointout you don't include the last 2 charectors. (i found that out when it didn't work.) casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop 
yep it loaded... (it looks nice, but a liitle slow on my g3 233.)

now on to my problem.

 i can see the hard disk.but i am not allowed to drag and drop vmlinux or
initrd.img onto mypendrive. error "operation not permitted" while copying "/vmlinux". i see in permissions that only root can copy it. but what is the password for the live cd? hehe! nearly there now!

thanks.:rolleyes:

---

### Post by erniewinner on 2006-04-03
](*,) ](*,)  well i managed to get the files on the key drive by using cp vmlinux-2.6.12-9powerpc64-smp  /media/usbdisk + cp initrd.img-2.6.12-9-powerpc#6A3. these are the files not the shortcuts... renamed  file 1 to vmlinux (in linux kernals folder.)
renamed file 2 to ramdisk.initrd.gz (in system folder.) used the bootx app to put the files in etc on reboot i get an error: 

sorry a system error occurred. ".bootx extension" unimplemented trap. blah blah blah to restart with extensions off. :confused:

---

### Post by jdp on 2006-04-04
If it's to run on a G3 233 machine, you most certainly don't want to use the ppc64-smp kernal.  You just want the plain powerpc kernal.  I'm guessing you are using a Beige G3?  Getting the files over to the MacOS side is explained in most of the OldWorld install guides like the one I did: [http://www.applefritter.com/node/8936](http://www.applefritter.com/node/8936)

Is ther some reason you didn't do it that way, or are you trying to find a more "point-n-click" way to do it all?

---

### Post by erniewinner on 2006-04-04
to be honest i didn't quite get that last step. so yeah i was looking for a more point and click way to do it. it struck me as odd it said ppc64... but i went to the boot folder and there were two shortcuts one vmlinux and the ramdisk in the boot folder in plain site, i assumed this was them. so i did a properties look up on them and it gave me the info i assumed was correct. so i used it in the terminal and copied them over...

i suppose this leads to two ideas. 1. the install has copied the wrong files for my beige g3.
2. they are somewhere else. (which wouldn't make sense.) where would the files be??? thanks.

i'll have to set it up again and have a look. :-k

---

### Post by erniewinner on 2006-04-04
](*,)   bugger! oh well seems when you boot from the live cd the "filesystem" is that of the cd. accounting for pp64 + normal ppc being in the boot folder. 
i went up to the disk... (can't remember the name) icon and managed to see my hd and enabled the partition that has boot on it and copied the 2 files over to my usb drive. i heard the drive clicking as it worked. i wasn't so obsurvant as to notice the cd spin up last time i copied. renamed them but i still can't get in... i'll look at your guide and see if it looks any easier now. it can't be as bad as this. 

ok. so my problem is this i boot up and i'm stuck at a command line that says:

busy box v1.00 yadda yadda /bin/sh: can't access tty; job control turned off... arrrg!

---

### Post by erniewinner on 2006-04-04
[-( oh well i'm about done trying to get the mac up. i've got ubuntu on my pc. i suppose i could stick yellowdog back on. but i don't think they do security patches like ubuntu do.

cd /target
mkdir hfs
mount /dev/hdc6 hfs -t hfsplus

i got as far as this with the command line and got blah, blah,blah no such file or directory.

doing "df" doesn't list my drive? the installer called it hdc8 (installed) so i was guessing at hdc6 for the hfsplus partition.

i'm going for a long sleep... and a coffee! :-|

---

### Post by erniewinner on 2006-04-05
ha! it seems i forgot the kernal arguments for the drive. root=/dev/hdc8. i have a partial succes in that i have logged in but... i'm stuck at a flashing cursor??? wheres the nice ubuntu welcome screen? 8) thanks.

---

