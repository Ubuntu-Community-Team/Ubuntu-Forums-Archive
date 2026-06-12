---
title: "X-Fi Linux drive in Ubuntu 8.04"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by phlebas on 2008-05-15
Has anyone gotten the latest linux driver for Creative's X-Fi sound card to work?

[http://us.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=1&Product_Name=Sound+Blaster+X-Fi+Platinum&Product_ID=14065&modelnumber=&driverlang=1033&OS=12&drivertype=1&x=30&y=10](http://us.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=1&Product_Name=Sound+Blaster+X-Fi+Platinum&Product_ID=14065&modelnumber=&driverlang=1033&OS=12&drivertype=1&x=30&y=10)

If so, how? 

Thanks,
Flea

---

### Post by jallosway on 2008-05-15
Hi!

I'm sorry to say that I have the same problem but no solution. When I try to install [COLOR="Red"]XFiDrv_Linux_US-1.18[/COLOR] it says there is no device. I guess Ubuntu doesn't recognizes my X-Fi Extreme Audio soundcard.
Anyone having a solution?

Many thanks, Jallosway!

---

### Post by Gideon123 on 2008-05-15
Look at this tread. Its all about the xfi card.

[http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi](http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi)

---

### Post by radamo on 2008-05-16
> **jallosway said:**
> Hi!

I'm sorry to say that I have the same problem but no solution. When I try to install [COLOR="Red"]XFiDrv_Linux_US-1.18[/COLOR] it says there is no device. I guess Ubuntu doesn't recognizes my X-Fi Extreme Audio soundcard.
Anyone having a solution?

Many thanks, Jallosway!

I have the same card.  I worked with one of the support guys over at 4-front site ([http://www.4front-tech.com/forum/viewforum.php?f=3](http://www.4front-tech.com/forum/viewforum.php?f=3)) and they could not get my X-fi Extreme Audio to work.  I am still using on board sound. Would love to see somebody get this to work.
RA

---

### Post by Plasma_NZ on 2008-05-17
> **jallosway said:**
> Hi!

I'm sorry to say that I have the same problem but no solution. When I try to install [COLOR="Red"]XFiDrv_Linux_US-1.18[/COLOR] it says there is no device. I guess Ubuntu doesn't recognizes my X-Fi Extreme Audio soundcard.
Anyone having a solution?

Many thanks, Jallosway!

You have the same card as me... and ubuntu see's it automatically as a CA0106 - and it works fine... 

And im running 3 audio-cards...

Onboard
PCI Sound Blaster Live! 5.1
PCI Audigy X-FI Extreme Audio 5.1

Try a "asoundconf list" - is it listed??
Also try "lspci" can u see your audigy card in there..?

---

### Post by jallosway on 2008-05-18
Thanks for all replies!

@Gideon123
I will try that guide again since he edited it 2 days ago. Maybe it'll work this time. :)

@radamo
I will keep on trying and if I come up with something that's works I will give you a call!

@Plasma_MZ
Ok, so CA0106 actually is my Extreme Audio card? Thats nice to know. This is my output from lspci:
...
[COLOR="Red"]02:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS[/COLOR]

I guess Ubuntu recognizes my soundcard after all. :) But how do I check the "asoundconf list"?

---

### Post by Plasma_NZ on 2008-05-19
> **jallosway said:**
> Thanks for all replies!

@Gideon123
I will try that guide again since he edited it 2 days ago. Maybe it'll work this time. :)

@radamo
I will keep on trying and if I come up with something that's works I will give you a call!

@Plasma_MZ
Ok, so CA0106 actually is my Extreme Audio card? Thats nice to know. This is my output from lspci:
...
[COLOR="Red"]02:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS[/COLOR]

I guess Ubuntu recognizes my soundcard after all. :) But how do I check the "asoundconf list"?

Ok to see what cards asoundconf can see in terminal type 

```
asoundconf list
```

you should get something like this 

> physics@physics:~$ asoundconf list
Names of available sound cards:
CA0106
Live
NVidia
physics@physics:~$ 


Then to set a certian card as ubuntus default use

```
asoundconf set-default-card name-of-card-thats-reported-in-previous-output
```

eg.. for me to set my audigy as default in terminal i type

```
asoundconf set-default-card CA0106
```

---

### Post by jallosway on 2008-05-20
Thanks for a nice tutorial, Plasma_NZ!

I actually reinstalled Ubuntu before I took a look at your tutorial and you know what? Now it works, just like (auto)magic! I'm happy and hopefully someone else will find this thread useful and avoid being too fast doing a reinstall.

Anyway, thanks a lot! - Jallosway

---

### Post by Skeet on 2008-05-20
Too bad it doesn't support XtremeAudio :(

Knew I should have gone for the XtremeGamer..

---

### Post by Yellow Pasque on 2008-05-20
> Knew I should have gone for the XtremeGamer..
No, you should've avoided Creative hardware altogether...

---

### Post by Plasma_NZ on 2008-05-21
> **Skeet said:**
> Too bad it doesn't support XtremeAudio :(

Knew I should have gone for the XtremeGamer..


My Extreme Audio is workin fine :) if u read my posts in this thread you'll find out how to get it to work..

---

### Post by borlosky on 2008-07-11
> **Gideon123 said:**
> Look at this tread. Its all about the xfi card.

[http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi](http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi)

thanks!!!, worked great.

---

### Post by Phkillah on 2008-09-14
I'm using CA0106 successfully on an X-Fi Extreme Audio..
However, only 2.1 works:(

Any ideas?

---

