---
title: "Using external HDD"
date: 2009-04-05
forum: x86 64-bit Users
---

### Post by andjen on 2009-04-05
I've got a dual boot system with Vista and Hardy on a 64-bit system. My problem is that I can't do anything with my Lacie external disk drive.

If I've been in Vista then I make sure that I 'Safely Remove' the disk before booting into Ubuntu. The disk is recognised and automounted at first but as soon as I try and access anything then the external disk disappears from view and I can no longer access it from Ubuntu.

I've even tried becoming root (with 'sudo -i') before trying to get at the drive so that I've got full permissions but that doesn't work either.

I've got loads of data on that disc and I don't want to have to go back into Vista every time I want to access it!

What am I doing wrong (or not doing)?

---

### Post by zigga15 on 2009-04-05
This could be happening for a number of reasons.

First of all Vista sucks. There is a very high probability that the problem stems from there.

Now I have that off my chest, you should try this:

sudo su
ls /dev/disk/by-label/
echo this will spit out all the disks connected to it
mount /dev/disk/whatever you drive is called

Hope this helps!

~ Dan

---

### Post by andjen on 2009-04-05
Thanks for your quick reply zigga15.

I did as you requested with the folowing results :

'sudo su" gets me to be root but then 'ls /dev/disk/by-label/' gives the following message 'ls: cannot access /dev/disk/by-label/: No such file or directory'

What's next (I'm relatively new to Ubuntu but thought I'd better post in this forum because I've got a 64 bit system)?

---

### Post by zigga15 on 2009-04-05
> **andjen said:**
> Thanks for your quick reply zigga15.

I did as you requested with the folowing results :

'sudo su" gets me to be root but then 'ls /dev/disk/by-label/' gives the following message 'ls: cannot access /dev/disk/by-label/: No such file or directory'

What's next (I'm relatively new to Ubuntu but thought I'd better post in this forum because I've got a 64 bit system)?

basically we want to find the name of the device and mount it. in dev/disk you should find something to do with your device

cd /dev/disk
ls
mount device-name

keep looking around in /dev/ and /dev/disk until you find something that resembles the disk, there shouldn't be that much stuff in there.
64 bit won't make much difference here I don't think.

---

### Post by andjen on 2009-04-05
Sorry but I can't find anything in /dev/ or /dev/disk that relates to my external Lacie drive. The only place that I can find it is in /media but I can't open the folder "because I don't have the necessary permissions" and it has got an "unreadable" emblem next to it.

---

### Post by zigga15 on 2009-04-05
ohh ha ha...

sudo chmod -R 555 /Media/Lacie(or wateva)

If that doesnt work:

sudo chmod -R 777 /Media/Lacie(or wateva)

usually not a good idea though, the drive must be locked or something... If you can't sudo ls it then change the permissions forcibly 

~ Dan

---

### Post by andjen on 2009-04-05
> **zigga15 said:**
> ohh ha ha...

sudo chmod -R 555 /Media/Lacie(or wateva)

If that doesnt work:

sudo chmod -R 777 /Media/Lacie(or wateva)

usually not a good idea though, the drive must be locked or something... If you can't sudo ls it then change the permissions forcibly 

~ Dan

The response to both of those commands is

"chmod: cannot access `/Media/Lacie': No such file or directory"

although I can see a Lacie folder inside Media!

Sorry but I'm not sure what you mean by "change the permissions forcibly".

Andrew

---

