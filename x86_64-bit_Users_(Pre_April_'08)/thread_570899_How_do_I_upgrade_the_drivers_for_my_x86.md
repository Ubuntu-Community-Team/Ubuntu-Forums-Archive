---
title: "How do I upgrade the drivers for my x86?"
date: 2007-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by MasterNetra on 2007-10-08
How do I upgrade my drivers for my 64-bit x86 graphics card? I'm using Feisty Fawn version. I'm trying to do this in a effort to help correct a problem with Planeshift, which is when i run the updater the text on the updater is either distorted or not there... I also have attempted to run the client and the flash screen flickers on then to black with small sections showing then going back again..thus i suspect my drivers not up to date. Otherwise i more then meet the MMO's requirements.

---

### Post by John.Michael.Kane on 2007-10-08
Might help, if you told us what gpu you are using.

---

### Post by MasterNetra on 2007-10-08
> **SD-Plissken said:**
> Might help, if you told us what gpu you are using.

gpu?? where would i find that information...Sorry I'm still a noob when it comes to linux. In HardInfo it says this: OpenGL Renderer Mesa DRI Intel 845G 20061017 x86/MMX/SSE2. Doesn't saying anything regarding a gpu. I'm not famliar with with exact specs of this computer as it is. Only really that its a Gateway 500se... Far from new but still can run PlaneShift and Anarchy Online (Well at least it did when i was running XP...)

---

### Post by John.Michael.Kane on 2007-10-08
> **MasterNetra said:**
> gpu?? where would i find that information...Sorry I'm still a noob when it comes to linux. In HardInfo it says this: OpenGL Renderer Mesa DRI Intel 845G 20061017 x86/MMX/SSE2. Doesn't saying anything regarding a gpu. I'm not famliar with with exact specs of this computer as it is. Only really that its a Gateway 500se... Far from new but still can run PlaneShift and Anarchy Online (Well at least it did when i was running XP...)

Gpu=graphics processor unit eg: the Video card. 

Most likely looking at what you typed your machine might have a intel gpu.

Type the below command inside your terminal.
```
lspci
```

You should see a few line of hardware info. one of the lines may read like the one below.
Example 00:05.0 VGA compatible controller: your video card name here.

---

### Post by MasterNetra on 2007-10-08
> **SD-Plissken said:**
> Gpu=graphics processor unit eg: the Video card. 

Most likely looking at what you typed your machine might have a intel gpu.

Type the below command inside your terminal.
```
lspci
```

You should see a few line of hardware info. one of the lines may read like the one below.
Example 00:05.0 VGA compatible controller: your video card name here.

yea its Intel, here is what was displayed.
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by John.Michael.Kane on 2007-10-08
> **MasterNetra said:**
> yea its Intel, here is what was displayed.
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Theres no clear cut way I can find either through searching the forum or through Google to upgrade Intel drivers. For the most part Intel states it's best to get the drivers direct from your distro maker. In this case that would mean Upgrading to Gutsy.

That said your options are.
1) Upgrade to Gutsy 'might be the best way to go.'
2) Try to sort out the issues currently plaguing your setup.

---

### Post by MasterNetra on 2007-10-08
> **SD-Plissken said:**
> Theres no clear cut way I can find either through searching the forum or through Google to upgrade Intel drivers. For the most part Intel states it's best to get the drivers direct from your distro maker. In this case that would mean Upgrading to Gutsy.

That said your options are.
1) Upgrade to Gutsy 'might be the best way to go.'
2) Try to sort out the issues currently plaguing your setup.

I plan too. Would it be possible to upgrade without losing data?

---

### Post by John.Michael.Kane on 2007-10-09
> **MasterNetra said:**
> I plan too. Would it be possible to upgrade without losing data?

Under normal situations upgrading from Feisty 64bit to Gutsy 64bit should not be an issue,however. Issues sometimes happen. 

What I would suggest is you backup any important data before upgrading, As this will allow you to upgrade without fear of loosing your data should a issue arise.

To upgrade from Feisty 64bit to Gutsy 64bit run the command below.
```
gksudo "update-manager -c -d"
```

---

### Post by MasterNetra on 2007-10-09
Actually I'm having a problem at the moment. I have the details here:

[http://ubuntuforums.org/showthread.php?t=533257&page=3](http://ubuntuforums.org/showthread.php?t=533257&page=3)

My posts begin from the top of page 3 there.

---

### Post by John.Michael.Kane on 2007-10-09
> **MasterNetra said:**
> Actually I'm having a problem at the moment. I have the details here:

[http://ubuntuforums.org/showthread.php?t=533257&page=3](http://ubuntuforums.org/showthread.php?t=533257&page=3)

My posts begin from the top of page 3 there.

The problem could be a broken dependency.

Try the below method.
First run:
```
sudo dpkg --configure -a
```
This command will try to configure all packages that are unconfigured.

Should the above not work move on below.

Next:
```
sudo aptitude -f remove
```
This command will try to remove all problematic packages automatically.
Now rerun:
```
sudo dpkg --configure -a
```

Last resort should the above not work.
```
sudo aptitude remove -f packageA
```  where packageA is the name of the package. In this case it would wine or winefix, and any of it's dependencies.

---

### Post by MasterNetra on 2007-10-09
I learned the problem (which there was also a problem on winefix installtion) is that it was trying to find a dircectory that didn't exist so it couldn't "update, find or remove" I'm atm at my college and will attempt to address this when i get home as instructed.

---

### Post by MasterNetra on 2007-10-09
That didn't work, Its says i may have to manually fix it...

---

### Post by MasterNetra on 2007-10-09
Fixed! I have to manuelly edit dpkg's status and available files and remove winefix's files in the info folder. I was wondering would it be safe to leave the .png files alone along with there strange connecting files like "application-x-extension-lnk.png", "x-ms-dos-executable.png", and "x-extension-msi.png" ?

---

### Post by John.Michael.Kane on 2007-10-09
> **MasterNetra said:**
> Fixed! I have to manuelly edit dpkg's status and available files and remove winefix's files in the info folder. I was wondering would it be safe to leave the .png files alone along with there strange connecting files like "application-x-extension-lnk.png", "x-ms-dos-executable.png", and "x-extension-msi.png" ?

Depends they make be expecting wine to be install. Watch for any errors related to those files. Most likely you should be fine.

Push comes to shove you should be able to remove those .png files.

---

### Post by MasterNetra on 2007-10-09
Aye but i really wouldn't look forward to removing each of them individually x.x Also i should note i removed "winefix" which was a script ment to help better wine. Wine was never removed and functions as usual.

---

### Post by John.Michael.Kane on 2007-10-09
> **MasterNetra said:**
> Aye but i really wouldn't look forward to removing each of them individually x.x Also i should note i removed "winefix" which was a script ment to help better wine. Wine was never removed and functions as usual.

IMHO if your not seeing any further errors or problems leave them be.

---

### Post by MasterNetra on 2007-10-09
Ok sounds good. Oh regarding the 7.10 release, i think i'll wait until its out of beta. I've already pre-ordered a CD.

---

### Post by MasterNetra on 2007-10-09
Eep i just released Ubuntu isn't reconizing my seconded drive which is my CD-RW drive...

---

### Post by John.Michael.Kane on 2007-10-09
> **MasterNetra said:**
> Eep i just released Ubuntu isn't reconizing my seconded drive which is my CD-RW drive...

Do you mean when you insert a cd it does not mount it, and show a icon on the desktop?

To check to see if that piece of hardware is seen run the command below.
```
lshw
```

Scroll down to the section label ide, and you should see your device or not.

---

### Post by MasterNetra on 2007-10-09
I don't reconize it saing there is any, but my first drive which is a DVD-ROM is seen by the system and used... Both devices came with the computer why wouldn't Ubuntu recognize it? Not sure but i think knoppix may of... And yet it was in that CD-RW that i loaded and installed Ubuntu... btw i meant realized not released >.>

---

### Post by John.Michael.Kane on 2007-10-09
> **MasterNetra said:**
> I don't reconize it saing there is any, but my first drive which is a DVD-ROM is seen by the system and used... Both devices came with the computer why wouldn't Ubuntu recognize it? Not sure but i think knoppix may of... And yet it was in that CD-RW that i loaded and installed Ubuntu... btw i meant realized not released >.>

You can try putting a cd in the drive in question, and see if it will mount the cd.

---

### Post by MasterNetra on 2007-10-09
Actually Hardinfo report shows it only reconizes the DVD drive and not the cd-rw... >.> Maybe i should get a DVD-RW drive to replace it >.> I just gotta make sure it has a IDE connection >.>...lol for some reason Hardinfo has it listed under SCSI instead of IDE :p

---

