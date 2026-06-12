---
title: "Weird behavior on Athlon 64 3200 + ATI x1600"
date: 2006-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by dahaka on 2006-10-05
Hi folks

I've used gentoo for months but I decided to move to Ubuntu. (with the same PC, everything working nicely)

I had problems to install the amd64 version using the desktop live cd, so I gave a chance to the alternate version and it worked. However, after the system boot I can't start X and there are some strange errors even on the console interface (while I try to fix the X problem). 

About the X error, I've already installed the fglrx driver and the xserver, but after the gdm login nothing appears on the screen and about 15 seconds later the pc freezes. 

While I'm trying to change xorg.conf, for example, using the console, there are some programs that return segmentation fault (ls, less (when I was reading logs...), vim ) and sometimes error messages appear (it seems to be from the kernel). 

Examples of error messages:
BUG: soft lockup detected on CPU#0!
Kernel panic: Aiee, killing interrupt handler
Kernel oops

Sometimes another messages are shown but I can continue using the console. Ahh, another strange thing is that the PC beeper produces sound with some of the messages. 

My PC is an Athlon 64 3200 , video card ATI x1600 pro 512mb , HDD SATA Samsung 250 GB, motherboard Asus A8V-E SE

These errors happened with: Dapper amd64 & 32bits , Edgy beta release amd64 & 32bits 

So, does anybody have any idea about how to solve it? thanks

---

### Post by pay on 2006-10-05
I'm not sure if the alternate install installs gnome or not, but if it doesn't just install it```
sudo aptitude update
sudo aptitude install ubuntu-desktop #you can add an x or a k infront of ubuntu to choice either kde or xfce
```

EDIT: sorry you must already have gnome installed since your getting the gdm.I jumped the gun:)

Here's someone with the segmentation fault that you were getting. Maybe you can use their solution:confused:
[http://www.ubuntuforums.org/showthread.php?t=271640](http://www.ubuntuforums.org/showthread.php?t=271640)

---

### Post by dahaka on 2006-10-05
Thank you for answering.

I took a look at the link you've sent, I'll try tonight, I'm at work now. 

I'll check if it solves the apt problem, then I post here the changes

---

### Post by dahaka on 2006-10-06
The apt error has gone. Unfortunately the kernel ooops, aiee, etc continue. I booted on the "single user mode" and then the system works fine. I used it to configure the ATI driver stuff, turn off acpi, apt-get update... When I tried to boot again, the same erros appeared, the PC has frozen again, etc etc etc... 

I attempted to compile the kernel (almost without hope), then a curious message has been shown (I don't remember the exact words): "You processor can't support 64 bits" or stuff like that!?!??! How???

It's funny, I have a pc in which is easier to install gentoo than ubuntu!

---

### Post by patrickfromspain on 2006-10-06
couldn't it be a faulty ccd? Did you check md5sum?

---

### Post by dahaka on 2006-10-07
> **patrickfromspain said:**
> couldn't it be a faulty ccd? Did you check md5sum?

It has been checked...

---

