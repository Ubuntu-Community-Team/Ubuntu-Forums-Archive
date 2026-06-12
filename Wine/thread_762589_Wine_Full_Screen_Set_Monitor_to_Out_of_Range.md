---
title: "Wine Full Screen Set Monitor to Out of Range"
date: 2008-04-22
forum: Wine
---

### Post by Eddie Wilson on 2008-04-22
Good Day All,
I've got a new problem with screen resolution in Wine. I've been running Ubuntu for several years and I've always used Wine to play  my Hoyle games. I've always been able to play them in full screen. I've upgraded or lets say installed Ubuntu 8.04 RC and also installed Wine after that. I ran winecfg and performed all the settings that I always use. I installed my Hoyle programs and then tried to play them. I can play in windowed mode but when I go to full screen I get and Out Of Range message on my monitor. I can go back to windowed mode and it works just fine. I've never had this problem in Wine before. I've done several searches and found nothing but I've not gone to the Wine forums yet. I thought I would try here first. I'm not wanting anyone to solve my problem for me I  just would like to know if anyone has any idea what may be causing the problem. Other than that everything is working great.

Thanks,
Eddie

---

### Post by kahrytan on 2008-04-22
Are you using 800x600 resolution?

---

### Post by Eddie Wilson on 2008-04-23
Nope. I'm using 1024 x 768. That's what I've been using for quite some time and I've never has any problems.:confused:

Thanks,
Eddie

---

### Post by Eddie Wilson on 2008-04-24
Well I kept searching and I may have found my problem. I had to do a reinstall because of an unrelated problem. I reinstalled everything except for the Nvidia drivers. Also that means that I don't have Compiz Fusion enabled yet. My WINE and Hoyle games are working perfect now. I'm not sure which one caused the problem but I will find out tonight. I will install the Nvidia drivers and also see if Fusion causes any problems when enabled. I will report back and hopefully be able to mark this solved.

Eddie

---

### Post by Eddie Wilson on 2008-04-28
I found the problem for sure. It was not Compiz Fusion. It was the new Nvidia driver. I removed it and installed the nvidia-glx driver and had no further problems. I have an older Nvidia card. I installed the nvidia drivers using the app. in Ubuntu 8.04 and thats how nvidia-glx-new got installed.

Thanks,
Eddie

---

### Post by Scarecrow60 on 2011-06-28
Open "Applications"
Under "Installed Applications" you should find "Configure Wine"
Open "Configure Wine" and click on the "Graphics" tab
Check the box to "Emulate a virtual desktop"
The default 800 x 600 resolution worked well for me.

---

