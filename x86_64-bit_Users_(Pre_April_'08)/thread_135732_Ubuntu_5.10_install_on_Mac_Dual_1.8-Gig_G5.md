---
title: "Ubuntu 5.10 install on Mac Dual 1.8-Gig G5"
date: 2006-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by schroeders on 2006-02-24
I'm trying to install 5.10 on a Dual 1.8 G5 from a CD I burned from an ISO file. I have two hard drives installed and want Linux on the one that doesn't contain my Mac 10.4.5 OS The installation proceeds normally, I let the partitioner format the whole second (250 Gig) drive (also tried having it use the largest free space), which it does. It continues the install to the point where it ejects the CD and says to hit Return to boot from the newly installed Linux OS. When I do so it boots back into OS X. When I reboot holding the Option key down, I get the screen giving me a choice between the existing OSs. I choose the Linux one, hit the proceed arrow and am taken to a command line page telling me to press "x" for OS X or "l" for Linux (and some other choice). When I press the "l" key I get taken back to to the previous "choice" page that I got when booting with the Option key down. 

As might be obvious, I'm new at this. I would appreciate any suggestions

---

### Post by oswaldkelso on 2006-02-24
I'd just reinstall.
It should give you the  l  x c options on reboot, not boot into osx.
Only if you've set the start up disc in the (osx) start up prefs should you have to hold the alt key to get choices and then linux.(or reset it with the Command line interface).
Is your linux hard drive set to slave? perhaps the jumpers need checking.  My 2nd hd on my g4 is linux and its set to cable select not slave.

---

### Post by schroeders on 2006-02-24
The G5 uses a serial ATA bus for internal drives and there are no jumpers to set on the drives. They might be slot-dependent, though. I just installed the new drive into the lower slot. Might have to try swapping them. I have reinstalled Ubuntu several times using different choices for the partitioning to be done by the installer. Tried manual control of the partitioner, too, with bad results. 
The OS X startup disk has to be set to something and since it doesn't see the Linux volume, its default is OS X. From the Ubuntu Installation Manual it seems that when the install CD is ejected and one hits the Enter key, it sould jump right into booting from the newly installed Linux, but it doesn't. It just reboots into OS X unless the Option key is held down -

---

