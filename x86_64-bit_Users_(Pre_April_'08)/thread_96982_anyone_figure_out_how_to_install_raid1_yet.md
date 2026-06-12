---
title: "anyone figure out how to install raid1 yet?"
date: 2005-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryedawg on 2005-11-30
hi has anyone figured out the mysterious raid1 problem yet? I have two amd64 hard drives and am trying to install ubuntu 5.1 on them and everything is easy and straight forward in the wizard until i get to the raid1 install when im partitioning them. when i partition it sees both drives. then when i go to use raid1 it wont allow it? from what ive read everywher no-one has seem to be able to figure it out? helpppp me...

---

### Post by bonzodog on 2005-11-30
It seems h/w raid support is quite broken in Ubuntu. I know Ubuntu is supposed to handle software raid, and does raid 5 OK, but I know i'm unable to implement a RAID 0 set-up with Ubuntu.

---

### Post by ryedawg on 2005-12-02
haha, thats hilarious! I'm willing to play any cd's that will work for me right now....

anyways, i got it to work after alot of F#$% around....this is how it went....

downloaded the install ubuntu linux cd...
pooped er in the drive .....
setup begins.....
detects my hardware and when it gets to the part where you can choose how to partition the discs...


1. choose edit partitions manually
   *it shows my two hard drives so i delete all the content on them until it    shows free space

First Drive:

2. Create a partition..
   * Primary
   * 2.9 GB partition size
   * file type: EXT3
   * mount point:  /BOOT
    *Set Bootable Flag to: ON

3. Create another partition  
   *Logical
   *Remaining Space left GB partition size (for me it was 77.2 GB)
   *file type: Physical volume for raid
   
Second Drive:

2. Create a partition..
   * Logical
   * 2.9 GB partition size
   * file type: Swap Area
   * use as:  Swap

3. Create another partition  
   *Logical
   *Remaining Space left GB partition size (for me it was 77.2 GB)
   *file type: Physical volume for raid

----------------------------------------------

Now go to configure Raid Array

1. It will want to finish partitioning the drives before you begin hit continue
2. Configure raid array
3. Pick 0 or 1...i chose one as i wanted it to mirror
4. It should it will ask how many drives and default to 2...continue
5. And then 0 ....continue

then it will try to configure and probably kick up an error saying that there is no root file system defined....so go back into your main partition page and select the raid array you created and set its mount point to / (which is root)
....continue

and bobs your uncle...
works like a charm for me.... after finally figuring all this out it installed fine except i kept getting a horrible screen not configured properly error when it came to the desktop so i wasnt able to view it....after hours of playing around on that i figured out how to do it..........

ctrl + alt + f2     to get me to the command line

typed in

#sudo nano /etc/X11/xorg.conf
then changed nv to vesa
hit ctrl + o  to save it
hit ctrl +x to exit

#sudo startx       

to start up the xserver
or if it says its already started then ctrl + alt +f7 to get back to desktop

all this is from memory so sorry if i left a few bugs or confusion but now im off and running...except i am trying to install plesk 7.5 reloaded and realized that breezy badger isnt supported so now i have to erase everything start over and install version 5.04 the hoary hedgehog.......arg .....lol

---

### Post by countryboy on 2006-05-01
I am afraid that you have not actually implemented any form of RAID there.

On one physical disk you have your boot partition and a data partition, on the other you have a swap partition and a data partition.  All you are doing is mirroring the data partition - if one of your drives fail your system is busted.

If you lose Disk 1, your machine will not boot.

---

### Post by toadhall on 2006-05-14
How I setup Software RAID1

System Info
Two SATAII 250GB 7200RPM disks
2GB DDRII 400 RAM

Partition
Disk #1 
partition 1 - 20gb logical | change file system to physical raid volume
partition 2 - 6.9 gb - logical | change file system to physical raid volume
partition 3 - ~ 213gb (whatever is leftover) logical |change file system to physical raid volume

Disk #2 
Set it up exactly like Disk #1

Go to Configure RAID devices
Pick Configure new MD Device
Pick RAID1
Pick 2 devices
Pick 0 failover/additional devices
Choose the two corresponding parts (#5 in my case on both disks)

Do this for all three RAID1 devices

Scroll up and pick the first RAID1 device that you have created, and hit enter.

From there you can pick the file type and mount point.  

I setup mine up in the following manner:
RAID1 first partition on part #5 as ext3 with mount point of / (root)
RAID1 second partition on part #6 as swap
RAID1 third partition on part#7 as ext3 with mount point of /home (user folders)

---

