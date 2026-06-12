---
title: "Graphics driver problem using Wine"
date: 2012-09-23
forum: Wine
---

### Post by sona1111 on 2012-09-23
hello, i am a sort of gamer transferring over to linux. I am trying to get one of my favorites, haloCE (the first one) on ubuntu. I have followed several online guides on how to do this using WINE and it installs ok but after loading the graphics driver does not seem to work, it shows a black screen or weird lines and shapes with the background menu music. Graphics card is a Mobility Radeon X1300.

i have tried installing the direct x windows components and using the useff, use00 and use11 switches. I have also tried virtual desktop and windowed modes.

---

### Post by oldos2er on 2012-09-27
Moved to Wine.

If you want a post moved or deleted, use the 'Report Abuse' button along with a short note explaining what you want to do.

---

### Post by BicyclerBoy on 2012-09-27
Did you run ?
winetricks mfc42

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720&iTestingId=69911](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720&iTestingId=69911)

Your video card is a 9 yr old bottom end model..& ATI as well..
Don't expect too much.
I guess you are running the open source radeon driver ?
I don't know if you can make any improvements..

---

### Post by sona1111 on 2012-09-30
this is what i get from running winetricks mfc42:

```
Executing w_do_call mfc42
Executing load_mfc42
Executing mkdir -p /home/paul/.cache/winetricks/vcrun6
Downloading http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe to /home/paul/.cache/winetricks/vcrun6
--2012-09-30 18:01:34--  http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe
Resolving download.microsoft.com (download.microsoft.com)... 208.47.254.10, 208.47.254.19, 208.47.254.24
Connecting to download.microsoft.com (download.microsoft.com)|208.47.254.10|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-09-30 18:01:35 ERROR 404: Not Found.

------------------------------------------------------
Downloading http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe failed

```

as for the card, i know that its old but:
1) it works on the windows partition of this computer without lagging (which i plan to get rid of if i can)
2) i have had it run on much worse hardware, actually. 

thanks for the info, any other ideas?

---

### Post by cwwilson721 on 2012-09-30
mfc42 seems borked in winetricks right now.

Try```
winetricks vbrun6sp6
``` instead. 

Works for me.

---

### Post by sona1111 on 2012-10-01
```
Unknown arg vbrun6sp6
Usage: /usr/bin/winetricks [options] [command|verb|path-to-verb] ...
Executes given verbs.  Each verb installs an application or changes a setting.

```

furthermore, ```
winetricks already-installed
``` produces: ```
d3dx10
d3dx11_42
d3dx11_43
d3dx9_26
d3dx9_28
d3dx9_31
d3dx9_35
d3dx9_36
d3dx9_39
d3dx9_42
d3dx9_43
d3dx9
d3dxof
devenum
directx9
mfc42
msvcirt
vcrun6sp6
vcrun6

```

...the problem must be somewhere else.

---

### Post by sona1111 on 2012-10-05
bump

---

### Post by ianfromrocky on 2012-12-08
bump - running Champions Online and Guild Wars 2.
Intel 3000HD graphics with Linux Mint 13

I know GW2 work on my desktop with a newer low budget ATI graphics card. I've had virtually no luck in gaming in linux on this machine and I can only think that the MESA driver doesn't actually work very well. Still a solution would be nice. 

I've been using mostly Ubuntu and now Mint since 2007, but recently I've been running windows7 for the last month and a half. That's just wrong in my opinion. Can't wait for the day when I can afford a better linux laptop. :(

[https://docs.google.com/open?id=0BxpRF3Birx06U1JJQ09VZEJHc1U]("https://docs.google.com/open?id=0BxpRF3Birx06U1JJQ09VZEJHc1U")

---

### Post by BicyclerBoy on 2012-12-08
With intel HD iGfx you need latest stable kernel & intel driver.

Try adding xorg-edgers ppa for both..

The default std *buntu distro has SNA features turned off.

---

### Post by Tweak42 on 2012-12-08
> **sona1111 said:**
> 

as for the card, i know that its old but:
1) it works on the windows partition of this computer without lagging (which i plan to get rid of if i can)
2) i have had it run on much worse hardware, actually. 

thanks for the info, any other ideas?

Just because something runs ok on windows doesn't mean it's equivalent under linux.  This is even more the case with older ATI video chips because even if they did have proprietary support at one time, they dropped it once the open source driver got to a resonable level of 2D functions.

2D support should work but barely any 3D, this thread pretty much sums it up:
[http://ubuntuforums.org/showthread.php?t=1723013](http://ubuntuforums.org/showthread.php?t=1723013)

---

### Post by BicyclerBoy on 2012-12-08
"ianfromrocky" has posted about graphics performance of the intel HD3000.
His (or her) desktop with new bottom end AMD GPU was a point of comparison.

Complaining in this thread about legacy support for old ATI cards is not relevant or helpful.

---

