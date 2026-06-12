---
title: "SimpleTech 160gb external hdd."
date: 2008-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Koolgecko91 on 2008-03-27
When I plug it in it can not mount. Any way I can get it to work?

---

### Post by shane2peru on 2008-03-28
We are going to need a few more details.  Did you buy this hdd like this?  Did you buy the case and put the hdd in the case yourself?  Does it have an external power source?  Is it plugged in and turned on if it does have an external power source?  Does the light come on?  If not, does the hdd spin when plugged in?  Perhaps the jumpers are not set correctly?  Is it NEW, or used?  

Shane

---

### Post by Koolgecko91 on 2008-03-28
> **shane2peru said:**
> We are going to need a few more details.  Did you buy this hdd like this?  Did you buy the case and put the hdd in the case yourself?  Does it have an external power source?  Is it plugged in and turned on if it does have an external power source?  Does the light come on?  If not, does the hdd spin when plugged in?  Perhaps the jumpers are not set correctly?  Is it NEW, or used?  

Shane

Ok...Its a HDD that i borrowed. Its a standalone HDD. Its a travel one cause it has a stability system so it can be moved when spun up. It has an external power source but you dont need it. The lights come on and it try to mount but it cant. Its used cause its my friends. All my media,docs,and stuff are on it from when i made the switch. I went to Restricted Drivers when its plugged in and it didnt pop up on and says unable to mount.

---

### Post by shane2peru on 2008-03-28
> **Koolgecko91 said:**
> Ok...Its a HDD that i borrowed. Its a standalone HDD. Its a travel one cause it has a stability system so it can be moved when spun up. It has an external power source but you dont need it. The lights come on and it try to mount but it cant. Its used cause its my friends. All my media,docs,and stuff are on it from when i made the switch. I went to Restricted Drivers when its plugged in and it didnt pop up on and says unable to mount.

Ok, now we are cooking with gas.  Is it already formatted?  What is it formatted with?  If it isn't FAT32 (which it probably isn't) you are going to probably need to install ntfs-3g.  My guess, and it is only a guess is that it is probably formatted in NTFS (windows latest format with XP) and therefore you can't access it.  I don't know if Gutsy comes ready to read and write to NTFS, so if anyone can comment on that, that would be great.  I don't use NTFS at all, so I really have no idea if it works out of the box.  Try installing that app, if it is formatted in NTFS you should be all set after that.  If not post back letting us know what it is formatted with and what version of Ubuntu you are running.  

Shane

---

### Post by Koolgecko91 on 2008-03-28
How do I install it?

---

### Post by shane2peru on 2008-03-28
> **Koolgecko91 said:**
> How do I install it?

**System -> Administration -> Synaptic** then search for ntfs-3g.  Then click on install.

Shane

---

### Post by Koolgecko91 on 2008-03-29
It didnt work.

---

### Post by shane2peru on 2008-03-29
The install didn't work?  or the hdd still doesn't get mounted?  I still have a few more tricks up my sleeve.  Can you ask your friend what the hdd is formatted as?  Does he use Windows?  Or plug the hdd in and then open **Applications -> Accessories -> Terminal**  in the terminal paste this:

```

lsusb

```
(that will list everything that is  connected to the usb ports)
and then this:

```

sudo fdisk -l

```
(that will list all your hdd and the format they have)

Post the results of those two commands and we will go from there.

Shane

---

### Post by Koolgecko91 on 2008-03-29
lsusb
```

Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 4971:ce02  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000 

```

sudo fdisk -1
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7b1cd9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18753   150633441   83  Linux
/dev/sda2           18754       19457     5654880    5  Extended
/dev/sda5           18754       19457     5654848+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda41a35f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

```

---

### Post by shane2peru on 2008-03-29
> **Koolgecko91 said:**
> 

sudo fdisk -1
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7b1cd9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18753   150633441   83  Linux
/dev/sda2           18754       19457     5654880    5  Extended
/dev/sda5           18754       19457     5654848+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda41a35f

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sdb1               1       19457   156288321    7  HPFS/NTFS[/COLOR]

```
Ok, see the red above, that tells us that it is formatted as HPFS and or NTFS.  I know what NTFS is, but HPFS I had never heard of.   Here is a good link to learn a little about it:
[http://en.wikipedia.org/wiki/High_Performance_File_System](http://en.wikipedia.org/wiki/High_Performance_File_System)

Here is another link that bears bad news:
[http://stason.org/TULARC/os/linux-faq/029-Can-Linux-Access-OS-2-HPFS-Partitions.html](http://stason.org/TULARC/os/linux-faq/029-Can-Linux-Access-OS-2-HPFS-Partitions.html)

I don't know how old that info is, and I really have 0 experience with HPFS.  You can probably mount it and read the info from it, but it may be a little more difficult.  If it is NTFS here is a link for getting it to work:  [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs)  You will need to start at step 3 Auto Configuration (unless you want to do the manual configuration).  Honestly IMHO it isn't worth it to mess around with NTFS if you don't have to.  IF you must share the drive with a windows computer format it in FAT32 the only major limitation is you can't have really large file (I forget the exact number but I think it is something like over 2GB or something)  If you aren't using windows then, just format it as ext3.  Make sure your friend gets the data off first. :)  I don't have and don't know anything about HPFS so if it is indeed HPFS I don't think any advances have been made toward writing to that file system.  You will have to Google around and see about that.  NTFS can be mounted and written to, just depends on how dedicated you are to making it succeed.

Shane

---

### Post by Koolgecko91 on 2008-03-30
Still wont work but w/e. Im leaving Linux this week anyway.

---

### Post by avai on 2008-04-03
Currently, I find myself in a similar situation as Koolgecko91. My previous challenges with the simpletech external hd were with feisty, and now, I have gutsy.
The outputs for **lsusb** and **sudo fdisk -l** are as follows:

> 
lsusb:

Bus 003 Device 002: ID 4971:ce02  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000


sudo fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0779162

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3897    31302621   83  Linux
/dev/sda2            9403        9729     2626627+   5  Extended
/dev/sda3   *        3898        9402    44218912+  83  Linux
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris
/dev/sda6            9403        9566     1317267   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Lime"]/dev/sdb1               1       19457   156288321   83  Linux[/COLOR]


When I used feisty, I reformatted the external HD which results in the change in the fdisk -l output highlighted in green in the above code. Any assistance you could provide in completing the mounting process for the HD would be very much appreciated.

---

### Post by shane2peru on 2008-04-03
> **avai said:**
> Currently, I find myself in a similar situation as Koolgecko91. My previous challenges with the simpletech external hd were with feisty, and now, I have gutsy.
The outputs for **lsusb** and **sudo fdisk -l** are as follows:



When I used feisty, I reformatted the external HD which results in the change in the fdisk -l output highlighted in green in the above code. Any assistance you could provide in completing the mounting process for the HD would be very much appreciated.

Great!  Your's should be easy since it is formatted as Linux (barring any technical problems with SimpleTech drives).  I'm assuming then it doesn't auto mount?  Let's make sure your options are set right (which they should be)  go to **System -> Preferences -> Removable Drives and Media**  Click on the storage tab, and both boxes beside the 'mount' options should be checked.  If they are and it still doesn't mount then I'm assuming it is something to do with SimpleTech drives or Ubuntu not recognizing them correctly.  However we should still be able to mount it manually as follows:
In the terminal type:
```

sudo mkdir /media/SimpleTech

```
Now:
```

sudo mount /dev/sdb1 /media/SimpleTech

```

Now is should be mounted if you have any errors please post them back here.  Hope that does it for you.

Shane

---

### Post by avai on 2008-04-21
Sorry for the delayed response, I've been busy the past few weeks.

The output I received from the second command is:
> 
mount: you must specify the filesystem type


---

### Post by shane2peru on 2008-04-21
> **avai said:**
> Sorry for the delayed response, I've been busy the past few weeks.

The output I received from the second command is:

Ok, you need to put this:

```

sudo mount -t ext3 /dev/sdb1 /media/SimpleTech

```

That should fix the problem.  That is odd though because usually it 1.  Automounts and 2. usually picks up the type if it is not some odd type.  Let me know if that gives you any problems.

Shane

---

### Post by raynevandunem on 2008-07-13
Hi, just had a problem with mounting this drive when running the two sudo commands you posted:

```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/SimpleTech -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/SimpleTech ntfs-3g force 0 0

```

The problem is that I'm running Ubuntu as dual-boot alongside WinXP. Does that mean that I have to go back into WinXP, mount it and then unmount it in the "Safely Remove Hardware" manner, just to get Ubuntu to recognize it when I boot back into it?

EDIT: Nevermind. I did the above and it worked.

---

