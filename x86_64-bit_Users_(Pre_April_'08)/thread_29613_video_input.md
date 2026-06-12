---
title: "video input"
date: 2005-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ooZAFLE on 2005-04-25
I searched the forums and couldn't find an answer to this... How do i get video-in to work.. I've gotten my video out to work before by setting up xorg with multiple screens etc. But i'm not sure how to get video in to work... could someone point me in the right direction.. also i was planning on using the tvtime program to watch the signal is this a good program?

---

### Post by ooZAFLE on 2005-04-25
oops.... I got a nvidia MSI NX6600GT card with the vivo plug-in for all video-in and out,

---

### Post by FluffyElmo on 2005-04-25
I don't believe the Nvidia Linux drivers support any video-in functionality. There were several posts on the topic in this Nvidia Linux forum which might provide more information...
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14) 

I think if you use the default open source driver (not the Nvidia one), you may be able to use RivaTV to get tv in going, but at the expense of OpenGL support/performance. The latest Nvidea drivers don't allow external programs (ie RivaTV) to access the GPU registers.
[http://rivatv.sourceforge.net/](http://rivatv.sourceforge.net/) 

Note that I don't have a 6600GT myself but am thinking of buying one, so the above is based on research not experience. Post your experiences, if I don't have to buy an additional capture card I'll have a 6600GT tomorrow...

---

### Post by ooZAFLE on 2005-04-25
thanks... that sucks that there isn't any official nvidia support for video in. and off topic but i definetly recomend the 6600gt card. its freakin' amazing. I realy like the MSI card that i got too. performs very very well and stays cold all the time.

---

### Post by FluffyElmo on 2005-04-25
Yeah, I'm decided on the 6600gt, nothing else comes close for the price. If the MSI runs cool that could be the choice. I'm going to look for a good capture card as well though before I purhase, video capture is actualy more important to me right now.

---

### Post by ooZAFLE on 2005-04-27
i'd get the PCI-e version if its an option for you over the AGP version. the PCI-e runs slightly faster and cooler.

---

### Post by c_dog on 2005-04-27
[QUOTE=ooZAFLE]thanks... that sucks that there isn't any official nvidia support for video in. and off topic but i definetly recomend the 6600gt card. its freakin' amazing. I realy like the MSI card that i got too. performs very very well and stays cold all the time.[/QUOTE]

In all fairness to Nvidia, the Nvidia Geforce 6xxxx series chips do not have their own boradcast video-in encoders. They have Video-out encoders only which are supported by the Nvidia drivers. The chips do have video mixers with they use with external video-in encoders either on card as a third party chip or on another card such as a TV tuner card. If a manufacturer puts a video in on one of the Geforce cards it's not a NVidia chip, so I wouldn't expect Nvidia to have to support it. Therefore you probably want to beat up on MSI to provide the dirvers for the chip they used. Gigabyte and ASUS have been pretty good at supplying third party Linux drivers in cases like this, but I have not seen much of this kind of support from MSI.

---

### Post by ohno on 2005-05-05
hello all,

I just bought one of these 6600GT's for two reasons, Gaming and capturing. The gaming is great but the capture features on this card are truely crap. I just switched over from using a leadtek FX5600 card, and found the Winfast PVR utility that came with it excellent for real time recording in MPEG2 format. *sigh*

Unfortunatly the MSI bundle that comes with the card only has WINDVD creator for recording. Absolute rubbish compared to the Winfast PVR, wont even let you watch what you record, you have to guess or listen to when to stop recording!.

I havent found any other capture programs that are supported by the card, and feel MSI have tricked me into buying a separate Capture card. If i cant find a solution soon soon i will sell the card and go back to Leadtek or find another source.

---

