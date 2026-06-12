---
title: "gparted help"
date: 2009-03-25
forum: x86 64-bit Users
---

### Post by utnr6 on 2009-03-25
i just want a simple dual boot of ubuntu and windows and what i have is a mess
help me simplify this...i have a gparted live cd and SORTA know how it works

unallocated   1mb
/dev/sda1   ntfs  1.46gb
unallocated  5mb
/dev/sda2   ntfs (c:)  165gb  26gbused
/dev/sda3   extended    59gb
   /dev/sda6  ext 3  /   29.16gb  4.47gbused
   /dev/sda7  linux swap    1.3gb
   /dev/sda5  ext3  /media/disk  29.16gb  641mbused  ???
unallocated          6.58gb

please tell me what to do!!!

---

### Post by utnr6 on 2009-03-25
oh yea  iboot from (0,5) ext3 
windows doesnt go past starting up...

---

### Post by miegiel on 2009-03-25
> **utnr6 said:**
> windows doesnt go past starting up...

That's your problem? What does happen? Do you get a boot menu to choose windows at all?

Moving the 2 NTFS partitions to the start of the disk might help, maybe that messed up the grub installation.

ps When messing around with gParted it's a good idea to BACKUP all you don't want to risk loosing to a separate disk, CD, etc. There's always a risk of human error and power failure ;)

---

### Post by utnr6 on 2009-03-26
when i but grub 1.5 loads...

then i see the 2 different ubuntu installs and under other operating systems i see my vista/longhorn

if i choose vista/longhorn, it goes to the black "starting up..." screen and then stays there

my two ntfs at the top were placed there directly following my initial installation... they remained the same after i f-ed with gparted but now i have all that other nonsense

what i really want to know is what to resize/move/or delete

---

### Post by miegiel on 2009-03-26
Have you changed your partitions a lot? Like delete or add partitions in front of the windows partition.

It looks like the windows boot loader can't find the windows partition anymore. After choosing "other operating systems" in grub, grub quits and hands the boot over to the vista boot loader. You probably need to rearrange the partitions so that the vista boot loader can find the partition. Or you need to edit the boot.ini to point the vista bootloader in the right direction.

Open the boot.ini in a text editor to see where the bootloader expects vista to be. It's probably hidden in the root of one of your NTFS partitions.

---

### Post by utnr6 on 2009-03-26
I used the partition editor live disc one time and then this mess arose so yea, you are right....
i'll give the boot.ini thing a shot, sounds like it'll help.  I'll let u know what happens

thanks so much for the responses

also, i've goodled and googled and can't seem to find gparted examples of good setups... is there a proper order for rearranging this stuff and if so what is it?  I'm sure the answer is personal preference but I'm easy and I just want to use grub, and have windows and ubuntu both work.

---

### Post by miegiel on 2009-03-26
> **utnr6 said:**
> also, i've goodled and googled and can't seem to find gparted examples of good setups... is there a proper order for rearranging this stuff and if so what is it?  I'm sure the answer is personal preference but I'm easy and I just want to use grub, and have windows and ubuntu both work.

Depends on what you want really, but there are some best practices. Like keeping windows on 1 partition at the beginning of the disk and putting the ubuntu partitions behind it.

I've made a quintuple boot, but only 3 of the 5 work. for inspiration here's my fdisk -l. The first 3 are for different windowses about 50GB each. In the extended there are 2 linux partitions of 20GB with a shared swap and home partition.

```
:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eb39a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       12748    51199155    7  HPFS/NTFS
/dev/sda3           12749       19122    51199155    7  HPFS/NTFS
/dev/sda4           19123       60801   334786567+   5  Extended
/dev/sda5           19123       21672    20482843+  83  Linux
/dev/sda6           21673       22194     4192933+  82  Linux swap / Solaris
/dev/sda7           22195       24744    20482843+  83  Linux
/dev/sda8           24745       60801   289627821   83  Linux
```

---

### Post by utnr6 on 2009-03-26
ok, more research and I think that my ubuntu install erased my boot.ini file... i can mount my vista drive and view all of my files and boot stuff but boot.ini is nowhere to be found. 
my sudo fdisk thing doesnt look too bad

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b78f3f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         193       21756   173212830    7  HPFS/NTFS
/dev/sda3           21757       29542    62541045    5  Extended
/dev/sda5           25733       29542    30603793+  83  Linux
/dev/sda6           21757       25562    30571632   83  Linux
/dev/sda7           25563       25732     1365493+  82  Linux swap / Solaris

gparted shows the following:
unallocated                              1.00 MiB
/dev/sda1   -!-   ntfs                   1.46 GiB
unallocated                              5.09 MiB
/dev/sda2         ntfs   /media/SQ###  165.19 GiB  (vista)   boot
/dev/sda3         extended              59.64 GiB         
    /dev/sda6     ext3   /              29.16 GiB  (5.57G)
    /dev/sda7     linux-swap             1.30 GiB 
    /dev/sda5     ext3                  29.19 GiB  (641MB)
unallocated                              6.58 GiB

  ok, i believe when I did my gparted, i created a new ext3, which i think is my current sda5 that is 641MB that probably has my windows boot.ini file.
  under ubuntu places, computer, this drive appears as {31.3GB Media} and has one folder called lost and found which i cannot open (root permissions)

I have a toshiba satellite and my /dev/sda1 is labeled TOSHIBA SYSTEM VOLUME... its folders are $RECYCLE.BIN,  SOURCES, SYSTEM INFORMATION,then it has the files BOOT.SDI and WinREPartition.ini

the final unallocated is what I thought I created as a logical partition to be linux-swap, don't think that is what it became though

You have already done so much so if you are irritated don't respond, ill continue to research... What I'm thinking a solution could be is just to move the Lost and Found folder from my 2nd ext3 place into my SQ#### vista folder, then just delete that partition as well as the unallocated.  Hopefully from there I can edit my boot.ini.  

1 final thing,maybe I am missing some very elementary information on this whole volume thing, but what is the importance of my 1.46Gb toshiba system volume... is it basically vista's version of grub?

and finally, i have important school folders and anything else i need backed up on other discs so none of my information is really valuable, i'd just like to fix this instead of risking the chance of wasting a bunch of time re-doing it all and ending up in the same place. anyway, you've done more than enough so feel free to ignore me if i've outworn my welcome.

---

### Post by miegiel on 2009-03-26
Hmmm ... maybe you should look into if vista still uses the boot.ini file. Though it has been part of the windows boot loader since NT4, they have changed some stuff in vista. To bad my vista's aren't working, so I can't go check :) The boot.ini is by default a hidden file though, you need to look good (turn "show hidden files" on in the file browser).

A quick and dirty way to get things running again is to restore windows and make some room on you disk and then reinstall ubuntu.

---

