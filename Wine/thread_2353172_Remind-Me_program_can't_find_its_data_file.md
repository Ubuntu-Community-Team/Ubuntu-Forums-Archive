---
title: "Remind-Me program can't find its data file"
date: 2017-02-19
forum: Wine
---

### Post by steve169 on 2017-02-19
I run both Windows 7 and Ubuntu 16.04 on my desktop PC.

WINE is installed in Ubuntu and is working.

I run an appointment calendar program in Windows called Remind-Me.

I've also installed Remind-Me in WINE, and it boots fine.

**My goal is to be able to display _and edit_ Remind-Me in both Windows and WINE.**

To do this, I must specify in the WINE start-up command line the location of the Remind-Me data file, which in Windows is:[INDENT][B] 
"C:\Users\Stevie\Application Data\Remind-Me\mydata.bdy"[/B]
[/INDENT]

WINE has installed two icons on my Ubuntu desktop: "Remind-Me" and "Remind-Me.lnk."

In the "Remind-Me" icon I have gone to Properties and added the data file location to the command line thus:

[INDENT]env WINEPREFIX="/home/stevie/.wine" wine C:\\Program\ Files\ \(x86\)\\Remind-Me\\RemindMe.exe **"/media/C:\\Users\\Stevie\\Application\ Data\\Roaming\\Remind-Me\\mydata.bdy"**
[/INDENT]
 
Remind-Me boots but does not display the data from the data file.

**Have I entered the data file location in the wrong format?**

---

### Post by uNoubu8a on 2017-02-20
Yes, I believe your path to the windows files to be completely wrong.

First we have to ensure that the disk or partition with the Windows files are being mounted.  Could you give the output of ***ls /media/$USER/*** from a terminal (I hope that is the correct command, sucks when there is no Linux machine nearby)...

---

### Post by steve169 on 2017-02-21
The*** ls /media/$USER*** command brought nothing up, only the usual prompt, which in my system is ***stevie@microsteve:~$***

I've already set ***fstab*** to mount all my hard drives at boot-up. Windows and Ubuntu are on the same hard drive but in different partitions.

---

### Post by uNoubu8a on 2017-02-21
> **steve169 said:**
> The*** ls /media/$USER*** command brought nothing up, only the usual prompt, which in my system is ***stevie@microsteve:~$***

I've already set ***fstab*** to mount all my hard drives at boot-up. Windows and Ubuntu are on the same hard drive but in different partitions.

What is the path to your Windows partition as it isn't showing up under /media ?  I assume you can access the parition from a file manager etc?  You say you set up fstab to mount automatically, where are you mounting the Windows partition?

---

### Post by steve169 on 2017-02-22
Dear Work-Work:

Re your message "What is the path to your Windows partition as it isn't showing up under  /media ?  I assume you can access the parition from a file manager etc?   You say you set up fstab to mount automatically, where are you mounting  the Windows partition?"

1.   At start-up Grub 2 gives me the choice of booting either Ubuntu (the default) or Windows 7.

2.  I have 3 hard drives; one is solid state. Here are the contents of each drive:
[INDENT][B]Drive 1 (SSD)
[/B][/INDENT]
[INDENT=2]_Partition 1_: formatted *NTSF* and contains the Windows 7 operating system (Drive C).

_Partition 2_: formatted *ext4* and contains the Ubuntu 16.04 installation. It is encrypted.

_Partition 3_:  formatted *linux swap* and contains Ubuntu swap files. It is encrypted.

_Partition 4_: formatted *NTSF* and contains Windows data files and a few Ubuntu data files (Drive E).
[/INDENT]
[INDENT][B]Drive 2 (standard hard drive)
[/B][/INDENT]
[INDENT=2]_Partition 1_: formatted *NTSF* and contains Windows data files (Drive G).
[/INDENT]
[INDENT][B]Drive 3 (standard hard drive)
[/B][/INDENT]
[INDENT=2]_Partition 1_: formatted *NTSF* and contains Windows data files (Drive F).
[/INDENT]
[INDENT]

[/INDENT]
3.  Here are the contents of my fstab file:

[INDENT]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=ef7d3f98-eca1-430e-9cd8-5dc8d3448c6d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3ca1f0c9-12fc-4063-8a89-507dcb429685 none            swap    sw              0       0
# mount C
UUID=0CE2B73AE2B7273C    /media/C    ntfs    auto    0    0
# mount E
UUID=58BCDBEEBCDBC4A2    /media/E    ntfs    auto    0    0
# mount F
UUID=2ADBE8A42FE77935    /media/F    ntfs    auto    0    0
# mount G
UUID=34B6CF29B6CEEA86    /media/G    ntfs    auto    0    0
[/INDENT]

---

### Post by uNoubu8a on 2017-02-22
Ok, so if you do ls /media you see all the drives C through E?

---

### Post by steve169 on 2017-02-22
Re your message: [I]Ok, so if you do ls /media you see all the drives C through E?
[/I]
Yes. Running ***ls /media*** shows drives ***C:, E:, F:*** ***and*** ***G:*** plus any thumb drive I might have plugged in. It also shows ***stevie***, which is my user name in Ubuntu.

---

### Post by uNoubu8a on 2017-02-23
OK, the format you use here:

> In the "Remind-Me" icon I have gone to Properties and added the data file location to the command line thus:

env WINEPREFIX="/home/stevie/.wine" wine C:\\Program\ Files\ \(x86\)\\Remind-Me\\RemindMe.exe "/media/C:\\Users\\Stevie\\Application\ Data\\Roaming\\Remind-Me\\mydata.bdy"


I am unsure about all of the "\\" in use.  In my opinion you can try changing **"/media/C:\\Users\\Stevie\\Application\ Data\\Roaming\\Remind-Me\\mydata.bdy"** to ***"/media/C/Users/Stevie/Application/Data/Roaming/Remind-Me/mydata.bdy"***

*(PS - To check the path open /media/C in Nautilus (File Browser) and follow the path to the mydata.bdy file, hit Ctrl+L and copy the path from Nautilus...)*

---

### Post by steve169 on 2017-02-25
Dear work-work,

I tried your recommended command line and lots of variants, but nothing worked. Probably this application just won't function in WINE, so I'm throwing in the towel and going to a different application. Many thanks for your efforts.

---

### Post by uNoubu8a on 2017-02-26
> **steve169 said:**
> Dear work-work,

I tried your recommended command line and lots of variants, but nothing worked. Probably this application just won't function in WINE, so I'm throwing in the towel and going to a different application. Many thanks for your efforts.

:( I am sorry was not of more assistance.

---

