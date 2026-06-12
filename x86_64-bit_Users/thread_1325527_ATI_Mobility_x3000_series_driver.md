---
title: "ATI Mobility x3000 series driver"
date: 2009-11-13
forum: x86 64-bit Users
---

### Post by natrobius on 2009-11-13
Hi, and thanks in advance for any posts in response to this question.

I am running Ubuntu 9.10 (x86_64) on a HP Pavillion DV5-1004nr. I have been looking for a accelerated video driver for the integrated Mobility Radeon x3000 series card in this laptop for a while.

Steps I've taken:

[LIST=1]
[*]Installed the ATI proprietary driver.
Notes: Even though ATI does not claim their driver supports this integrated chipset, I wanted to try it out to see if the card was similar enough to be supported. I installed through the Ubuntu package manager, and manually (downloaded from the ATI website) both resulted in getting a solid black screen upon bootup.
[*]Installed the open source driver.
Notes: This seemed a little pointless, as there is still no 3d support. It is worth noting, that I installed the open source driver on LinuxMint, not on pure Ubuntu. This ended much the same way the proprietary driver did, with a black screen.
[/LIST]
If anyone here can offer me help in getting 3d running on this system, I would be very grateful, as this is my primary work rig, and I program OpenGL software for Linux.

Again, thanks in advance.
Nathan.

---

### Post by BramWillemsen on 2009-11-13
That's really strange... I installed the binary drivers from ATI's website on my 64 bit ubuntu 9.10. It works really good on my mobility HD3200. Which card do you have? (i'm quite a linux noob so i probably won't have answers for you, just wanted to tell it is possible)

edit: my laptop is also a HP, 6735s though

---

### Post by natrobius on 2009-11-13
It seems that we are supposedly running the same card. On CNet it is listed as:

> ATI Radeon HD 3200 Shared video memory (UMA)

Could you post where you found installation instructions, or any special steps you had to take to make it work? Maybe I'm just missing something.

---

### Post by BramWillemsen on 2009-11-13
Did you make a clean 9.10 install? I did. First I made sure no open source drivers were installed (look in synaptic, search for ati). In my case there were no drivers installed when 9.10 was installed. I then just downloaded the binary drivers from the ATI website. The archive you download contains a pdf that you most likely read. Execute the binary file with root permissions (sudo) and follow the instructions in the PDF. During the installation the program will ask you whether you want it to change the xorg.conf file (contains information for X which settings to use I think). I let the installation program edit the xorg.conf file, rebooting and everything worked for me.

Maybe something got messed up on your system. The PDF file that comes with the ATI archive also contains instructions for uninstalling. Maybe you should uninstall first, reboot, then try using the PDF as guide to install the binary drivers.

I am probably stating the obvious to you, but maybe it helps :)

---

### Post by natrobius on 2009-11-13
I haven't modified this copy of Ubuntu yet, but I'll check synaptic first. I'll post back my results.

---

### Post by rp3 on 2009-11-13
> **natrobius said:**
> It seems that we are supposedly running the same card. On CNet it is listed as:



Could you post where you found installation instructions, or any special steps you had to take to make it work? Maybe I'm just missing something.

I have a Mobility Radeon HD 3650 in my Toshiba and if I enable the restricted drivers I get a kernel panic at boot up... I guess I am in the same boat for now.  Will give it a while before I try again, as I wasn't able to figure out how to 'remove' it to get my machine to boot again :)..

Chow..

---

### Post by natrobius on 2009-11-13
Ok. So I installed the driver. Linux is beautiful now, all the eye candy works..... One problem... My Atheros internal wireless has quit working. It finds the networks within range, but even with the correct network key, will not connect. This connection was working immediately before installing the driver. Any ideas?

---

### Post by BramWillemsen on 2009-11-13
not sure about that one :) but im glad you got your 3d stuff working. Maybe you can make a new thread about your wireless.

---

