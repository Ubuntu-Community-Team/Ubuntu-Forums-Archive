---
title: "Adobe CS4 on Ubuntu?"
date: 2017-04-21
forum: Wine
---

### Post by farfalle on 2017-04-21
Hey Everyone,
I have been looking around for a way to install the old adobe cs4 suite on to my xUbuntu system, preferably from the disks (it's a 4 disk set, and who has the money to pay for the new yearly subscription version). I have tried to run the installer with wine, but it says that something went wrong, but refuses to give me an error report, it just sits there... thinking...
If it is necessary I can also burn the disks to a flash drive and attempt to install them that way, thanks!

---

### Post by DuckHook on 2017-04-21
Welcome to the forums, farfelle.

WINE is not a magic bullet. My own view is that it's a wonder that it works at all. I successfully use it for a few ancient games, but have not had any luck with newer, more resource-intensive games, nor for most demanding design apps like AutoCAD nor any of the Adobe suite of products. Some have reported at least partial usability, but this varies with the version of WINE and the type and version of the app. Even when usable, I've usually had to make some pretty arcane tweaks and customizations.

I have no idea what your Linux knowledge is, nor your expectations. You might find the link in my sig useful: ***Linux is Not Windows***

If your HW is powerful enough, a better strategy would be to run Windows in a VM and then run CS4 within the Windows VM.

When contemplating the use of WINE, it is always a good idea to first check your app against the Wine Database. A check of your app brings up this: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=14318](https://appdb.winehq.org/objectManager.php?sClass=version&iId=14318) which doesn't look at all promising. Any rating other than "Platinum" is usually worthless in a work or production environment.

---

### Post by Shobuz99 on 2017-04-25
farfalle,
> **DuckHook said:**
> Welcome to the forums, farfelle.

WINE is not a magic bullet. My own view is that it's a wonder that it works at all. I successfully use it for a few ancient games, but have not had any luck with newer, more resource-intensive games, nor for most demanding design apps like AutoCAD nor any of the Adobe suite of products. Some have reported at least partial usability, but this varies with the version of WINE and the type and version of the app. Even when usable, I've usually had to make some pretty arcane tweaks and customizations.

I have no idea what your Linux knowledge is, nor your expectations. You might find the link in my sig useful: ***Linux is Not Windows***

If your HW is powerful enough, a better strategy would be to run Windows in a VM and then run CS4 within the Windows VM.

When contemplating the use of WINE, it is always a good idea to first check your app against the Wine Database. A check of your app brings up this: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=14318](https://appdb.winehq.org/objectManager.php?sClass=version&iId=14318) which doesn't look at all promising. Any rating other than "Platinum" is usually worthless in a work or production environment.
I can add a critique here against WINE, based on my experience with Ubuntu 10.04 LTS and Dreamweaver MX 2004. 
I don't recall the version of WINE at that time; but I had a great deal of frustration installing Dreamweaver MX 2004 using the installer that ran in WINE.
I did manage to get it installed and working; but a had many many crashes over the 5 to 8 years that I used BOTH of those products within 10.04 LTS.
I was even overly determined to use that combination, after 10.04 LTS support ran out. 
Instability was the key factor for the WINE I used at the time.
And as I recall, @DuckHook, you very kindly but firmly suggested that I upgrade Ubuntu and forget about using WINE & Dreamweaver.
I took your advice. I went to 14.04 LTS and did not backup the Dreamweaver software---just the data I created--and instead installed Dreamweaver
on a Windows Vista machine that I only use occasionally for music and website maintenance.
I never looked back. 
I'm sure that CS4 is much different from its predecessor Dreamweaver; but I can freely say that I recommend what @DuckHook says as a better idea.

Rick (Shobuz99)

---

### Post by leunam12 on 2017-04-27
I have it running. Some websites recommend to install it with Playonlinux, but I did a direct install. You have to install the following components with winetricks first: ```
msxml6 gdiplus gecko vcrun2005 ie6
``` you also need the msttcorefonts package

---

### Post by LastDino on 2017-04-27
This is not specifically direct solution to your query, but as someone who did little bit of PS and AutoCad, I've had similar experience as DuckHook, I've tried and not succeeded to get these programs to run smoothly.

Although, AutoCad didn't have any feasible Linux replacement for me, PS did, which was GIMP.

IMO GIMP even though free, performs better than PS unless and until you're talking about advanced extra add-ins which you can buy in PS.

So, as far as I can suggest, give shot at GIMP, it is compatible with formats and all.

---

### Post by mastablasta on 2017-04-28
9,10 year old program. might need an older version of wine fto perform well (not necessarily though). this can easilly be done with playonlinux.

some of it's features might indeed be present in alternative programs.

---

