---
title: "Wireless internet card not working 3945ABG"
date: 2008-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by xithilinx on 2008-02-22
I'm having a problem with the Intel Pro/Wireless 3945ABG not working within ubuntu 7.10 amd64. I'm quite new to this and have tried going the NDISwrapper route and actually got the driver to install, or atleast I think it did. 
 
sudo ndiswrapper -l
bcmwl5 : driver installed

Which is the inf file I was supposed to install in the how-to guide at 

```
http://ubuntuforums.org/showthread.php?t=112526
```

Now the thing is it seems that everything is working fine, but just as I try working with wifi-radar I get no results as to it working. Even doing the commands in the how to just result in these.. 

sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

I'm not even sure what I'm doing wrong seeing as I did everything included in the how-to, so it's just getting frustrating to work on.  By the way I'm using eth0 as my lined connection at the moment to post this, but preferably I would like the wireless internet to be working on this distribution instead and am just getting no results thus far.

---

### Post by Kilz on 2008-02-22
Perhaps [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy") can be of help to you.

---

### Post by xithilinx on 2008-02-22
I don't exactly get what that first step expects me to do ... 

The wifi-radar program won't even recognise that I have a wireless card.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        no wireless extensions.

eth0      no wireless extensions.

Plus I have no idea where to start on getting this to work as the howto guide I supplied did not work successfully with me, so I'm stuck as to what to do.

---

### Post by xithilinx on 2008-02-22
One more thing is that I think that ubuntu doesn't even see the card for some reason because I've heard that for most people when they install gutsy the card works straight out of the box. Although that wasn't what happened for me obviously, and I am sure that the card works fine inside my laptop (m1710) since when I used to use windows it worked perfectly fine.

---

### Post by Kilz on 2008-02-22
> **xithilinx said:**
> I don't exactly get what that first step expects me to do ... 

The wifi-radar program won't even recognise that I have a wireless card.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        no wireless extensions.

eth0      no wireless extensions.

Plus I have no idea where to start on getting this to work as the howto guide I supplied did not work successfully with me, so I'm stuck as to what to do.
Your card should be automatically detected, you should need no howto's. [Take a look at this page. ]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting") perhaps it can help you.

---

### Post by xithilinx on 2008-02-23
Alright well I feel dumb now haha. I forgot that a long time ago I disabled the wireless internet card inside my bios so I just went inside and activated it and now it works perfect. 

Thanks for the help by the way, this forum really does have the quickest replys and the most fullfilling answers.

---

