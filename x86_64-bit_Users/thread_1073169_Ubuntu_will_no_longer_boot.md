---
title: "Ubuntu will no longer boot"
date: 2009-02-18
forum: x86 64-bit Users
---

### Post by Moddington on 2009-02-18
Just today, after following the instructions found [here]("http://ubuntuforums.org/showthread.php?t=1002828") completely, I found that applications, including terminal, no longer wanted to open.  I decided to reboot, got past the GRUB screen and the loading screen with the Ubuntu logo, when it started spewing out console output, instead of loading the GNOME desktop.

I've tried various things already, such as both recovery mode boots that show up on GRUB (but mainly the first one).  The disk check runs through fine, but the package repair tool runs for a bit and then tells me that it cannot resolve practically every place it checks for updates.  It suggested I run apt-get update to fix the problem, but I got the exact same final output when I tried it out. (and I can't scroll up to see any other errors, just the last 20 or so lines)
After I went through the recovery mode the first time, I tried booting again, and got further than before, though it ended at an eternally-spinning cursor, which I could still move around.  Keyboard input also still worked, along with pressing the power button to get Ubuntu to close down peacefully.
I tried the solution [here]("http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/"), to no avail, and when I tried it a second time, the first command, "sudo swapoff /dev/sda5", tells me that /dev/sda5 is an invalid argument, even though fdisk tells me it is the linux swap partition.

Also, I suspect that this may have been caused by VirtualBox, which I had been messing around with, and installed an XP VM on it before the problems started happening.  I say I suspect it because I often see it mentioned during the startup or shutdown sequences, usually the first on the list, and my monkeying around with it may not have been all too beneficial.  However, I'm not knowledgeable enough to know what command to use to remove it, and the fact that I can't scroll through the help pages doesn't really help.

Right now I'm typing this from the Live CD, and I'll probably be here a while longer, googling for help.  I'm probably going to try out just plain disabling swap from the recovery prompt, and removing VirtualBox if I can find the commands for it.  Hopefully someone can help, I'm in a real rut here.

P.S. I'd be willing to backup my data on the main partition and do a reinstall if necessary, thankfully I don't have too much to back up.

---

### Post by jet2230 on 2009-02-18
to remove VirtualBox try: sudo apt-get remove VirtualBox

---

### Post by Moddington on 2009-02-18
I've removed VirtualBox, and now when I bott up, it does the same thing, but one line shows up as red and has '[fail]' on the right side of the line.  I think it said something about the kernel and a driver, and not being able to find one.
I've also removed the beta nvidia driver, so I'm now at a loss at how this happened, the only real lead I still have is with apt-get not being able to resolve any sites, and thus not download any new packages.

---

### Post by jet2230 on 2009-02-18
can't you try to reinstall? if you have no network access then you need some expert help!

---

### Post by cariboo on 2009-02-18
The only thing that video drivers and virtualbox have in common is that they are both kernel modules.

Have you tried starting in recovery mode and selecting xfix from the menu? Once xfix is done select resume and continue on to the desktop, from there you can repair your video driver problems.

If you need network access from the root prompt in recovery mode type:

```
dhclient eth0
```

substitute yor ehternet device for eth0.

Jim

---

### Post by Moddington on 2009-02-19
Heh, I just found out that I have an ATI card, not an nvidia one, on the computer in question.  It was probably my installing of a beta nvidia driver that mucked things up, though I've already set up another install of Ubuntu on the same computer.  I kept the old partition, just to see if I could figure out the problem for fun, but I'm far enough through setting up the new install that I'll be sticking with it even if I do fix the broken one.
Thanks for the help guys, most of the stuff suggested helped, but not in the right way.  It's still going to a text login underneath, but the GUI part still goes to a black screen with an eternally spinning cursor.

---

### Post by Reeman on 2009-02-19
> **Moddington said:**
> Heh, I just found out that I have an ATI card, not an nvidia one, on the computer in question.  It was probably my installing of a beta nvidia driver that mucked things up, though I've already set up another install of Ubuntu on the same computer.  I kept the old partition, just to see if I could figure out the problem for fun, but I'm far enough through setting up the new install that I'll be sticking with it even if I do fix the broken one.
Thanks for the help guys, most of the stuff suggested helped, but not in the right way.  It's still going to a text login underneath, but the GUI part still goes to a black screen with an eternally spinning cursor.
drop to a root login and do a "#dpkg-reconfigure -phigh xserver-xorg" to make X work by the vesa driver for x not anything else until you get the right video drivers for your ati video chip installed. 

If you decide to use the driver directly from ATI (which is what I do) then all you have to do is issue the command "sudo aticonfig --initial -f" to rewrite your /etc/X11/xorg.conf to use the ATI driver after the ATI installer has installed the driver. 

Don't sweat it if the ATI driver fails for some obscure reason. The vesa driver is bullet proof and you can always go back to it if the ATI driver borks, but by being carefull and making sure you have the right driver and the linux lib32 libs installed there should be no trouble.

The reason for using the right driver from ATI is that the automated ATI install in Ubuntu can and does install the wrong one some times! The ati web site has boxed drop down lists to choose os/linux/linux86-64/your card/your card model and then the correct driver download and instructions on installation. 

I found that to make sure the install works flawlessly installing wine helps so that any obscure lib32 dependancies were correctly in place for the ATI 64 bit linux driver.   

It tells you in the ATI web docs that the 32 bit linux libs are required as well for the 64bit linux ati driver to work but does not specify as to whether or not the dev headers are necessary so I installed build essential as well just to be certain everything was in place first.

Hope this saves you a re-install. It did for me with an onboard ATI Radeon XPress1250 that the Ubuntu auto install borked up!

---

