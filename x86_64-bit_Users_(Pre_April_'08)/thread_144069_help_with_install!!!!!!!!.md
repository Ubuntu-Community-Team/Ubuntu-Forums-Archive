---
title: "help with install!!!!!!!!"
date: 2006-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Richarddddd on 2006-03-13
hello i just recently got a cd in the mail... i tried the live version and it is cool... but i want to know something... I want to load and install my cd but i want to keep the Mac stuff on it too.... like so when i go onto system prefrences i can choose if i want to start up in mac or Ubuntu... how do i do that or can i do that.... also if i cant do that will the ubunto program allow me to load mac soft ware onto it like photoshop for instance, because i need photo shop and i just bought it so i meed the mac software , but i really want the ubuntu too. cant i have both? please get back to me on this as soon as you have any ideas... thank you so much... my email is [email]Piscessage8@aol.com[/email]

---

### Post by ssalman on 2006-03-13
Well let me start by saying I don't have a Mac, but I have read somewhere that you can dual boot with Mac OS, just as you can with Windows. Ubunutu will install (by  default) Grub for you and when you boot it will give you the choice between the two. So no problem. Just make sure that you don't replace the Mac OS when you'r partioning your HD.

Of cource that's all if you have a non-Intel Mac... but if you have one of the new Intel-Macs, that is a different story, and someone with more experiance need to post here :)

---

### Post by jdp on 2006-03-13
If you search the forums you'll find posts about disabling journalling in OS X, then using the free **parted** program on the install CD to resize your OS X partition.   Then you can let the installer automatically configure the free space for Ubuntu and it will also install **yaboot**, not GRUB, to be the boot menu for OS X, Ubuntu or CD.  Using the Startup Disk Control Panel in OS X will change the settings of YaBoot so that the Mac will only boot right to OS X.  You'd have to use the Startup Manager by holding the Option key at boot and selecting the Linux partition to boot from (the one with the little Penguin).

---

### Post by ssalman on 2006-03-13
Sorry, didn't know that there is a different boot manager for Mac... See a person with more experiance with Macs Posted... :)

Edit: I found [this]("http://www.osnews.com/story.php?news_id=13955") site, maybe it will be of some help.

---

