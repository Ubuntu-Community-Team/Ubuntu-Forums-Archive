---
title: "Anyone tried 64Studio? What about GRUB?"
date: 2007-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Unterseeboot_234 on 2007-06-22
I've had a couple of glitches with 64-Feisty. I mean, it installs clean and comes with a larger assortment of pre-built goodies however UbuntuStudio is for 32-bit. I whacked out a whole hard disc installing a 3rd-party user's .deb for a video app, Cinerella. Some kind of lib dependency that put my machine into a constant loop that prevented shut-down, updates or data access. Maybe if I knew Linux in the terminal I could have saved my drive. I won't build software in Feisty either because of that experience. I use Dapper and I'm very happy with it except for custom audio recording.

I found 64Studio. Built for the AMD-64. 64Studio is a Debian distro with the multi-media apps, pre-built and layered on top of a custom Debian Linux kernel. Downloadable ISO CD installer. This will require its own partition. I am tempted.

**MY QUESTION:** Will GRUB see all of my partitions after I install 64Studio? Any problems with 'buntu Dapper, 'buntu Feisty and Debian 64Studio and then having a choice which partition to boot?

---

### Post by crjackson on 2007-06-23
Go for man!  Let me know what you think of it for video / audio editing.  I'm struggling with Feisty64.

---

### Post by incubus on 2007-06-23
I know this is the worst answer you could expect, but it depends.  It depends on how studio64 will install GRUB.  Most modern installers will try to detect other operating systems to help new users, but to be sure this is something you'd have to ask the forum over studio64.

Now don't be scared of installing another OS, as long as you install in another partition.  Even if it messes up the MBR, you can fix it with the Ubuntu CD.  It's not hard.  There are many tutorials on this here.  You can also ask us if you can't follow them.

Either way, you know it: back up your stuff.  Don't trust computers.

incubus

EDIT: oops: s/studio64/64studio/g

---

### Post by incubus on 2007-06-23
Here's their forum:
[http://64studio.com/forum/](http://64studio.com/forum/)

Personally, if the installer asks if you want to overwrite the MBR, I would answer No and I would edit the GRUB menu.lst manually.  You'd just have to add an entry for 64studio, you know what I mean?

But if you don't want to get your hands dirty, you could ask their forum to see if everything is automatic.

incubus

---

### Post by Unterseeboot_234 on 2007-06-24
OK, thank you for your replies. I have been struggling. First, learn a little about vmPlayer from vmWare. The version in Ubuntu Add/Remove nor the script in Automatix2 DO NOT WORK. Period. End of discussion. If you have installed those (or tried to) you will have to remove everything vmWare related.

I reinstalled build-essential. You need that any more. Hardly anyone makes binaries that "run out of the box". You download a ready-to-build bundle. You've heard of plug and pray ... well we're in the days of run and pray. sighhhhh :)

I had to download the tar.gz of vmPlayer. Version 2.0. While I was snooping around on the vmWare site I found a thing called appliances. Someone has pre-fabricated an install of 64Studio to run within vmPlayer. I downloaded the 64Studio appliance and unzipped. A note about the 64Studio from the vmWare listings. The link is wrong. It has a typo. Clicking the link puts htttp://... . I had to Right-click the link --> properties -->Ctrl-C and paste that in the navigator location field on my browser take out one of the "t' before hitting return. It's a http: download when I wished it was FTP (translation: it takes forever and a day to download, go get a hamburger or something).

I unzipped the vmPlayer 2.0. cd into that folder and sudo ./vmware-install.pl.

I was almost surprised when it worked. I will have to learn more about vmPlayer. I told it no on a network when I should have said "heck yeah, buddy!" things like that. Anyway, vmPlayer came up. I then nav over to where I have the 64Studio upacked and waiting. I selected 64studio.vmx. Wait about 1.5 minutes and WHOAH, I've got a Debian desktop running inside a window in Ubuntu. The 64studio appliance is just like logging on to a Ubuntu session. The person that made 64Studio gives you a username: bagside and password: bagside. Then you have the Debian desktop. It's huge, the desktop, bigger than a ubuntu desktop so you have to scroll the horizontal and vertical scrollbars to get to some of the buttons and menus.

But, it comes loaded with a bunch of studio software. Already built. Already running. You will need to learn JACK, and get this, ROSEGARDEN. I've had issues with Rosegarden.

I'm excited. I can try things now. BEFORE I mess up my Dapper.

If any of you wonderful Forum readers is reading this and want to keep the discussion going, please do. If I get more replies I will consider a partion, Debian desktop (64Studio) install and then editing GRUB. I'm pretty sure GRUB will have to be edited. And, because of the Ubuntu Forums I was pre-warned that the default file for GRUB is pretty much "left-handed" and unusual.

I'm sorry I don't have a HowTo on VMware. But, I went through several attempts because of several comments on this board that VMware was worth it. Flat out worth it. OK, it is, but I was after a 64-bit media collection. I'll go back to Fiesty when I have more time and I hope UbuntuStudio has 64-bit.

---

