---
title: "Ubuntu AMD64 Live CD on Acer TravelMate 4400 w/ATI X700 (Feisty Fawn 7.04)"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Shadowfire on 2007-04-26
Here is a bandaid install and help for those out there that have a Acer Travel Mate 4400 w/ ATI and want to get it up in AMD64 version of Feisty Fawn 7.04.


***I would only recommend doing this install if your video card is a ATI on this version of laptop.  Do not try this other wise since this is for TravelMates with an ATI video card.


I am not sure if anyone has had any problems with the AMD64 version and Feisty Fawn 7.04 when installing on an Acer TravelMate with the AMD64 version, but I know I did with the Live CD.
Therefore I have decided to come back to post a work around for those that can not wait on a fix :)  and let you know how I got  the LiveCD to work so I could install Ubuntu.


1. Select the safe graphics mode install,

2. Let it load up and error out to no desktop.

3.  Then when it gives you a command prompt type in: 

**sudo vi /etc/X11/xorg.conf**

4. Then add at the bottom:

[B]Section "Extensions"
        Option  "Composite" "Disable" 
EndSection[/B]

5. Then type:

**sudo apt-get update**

6. Then type:

**sudo apt-get install linux-restricted-modules-$(uname -r)**

7.  Then type:

**sudo apt-get install xorg-driver-fglrx**

8. Then type:

**sudo depmod -a**

9. Then type:

**sudo aticonfig --initial**

10. Then type:

**startx**


It should now load to the desktop with full graphics.  You should be able to start / continue the install from here.


 Hope this helps others.

Shadowfire

---

### Post by Nowin on 2007-04-28
I have an Acer Travelmate 4402WLMi with an x700 that stopped working when I upgraded to Feisty. This worked great. Thanks.

---

### Post by MJewkes on 2007-04-30
Same problem
Same laptop

Problem is, I have no wired internet. I'm dual booting XP and Xubuntu, though, so i can download whatever I need to onto my ntfs partition.

Is there anyway to install this without the internet for apt-get?

Thanks,
Matthew

---

### Post by Ub1476 on 2007-05-25
>  	Same problem
Same laptop

Problem is, I have no wired internet. I'm dual booting XP and Xubuntu, though, so i can download whatever I need to onto my ntfs partition.

Is there anyway to install this without the internet for apt-get?

Thanks,
Matthew

Alright, this is an old post, but I'll give you the solution anyway. If you are lucky you might come check in here again:)

Follow this guide: [Linky]("http://ubuntuforums.org/showthread.php?t=448809&highlight=feisty+fawn")

Works, and no need to download drivers before you have gotten Feisty installed! 

Cheers

---

