---
title: "dual boot  ubuntu 8.1 64 bit with xp"
date: 2009-02-19
forum: x86 64-bit Users
---

### Post by wewee on 2009-02-19
hello , i have installed win xp on my dv5t laptop 
now i ant to install ubuntu as dual boot , i already downloaded 8.1 64 bit version 
can i find any guides on how to do it ??
i have a 24 GB free partition just for ubuntu i also have a 5 gb free partition for SWAP ( i made them that way when i formatted)
note that i never used linux before , i am a windows person 
but i have read some reviews and partitionned my hard disk this way coz i knew i was going to install linux sooner or later 
i don't wanna use wubi , i have the ubuntu disc i downloaded last week , i only need step by step instructions to a full installation while being able to choose wich OS on startup
thank you

---

### Post by x33a on 2009-02-19
it's a really simple process, and since you have already made the partitions, it's even easier

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

the feisty tutorial will work for intrepid also.

---

### Post by jespdj on 2009-02-19
Note that it's Ubuntu **8.10**, not 8.1.

The version number reflects the year and month it was released: 8 = 2008, 10 = October.

---

### Post by wewee on 2009-02-20
these guides didn't help at all :s
i selected manual for partitioning
when i have to choose partitions i figured out how to select swap partition but i still don't know how to configure the partition i am willing to use for linux 
and i mean "use as" and "mount point"
i never used windows before therefore i don't know what to choose
please guide me through it
i need to know how to setup the partition , wich FS and wich mount point and if there's anything i should do to the main partition where windows xp is installed
remember that i am dual booting

---

### Post by wewee on 2009-02-20
after many researches i have chosen mount pont "/" and ext3 journalist file system
hope i am doing everything ok :p
and by the way the way they display partitions is very annoying
i had to guess every partition i have by its size in MB because they don't name them the same as windows does "C D E F...."

---

### Post by wewee on 2009-02-20
windows is not loading anymore
<windows root>\system32\hal.dll missing file

---

### Post by stchman on 2009-02-20
> **wewee said:**
> hello , i have installed win xp on my dv5t laptop 
now i ant to install ubuntu as dual boot , i already downloaded 8.1 64 bit version 
can i find any guides on how to do it ??
i have a 24 GB free partition just for ubuntu i also have a 5 gb free partition for SWAP ( i made them that way when i formatted)
note that i never used linux before , i am a windows person 
but i have read some reviews and partitionned my hard disk this way coz i knew i was going to install linux sooner or later 
i don't wanna use wubi , i have the ubuntu disc i downloaded last week , i only need step by step instructions to a full installation while being able to choose wich OS on startup
thank you

I recommend you simply take those partitions (24GB and 5GB) and combine them to make one big free space partition (29GB).  There is no reason to have a 5GB SWAP partition.  My SWAP is maybe 1.5GB.  I also recommend you have at least 2GB RAM.

When installing Ubuntu their is an option to use the largest continuous free space.  Select that and the installer will create the file system and SWAP space in that partition.

Easy.

---

### Post by wewee on 2009-02-20
my installation is done
but windows xp is not loading anymore :s 
by the way  i have a 150 gb partition , most of it is free , if i choose what u mentioned i think the installer will chose that partition wich i like to keep intact
i am doing a recovery for xp from the cd

---

### Post by Mugzilla on 2009-02-20
> **wewee said:**
> these guides didn't help at all :s
i selected manual for partitioning
when i have to choose partitions i figured out how to select swap partition but i still don't know how to configure the partition i am willing to use for linux 
and i mean "use as" and "mount point"
i never used windows before therefore i don't know what to choose
please guide me through it
i need to know how to setup the partition , wich FS and wich mount point and if there's anything i should do to the main partition where windows xp is installed
remember that i am dual booting

I have a question for clarification:

When you went to install 8.10, and got to step 4, what partitioning options did it give you?  It should give you THREE.  It sounds like you are only getting TWO (Manually edit partition table and FULL Disk.)

You should have the option to resize a partition under the MANUAL option.

Do you have this option?

The reason I ask is, I had the same problem a week ago. I wanted to dual boot, but the option to resize did not show up.  My solution was to get rid of windows.  To my delight, I found out my verizon air card is plug and play in 8.10, so no more need for windows!

---

### Post by wewee on 2009-02-20
> **Mugzilla said:**
> I have a question for clarification:

When you went to install 8.10, and got to step 4, what partitioning options did it give you?  It should give you THREE.  It sounds like you are only getting TWO (Manually edit partition table and FULL Disk.)

You should have the option to resize a partition under the MANUAL option.

Do you have this option?

The reason I ask is, I had the same problem a week ago. I wanted to dual boot, but the option to resize did not show up.  My solution was to get rid of windows.  To my delight, I found out my verizon air card is plug and play in 8.10, so no more need for windows!

i don't remember any resizing option......
anyway i still need windows , cz i game a lot and most of the softwares i use don't work except for windows

---

### Post by Wolfhere on 2009-02-20
If you are just finding your way with Ubuntu, try the Wubi install first (I think the largest 'partition' is 30gig). That way, if you do not like it, you just have to do the add/remove programs. I started that way. When I was comfortable, I installed to the separate partition (after removing wubi). Once I found the answers to my sync for windows mobile pda and my favorite games, I replaced my Vista drive, partitioned for /, /home and swap and installed. I only use the Windows drive now for taxes and Ut3 (and I am not very good at that). I guess the point I am making is, since you are a windows person like I was, step into it like I did. 

The only decisions you would have to make is, if you are working off one drive and windows is 32 bit...do the 32 bit wubi install. Then by the time you are ready for a full install to the separate partition, you can use the next full supported release (9.04). 8.10 only has support for 18 months, and long term support (LTS) versions for 3 years. The whole scoop on Ubuntu can be found here: [http://www.ubuntu.com/products/whatisubuntu](http://www.ubuntu.com/products/whatisubuntu)

---

### Post by oli1997 on 2009-02-21
hi guys i was thinking that i could install ubuntu 8.10 64bit, but i was wondering what specs it needed mines not 64bit spec but i thought it might work since ubuntu isnt a big base like windows.


intell p4 336 2.8Ghz
1gb ram (might be upgraded to 2gb)*


*i thought 64bit was 3.5gb to what ever it is.

---

### Post by FXEF on 2009-02-21
> **oli1997 said:**
> hi guys i was thinking that i could install ubuntu 8.10 64bit, but i was wondering what specs it needed mines not 64bit spec but i thought it might work since ubuntu isnt a big base like windows.


intell p4 336 2.8Ghz
1gb ram (might be upgraded to 2gb)*


*i thought 64bit was 3.5gb to what ever it is.

If you do not have 64 bit hardware (CPU) then Ubuntu 8.10 64 bit will not install. You need to use 32 bit Ubuntu 8.10.

---

### Post by oli1997 on 2009-02-22
oh! never mind ill live lol:D

---

