---
title: "WoW Install: Can't click Agree on Licence Agreement"
date: 2008-11-27
forum: Wine
---

### Post by Poptart on 2008-11-27
I'm having a very strange problem. I'm trying to go back to WoW after being away for a few months. I've reinstalled since then, so I have to start at the beginning with the installation. I don't have the CD's, so I'm using the USA Installer found on the website.

Everything works fine until I get to the first license agreement. Then I can't click agree. I've only found one mention of this on the internet, and it involves using Crossover, which I don't use.

Just wondering if anyone has found a way around this that I haven't?

Thanks!

---

### Post by OrbJinzo on 2008-11-27
I think you have to scroll down to the bottom of the lincese to click it. And you can modify your config.wtf 

```
SET gxResolution "1680x1050"
SET gxRefresh "60"
SET hwDetect "0"
SET movie "0"
SET readTOS "1"
SET realmList "eu.logon.worldofwarcraft.com"
SET gxMultisampleQuality "0.000000"
SET readEULA "1"
SET readScanning "-1"
SET realmName "Stormreaver"
SET gameTip "54"
SET gxCursor "0"
SET SmallCull "0.040000"
SET frillDensity "32"
SET farclip "357"
SET MusicVolume "0.60000002384186"
SET SoundVolume "1"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET MasterVolume "1"
SET ffx "0"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET mouseSpeed "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraSmoothStyle "0"
SET cameraSmoothTrackingStyle "0"
SET cameraDistanceMaxFactor "1"
SET SoundZoneMusicNoDelay "1"
SET gxColorBits "24"
SET gxApi "opengl"
SET statusBarText "1"
SET ffxDeath "0"
SET minimapZoom "0"
SET guildMemberNotify "1"
SET profanityFilter "0"
SET readContest "-1"
SET minimapInsideZoom "5"
SET gxDepthBits "24"
SET accountName "Accountnameherestupid"

```

---

### Post by Poptart on 2008-11-27
I did scroll down. I even restarted a few times. The button won't become active to click.

Also, I haven't installed the game yet at all, so I don't even have a directory for the config file. Would making one and putting it there work?

---

### Post by Poptart on 2008-11-28
I did try adding a directory and the config file, but it didn't work. The agreement screen still comes up, and the button still won't work no matter how many times I restart or scroll up and down.

---

### Post by Poptart on 2008-11-28
Problem solved!

I had the up to date version of wine installed, but I uninstalled it and reinstalled and now everything seems to work just great.

---

### Post by JakeWatkins on 2009-02-02
> **Poptart said:**
> I did scroll down. I even restarted a few times. The button won't become active to click.

Also, I haven't installed the game yet at all, so I don't even have a directory for the config file. Would making one and putting it there work?

I'm having this problem.

And to answer your question, no, it would not work that way.. tried it. =\

Also, I tried uninstalling/reinstalling Wine, no help.

---

### Post by Bios Element on 2009-02-02
> **JakeWatkins said:**
> I'm having this problem.

And to answer your question, no, it would not work that way.. tried it. =\

Also, I tried uninstalling/reinstalling Wine, no help.

Upgrade WINE. The bug is fixed in the latest version.

---

### Post by pete44444444 on 2009-02-03
> **Poptart said:**
> I'm having a very strange problem. I'm trying to go back to WoW after being away for a few months. I've reinstalled since then, so I have to start at the beginning with the installation. I don't have the CD's, so I'm using the USA Installer found on the website.

Everything works fine until I get to the first license agreement. Then I can't click agree. I've only found one mention of this on the internet, and it involves using Crossover, which I don't use.

Just wondering if anyone has found a way around this that I haven't?

Thanks!

Please tell me how did you even get the installer to come up? I can't even get that far.

---

### Post by SadaraX on 2009-02-17
> **pete44444444 said:**
> Please tell me how did you even get the installer to come up? I can't even get that far.

Install the latest versions of Wine. You may need to add extra apt repositories to do this.

---

### Post by Pikestaff on 2009-02-18
Update Wine.  If that doesn't still doesn't fix it for you, this is what I originally did when back when I installed the Beta: [http://www.aspectofthehare.net/2008/09/linux-users-do-it-with-wine.html](http://www.aspectofthehare.net/2008/09/linux-users-do-it-with-wine.html)

Hope it helps <3

---

### Post by briandilley on 2009-03-31
Upgrading to the latest version of wine fixes this issue.  There is a great tutorial on winehq.com for doing this in ubuntu:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Basically what this does is let the folks that are actively developing and releasing wine provide you with updates for their software.

---

### Post by xdarkxanarchyx on 2009-12-20
I had this problem as well, I'm running Ubuntu 8.04 LTS and had the error with Wine version 1.0. After getting a newer version (1.1.32) the problem was solved. 
Note: latest version is 1.1.35 at the time of this post but due to server errors and bugs no earlier version worked.

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Linux 2.6.24-26-generic i686

---

