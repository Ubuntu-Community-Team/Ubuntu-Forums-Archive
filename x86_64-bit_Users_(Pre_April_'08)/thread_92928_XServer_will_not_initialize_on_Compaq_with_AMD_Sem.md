---
title: "XServer will not initialize on Compaq with AMD Sempron"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by CaKiwi on 2005-11-20
I have installed 5.10 on a second disk on Compaq presario

Processor Family: AMD Sempron
Installed RAM: 512 MB
Hard Drive Capacity: 160 GB
RAID: No
Graphics Card: ATI Radeon XPRESS 200 

It gets an error saying it could not initialize the XServer and comes up in command mode. 

TIA

CaKiwi

---

### Post by RAOF on 2005-11-20
Ok.  When you were configuring the X server, what driver did you choose?  Ati?  You should be able to get into a (slow) X server by running "sudo dpkg-reconfigure xserver-xorg" and selecting the "vesa" driver when asked.  Once that works, you might want to try installing the fglrx ati drivers.  They may work better for you.

But first, get a working X with the vesa drivers.  Everything's easier from X :)

---

### Post by CaKiwi on 2005-11-20
Thanks for the speedy response. 

I just did a standard installation and I was not asked about the X server or drivers so I presume I got defaults. I will try your suggestion and let you know what happens.

Thanks again

CaKiwi

---

### Post by CaKiwi on 2005-11-20
RAOF,

I tried the command you suggested but it asks me for the root password. The only password I created during the installation was for my user. How do I know what the root password is?

Also, after I set the driver, how do i start the X server for the command line?

Thanks again.

---

### Post by RAOF on 2005-11-20
It's not actually asking for the root password, it's asking for your password.  The first user gets added to the admin group.  One of the privileges of the admin group is that they can use sudo.  Just type **your** password.

And then, to start X, run "sudo /etc/init.d/gdm restart" (This assumes you installed Ubuntu, not Kubuntu.  If you installed Kubuntu, it would be sudo /etc/init.d/kdm restart, I think)

---

### Post by CaKiwi on 2005-11-20
Oh, sorry. I'll try that.

Thanks again.

---

### Post by CaKiwi on 2005-11-20
Worked great! Thanks. I am now using Firefox on Ubuntu to post this. (I had to go back to the dark side for the previous posts). I may play other drivers later.

Have a virtual beer on me.

---

