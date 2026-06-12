---
title: "Tried to install playonlinux now stuck"
date: 2015-09-22
forum: Wine
---

### Post by happyhacker on 2015-09-22
I have just installed Ubuntu 14, OK all seems to work. It's on my HP ProBook 4710s.

Want iTunes so did the apt-get install playonlinux and after some time the terminal finished with what appeared to be a need to agree some license with an <OK> on the screen but no way to click it. I shut down and restarted but now playonlinuxlinux is not installed and I cannot get back onto the wireless it just ends up saying "Not connected".

Advice appreciated.

---

### Post by kc1di on 2015-09-22
First we need a little more info. What version of Ubuntu, What desktop Unity?

Your wireless problem is separate from playonlinux.  so lets try to get that going first.

can you go to a terminal and type the following command and post the output here?
```
inxi -Fxz
```
Also post the output of ```
rfkill list all
```

Did you install wine before installing playonlinux?  Wine must be installed first.

---

### Post by mastablasta on 2015-09-22
> **kc1di said:**
> 
Did you install wine before installing playonlinux?  Wine must be installed first.


not really. wine version (various) can be installed later during programs install inside Play on Linux.

also not sure why OP felt the need to do it in terminal.

to select OK you can move with tab and press enter to confirm the selection. I believe it is the same in windows when you install CLI stuff.

---

### Post by happyhacker on 2015-09-22
inxi is not installed.
WIFI is working after restart twice.
I managed to get playonlinux installed (I think!). Installed Wine but not seemingly without hiccups. Tried iTunes, downloaded 64bit from Apple site.
Playonlinux asked me "install on new virtual drive", don't know what that means but tried it so I called it "virtual". The I got confused; do I want a 32 or64 bit drive (do I want a drive at all?). The file I got from Apple was 64 but as far as I know my HP 4710s is a 32 bit thingy. I selected 64, Then it said Wine being updated. Then it asked me to select a windows version so let's have windows 8! In the end after loads of seemingly error messages and my fumbling I have an iTunes logo on my desktop which does not run and asks me to install it.
So now I have after many attempts an "unclean" Ubuntu system. How do I get back to square 1? reinstall Ubuntu or maybe there's a cleanup utility somewhere?
Many thanks.

---

### Post by QIII on 2015-09-22
Since the wireless issue is addressed, moved to Wine.

---

### Post by happyhacker on 2015-09-22
OK, start again. I don't know if this forums is correct now but anyway, I used playonlinux (it finally seems to be going through the process - sort of) to install iTunes 12. It even installed another WINE version which I did first. During install it said I should get iTunes from Apply affiliates BUT there is only a 64bit version there. When I downloaded this at great expense to my limited B/W contract playonlinux said this was the wrong version! 

So where do I get the )correct) 32bit iTunes version from? That may seem obvious but it's 100MByte and I don't want to get it only to find there is another problem.

Advice appreciated.

---

### Post by uninvolved on 2015-09-24
I have no idea how well it will work in Wine but, well, here you go:
[http://filehippo.com/download_itunes_32/tech/](http://filehippo.com/download_itunes_32/tech/)

That is from a third party site. I've downloaded and have had good luck with them in the past - they've not latched on Spyware that I've ever seen. That was also the most recent version that I was able to find. I did check the regular download page at Apple's site but was unable to determine if it was 64 or 32 bit so I have elected to give you the above link. That is, as requested, a 32 bit version and is recent.

You should let us know if it works.

---

### Post by happyhacker on 2015-09-24
Is this the right one: [https://support.apple.com/kb/DL1790?locale=en_GB?](https://support.apple.com/kb/DL1790?locale=en_GB?)

Presumably though the one from file hippo will be sourced from Apple so should update itself from there!

I have used up my bandwidth for this month downloading the wrong stuff so will have to wait for next month.

---

### Post by mastablasta on 2015-09-24
this page says silver rating on version 12: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=31322&iTestingId=89752](https://appdb.winehq.org/objectManager.php?sClass=version&iId=31322&iTestingId=89752)

you need wine 1.7.45. obviously you need winXP emulation

> Works without UI artifacts like blank elements with installed graphic library gdi+:

winetricks gdiplus

and 'Windows XP' emulation

virtual drive is the drive in wine like C:\ it's not really there it's just the folder in the OS but to wine it acts as drive.

proprietary software.... might be easier to install some XP in virtual box and run them there.

---

### Post by happyhacker on 2015-09-24
Let's suppose for the moment I forget emulation. What I'm trying to achieve is to load music CDs on my Ubuntu laptop and easily transfer them to my MacBook Pro which doesn't have a DVD drive. Which native music AP would be best to use on Ubuntu that will import into iTunes on Yosimite? Thanks.

---

### Post by mystics on 2015-09-25
I think Banshee will allow you to sync music files. I'm not entirely sure how it works or if it would sync with an iTunes on a separate computer, though.

Another option is to put the music on your computer and then use a USB, Google Drive, or something else like that to transfer the files to your MacBook. Once there, you can follow Apple's guide to put it on iTunes: [https://support.apple.com/kb/PH20507?locale=en_US](https://support.apple.com/kb/PH20507?locale=en_US)

Either way, trying to get iTunes to work with Wine/PlayOnLinux might be the hardest way to get done what you want to get done given its somewhat iffy performance with Wine.

---

### Post by happyhacker on 2015-10-02
Well, I installed the 32bit version with PlayOnLinux but during that process I noted: "Error in POL_Wine, Wine seems to have crashed.". I continued but the iTunes screen when opened was largely blank but iTunes did report it couldnt contact the store. Any advice on what to do now?

---

### Post by mastablasta on 2015-10-02
ok I am not sure what iTunes do exactly (i thought it's a DRM web connected client that allows you to buy music cheaply online) and why do you need them in this case. but here is what I would do:

I would rip the CDs into MP3 files (many tools for that exist), then I would just move them over to another PC via network, USB flash drive or cloud storage service.

another option would be to create image of the CD and move that to another PC and then open the image there and moving the files to whatever program read the CD files in Mac.

iTunes - who needs them?


as for wine case - I am not sure what is wrong now, but if you have 64bit OS and trying to install 32 bit windows program you need to make sure that wineprefix is also 32 bit (by default it would create a 64bit one).

---

### Post by mystics on 2015-10-02
> **happyhacker said:**
> Well, I installed the 32bit version with PlayOnLinux but during that process I noted: "Error in POL_Wine, Wine seems to have crashed.". I continued but the iTunes screen when opened was largely blank but iTunes did report it couldnt contact the store. Any advice on what to do now?

This sounds like a common issue with iTunes: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=31322&iTestingId=88934](https://appdb.winehq.org/objectManager.php?sClass=version&iId=31322&iTestingId=88934)

Not sure about a work-around, but I would check into what mastablasta advised. 

Also, have you tried the method of transferring files that I mentioned above? Did it not work? Or is this still mostly a desire to get it to work for the future?

> **mastablasta said:**
> ok I am not sure what iTunes do exactly (i thought it's a DRM web connected client that allows you to buy music cheaply online)

Apple has since removed the FairPlay DRM from music. You can thank Amazon for that.

Anyways, iTunes is a convenient method for people with other Apple hardware, and anyone with a Mac will find it a good enough media player to just stick with it. It isn't necessary for music ripped from a CD, but it is the first choice for a lot of Mac users.

---

### Post by happyhacker on 2015-10-02
I will copy the image and transfer that. Thanks for the instructions.

---

