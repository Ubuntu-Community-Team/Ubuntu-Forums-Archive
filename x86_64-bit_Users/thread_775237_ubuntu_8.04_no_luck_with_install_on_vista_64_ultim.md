---
title: "ubuntu 8.04 no luck with install on vista 64 ultimate with raid 0"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by j_l_larson on 2008-04-29
Hi,

I've been trying to get ubuntu to co-exist with Vista on my machine for some time now.  I just tried the new 8.04 release today and still can't get it to work.

I'm trying to get Ubuntu to boot off of an external hard disk attached via USB.  I want to run the 64 bit version of Ubuntu.

My machine is an HP Pavillion m9080.  Intel Core Q6600, 8GB ram, 64 bit os (Vista Ultimate).  The video card is Nvidia GeForce 8800 GTS.  It has Raid 0 installed as it's only hard disk.  I've added a 120 GB hard disk on USB and changed the boot order in the bios so that the USB drive boots first before the raid 0 does so that ideally I could optionally boot Linux instead of Vista.

Basically, I do not want to disturb the existing Vista installation on the machine.  I know a lot of people here don't understand that sentiment, but I have put a lot of hours into getting things set up there and I don't want to start over.

I've taken photos of the installation step by step and put them on flickr so I could remember everything.

When I start the install, the first thing I get is an error message:  dmi_save_oem_strings_devices: out of memory
[http://www.flickr.com/photos/j_l_larson/2452899783](http://www.flickr.com/photos/j_l_larson/2452899783)

I chose the Safe Graphics Mode install:  
[http://www.flickr.com/photos/j_l_larson/2453724048/](http://www.flickr.com/photos/j_l_larson/2453724048/)

I chose USA/English all that standard stuff. 

When I get to the part about partitioning, I chose to use the guided partitioning on the external hard disk (see photo)
[http://www.flickr.com/photos/j_l_larson/2453736970/](http://www.flickr.com/photos/j_l_larson/2453736970/)

Then I get the ready to install window:
[http://www.flickr.com/photos/j_l_larson/2453738996](http://www.flickr.com/photos/j_l_larson/2453738996)
[http://www.flickr.com/photos/j_l_larson/2452912685](http://www.flickr.com/photos/j_l_larson/2452912685)


Then I chose the "Advanced Options" button and selected that the boot loader be installed on the external drive instead of hd0.  I did this because I am afraid of trashing my Vista partition.  This is the part I'm not too sure about.
[http://www.flickr.com/photos/j_l_larson/2453742614](http://www.flickr.com/photos/j_l_larson/2453742614)
[http://www.flickr.com/photos/j_l_larson/2453746258](http://www.flickr.com/photos/j_l_larson/2453746258)

So, then it starts installing:
[http://www.flickr.com/photos/j_l_larson/2452920757](http://www.flickr.com/photos/j_l_larson/2452920757)

Finally it finishes and has me reboot.  
[http://www.flickr.com/photos/j_l_larson/2452952461/](http://www.flickr.com/photos/j_l_larson/2452952461/)

The screen goes black after I hit the reboot button and I have to pull the power plug out.  
[http://www.flickr.com/photos/j_l_larson/2452956779/](http://www.flickr.com/photos/j_l_larson/2452956779/)

But then it starts up when I power up again.
[http://www.flickr.com/photos/j_l_larson/2453789500/](http://www.flickr.com/photos/j_l_larson/2453789500/)
[http://www.flickr.com/photos/j_l_larson/2453790790/](http://www.flickr.com/photos/j_l_larson/2453790790/)

But then when it reboots it says the disk does not exist:
(Grub loading please wait)
[http://www.flickr.com/photos/j_l_larson/2453794088/](http://www.flickr.com/photos/j_l_larson/2453794088/)
(Error 21: Selected disk does not exist)
[http://www.flickr.com/photos/j_l_larson/2453795244/](http://www.flickr.com/photos/j_l_larson/2453795244/)

Then I come to this menu with three options:
[http://www.flickr.com/photos/j_l_larson/2453796388/](http://www.flickr.com/photos/j_l_larson/2453796388/)
Ubuntu 8.04 kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, memtest86+
all of which give the same error 21, selected disk does not exist.

Drilling down on each of the menu options with the 'e' key doesn't help cause I don't know what to do with the information.

Please, thanks for any clues or advice
-Julie

---

### Post by ASULutzy on 2008-04-30
This isn't the most elegant solution, but it certainly won't hose your system up any more and is completely reversible.

You're probably just going to need to edit the device that it thinks Ubuntu is installed on. You could either boot off the live CD, and if it auto mounts the USB drive, then just click applications, accessories, terminal, then type ```
sudo fdisk -l
``` and paste the output here.

Alternatively, and very brute force ugly-ish, you could just push 'e' to drill down into that and keep guessing at it lol. How many hard drives do you have installed? If it's just your main one and the USB one you could probably guess it relatively quickly.

It's going to be /dev/(h or s)(d)(letter, if only two drives, usually a or b)(partition number, if you haven't repartitioned the USB drive probably 1 or maybe 2)

If it were me I'd just push 'e' at that menu and try changing it to /dev/sda1 and pushing 'b' to boot. If it doesn't work, just reboot and try /dev/sdb1/ or /dev/sda2 etc. This is the ugly solution, but it's probably about as quick as booting into the live cd and running fdisk -l

Hope this helps

edit: looking at your 1 screenshot, I'd say try changing whatever value is there to /dev/sdg1

---

### Post by j_l_larson on 2008-04-30
> **ASULutzy said:**
> 
If it were me I'd just push 'e' at that menu and try changing it 

You are a genius and it worked.  Thank you *so* super much.

I just pushed 'e' and changed it to read boot /hd0 and it worked!

many thanks!

:KS

---

### Post by j_l_larson on 2008-04-30
I would change the thread icon to a smiley face, but don't know how.  Thanks!

---

### Post by ASULutzy on 2008-04-30
Glad I could help, thanks for the thanks. Welcome to Ubuntu, hopefully it'll be smooth sailing from here on out!

---

