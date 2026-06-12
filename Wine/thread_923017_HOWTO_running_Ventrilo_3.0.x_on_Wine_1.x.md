---
title: "HOWTO: running Ventrilo 3.0.x on Wine 1.x"
date: 2008-09-17
forum: Wine
---

### Post by couzin2000 on 2008-09-17
I've been a big Eve-Online fan, and I've been trying to free up my two hands of the incessant typing, so I went to find some player-to-player comlink, but as you would guess, Eve Voice doesn't work properly, and most players playing Eve use Windows. No one using TeamSpeek there, everyone praises the quality of Ventrilo.

So I set out to have it run - and I did it. Now, let me share with you.

Before I start, let me explain my setup: **Ubuntu Hardy 8.04**, **Wine 1.1.4**, **Ventrilo 3.0.1**. I also have a VirtualBox install of WinXP SP2, which I was able to use to snatch away the [FONT="Courier New"].acm[/FONT] file I needed - but I have links for that if you don't have yours.
As hardware, I have a **Sound Blaster Audigy I**. I also use **ALSA** for everything sound.
One last thing: I don't own a 64-bit version of Ubuntu, so I don't have a clue how to do it for that one. *If someone suggests a thread, I'll add it here*.

_**HOWTO run Ventrilo on Ubuntu with Wine**_
[LIST]First, you must install **Wine 1.x** - if it's not done already, please floow the instructions here: _[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")_. It's better to install the [FONT="Courier New"].deb[/FONT] file directly than to compile from source, as far as I've read.[/LIST]
[LIST]Once you've installed the whole thing, you need **Ventrilo**. More specifically, you need Version 3.0.x of Ventrilo for Windows --the i386 version. Get it here: _[http://www.ventrilo.com/download.php]("http://www.ventrilo.com/download.php")_. Better to download it to your Desktop for now.[/LIST]
[LIST]When you try to run Ventrilo, you'll need a codec to be able to listen and talk at the same time, specifically **GSM 6.10**. This comes in the form of a file named [FONT="Courier New"]msgsm32.acm[/FONT]. you can get it from _[Filefront]("http://files.filefront.com/msgsm32acm/;4475049;/fileinfo.html")_, or from _[DriverGuide]("http://members.driverguide.com/driver/detail.php?driverid=7019")_, but the best solution is to get it from an existing Windows installation (in the _C:\WINDOWS\System32_ folder). I got mine this way.[/LIST]
[LIST]Copy the [FONT="Courier New"]msgsm32.acm[/FONT] file inside this folder: _[FONT="Courier New"]~/.wine/drive_C/windows/system32[/FONT]_.[/LIST]
[LIST]Open your [FONT="Courier New"]_~/.wine/drive_C/windows/system.ini_[/FONT] file using your favorite text editor. It should look something like this:```

[mci]
MPEGVideo=mciqtz.drv
MPEGVideo2=mciqtz.drv
avivideo=mciavi32.dll
cdaudio=mcicda.dll
sequencer=mciseq.dll
vcr=mcivisca.drv
; videodisc=mcipionr.drv
waveaudio=mciwave.dll

[drivers32]
msacm.imaadpcm=imaadp32.acm
msacm.msadpcm=msadp32.acm
msacm.msg711=msg711.acm
msacm.winemp3=winemp3.acm
vidc.mrle=msrle32.dll
vidc.msvc=msvidc32.dll
vidc.cvid=iccvid.dll
; vidc.IV50=ir50_32.dll
; vidc.IV31=ir32_32.dll
; vidc.IV32=ir32_32.dll
```[/LIST]
[LIST]Add the following line at the end of the file:```
MSACM.msgsm610=C:\windows\system32\msgsm32.acm
```*[COLOR="Red"]Note:[/COLOR]I found this particular line here:[http://www.codeweavers.com/compatibility/browse/name/?forum=1;app_id=413;mhl=4190;msg=3469]("http://www.codeweavers.com/compatibility/browse/name/?forum=1;app_id=413;mhl=4190;msg=3469"). Apparently, the full path is required in some cases for Ventrilo to find the codec. Most other howtos didn't specify, so I was left in the dark for quite a while before I found this. Thanks to whoever contributed to this post!*[/LIST]
[LIST]You need to setup the sound in Wine so that it uses ALSA. Go into **Applications > Wine > Configure Wine**, and under the **Audio** tab you must set sound drivers to [FONT="Courier New"]ALSA[/FONT]. As well, set **Hardware Acceleration** to [FONT="Courier New"]Emulation[/FONT] and check the **driver emulation** checkbox.[/LIST]
[LIST]Now to install Ventrilo: copy the install file to [FONT="Courier New"]_~/.wine/drive_C/program files/Ventrilo_[/FONT], and double-click it - the install should run smoothly.[/LIST]
[LIST]Once installed, go into **Applications > Wine > Ventrilo** and click on Ventrilo. The program should start.[/LIST]
[LIST]You'll need to input the server and personal info in there: that I leave to you. I've had absolutely no trouble getting a connexion with ventrilo, so you should have no trouble either. For this howto, skip this part and go straight to **Setup**.[/LIST]
[LIST]In the **Voice**, **Bind** and **Speech** tabs, make sure the [FONT="Courier New"]Use DirectSound[/FONT] checkbox is checked, and that you pull down the [FONT="Courier New"]Default DirectSound device[/FONT] items. I didn't add any Hardware mixing, as this seems only to confuse Wine more. Also, check the **Enable Push-To-Talk hotkey (PTT mode)** checkbox. *THIS MEANS that whenever you want to talk to someone, the system works like a C.B. system: push the bound key (you may choose which one in the textbox below this option) and while it is pressed talk into the mic. Once you're done, let go the key. I suggest you choose a key you don't use in-game. I use the **#** key.*[/LIST]
[LIST]Finally, set the codec to GSM 6.10. Use whichever format you wish: the further down the list, the better sound you get and the more bandwidth you use up. You can use the monitor button to see if your mic works.[/LIST]
You should try and connect with your friends to a server before connecting  in-game. Also, this has proven to work with my PC, yet my Eve-Online game client is full-screen -- so make sure you can setup your game to be windowed if you know you'll need access to the Ventrilo setup.

This is my first real HOWTO, so I hope this helps. Please let me know if it works for you or if you have problems. Have fun!

**[COLOR="Red"]Note:[/COLOR]** if you need more references, here are the sites I used:
[list][http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832")[/list]
[list][http://slinux.net/how-to-install-ventrilo-2-3-on-linux]("http://slinux.net/how-to-install-ventrilo-2-3-on-linux") *(site is hard to get through to - try [Google's cached version]("http://64.233.169.104/search?q=cache:gY9mdl9DF9kJ:slinux.net/how-to-install-ventrilo-2-3-on-linux+slinux+ventrilo&hl=en&ct=clnk&cd=1&gl=ca&client=firefox-a")*[/list]
[list][http://www.codeweavers.com/compatibility/browse/name/?forum=1;app_id=413;mhl=4190;msg=3469]("http://www.codeweavers.com/compatibility/browse/name/?forum=1;app_id=413;mhl=4190;msg=3469")[/list]

---

### Post by ShadowApex on 2008-09-22
I followed all parts of this howto and am now still getting an error in Ventrilo: "Codec initialization failed: Unable to find the specific codec."

I've added the msgsm32.acm file to the system32 path and edited my system.ini but the problem persists.

Any thoughts?

---

### Post by naesa on 2008-10-07
Great guide. Would love it if someone can add howto get Ventrilo running with wine on a 64-bits edition of Ubuntu.

---

### Post by Kemon on 2008-10-07
It's just the same. I have 64bit ubuntu and just followed the guide.
It's working!  Finlay <3
But I dont know how I can speek to somebody when I dont have ventrilo active, marked (minmized)

---

### Post by MikeEx on 2008-10-10
Confirming this guide works for 64-bit.

Even on Intrepid 8.10 beta.
Thanks!

Edit: PTT hotkey doesn't work unless ventrilo is the active window

---

### Post by evilpig on 2008-10-29
> **ShadowApex said:**
> I followed all parts of this howto and am now still getting an error in Ventrilo: "Codec initialization failed: Unable to find the specific codec."

I've added the msgsm32.acm file to the system32 path and edited my system.ini but the problem persists.

Any thoughts?

To make it work for me, I needed to put that line under the other ones.

msacm.imaadpcm=imaadp32.acm
msacm.msadpcm=msadp32.acm
msacm.msg711=msg711.acm
msacm.winemp3=winemp3.acm
**MSACM.msgsm610=msgsm32.acm**

I still cant get my mic working. any tips?

---

### Post by TVMA on 2008-11-04
Has anyone figured out how to get it working with the hotkey when you are in the game?

---

### Post by TimothyLuke on 2008-11-04
I am running Wine + WOW + Vent on 8.04 64 bit.  One of the things I have noticed that may be of use is that provided I start WOW and Vent via the exact same method, I can use the PTT key when either WOW or Vent has focus.

If is start Vent like: padsp wine ventrilo.exe
then I also need to start WOW like: padsp wine WoW.exe

or eg2:
If is start Vent like: wine c://Program\ Files//Ventrilo//ventrilo.exe
then I also need to start WOW like: wine c://Program\ Files//World\ of\ Warcraft//WoW.exe

In 64bit Ubuntu this seems to *just work* however I haven't run a 32bit Linux for a while to test it with.  In my case I have put both into the GNOME Games Menu and run them from there.

---

### Post by btallas on 2008-11-23
Sorry for bumping a fairly old thread but can Ventrilo only work with Alsa?  I cannot use Alsa at all as the sound is very bad in WoW.  OSS works great for WoW but when switching to Alsa and testing in winecfg, it locks up the window.  When starting Ventrilo, I still get "Codec initialization failed: Unable to find the specified codec.".  I get that even if I switch to Alsa (even though it doesn't work) in winecfg.  Any other tips?

---

### Post by Ficus on 2008-11-24
I having an odd issue with Ventrilo right now.  That is, if the vent server is using the GSM codec, everything works perfectly, but if it's using Speex, everything comes out very static-y and garbled, so no one can understand me, but I can hear everyone perfectly.  This happens on several different mics, so I know that's not the problem.

I've searched for this several different ways, but to no avail - does anyone else have issues with this, or is it just me?

---

### Post by volcanus on 2008-12-08
Hello

I'm pretty new to Ubuntu and I'm trying to run both WoW and ventrilo under wine. 

I've installed ventrilo and followed your HOWTO but I still get the error.
Does someone have some answers for me? :)

---

### Post by TVMA on 2008-12-10
> **volcanus said:**
> Hello

I'm pretty new to Ubuntu and I'm trying to run both WoW and ventrilo under wine. 

I've installed ventrilo and followed your HOWTO but I still get the error.
Does someone have some answers for me? :)

Can you post the error that you are getting?

---

### Post by volcanus on 2008-12-11
sorry I forgot to post it :P
this is what I'm getting when I connect

```
Unable to initialize outbound codec (GSM 6.10 - 44100 Hz, 16 bit): Unable 
to find the specified codec.
```

Edit: *I found it. In the system.ini file I wrote msacm in stead of MSACM. small difference between the caps but since linux is case sensitive I should've known *

---

### Post by Zackie on 2008-12-22
That is my system.ini file. I have the msgsm32.acm in my system dir tried it in my system32 and system32/drivers nothing is working so it seems get the same codec error when i start it up... any ideas?



[mci]

MPEGVideo=mciqtz.drv

MPEGVideo2=mciqtz.drv

avivideo=mciavi32.dll

cdaudio=mcicda.dll

sequencer=mciseq.dll

vcr=mcivisca.drv

; videodisc=mcipionr.drv

waveaudio=mciwave.dll



[drivers32]

msacm.imaadpcm=imaadp32.acm

msacm.msadpcm=msadp32.acm

msacm.msg711=msg711.acm

msacm.winemp3=winemp3.acm

vidc.mrle=msrle32.dll

vidc.msvc=msvidc32.dll

vidc.cvid=iccvid.dll

; vidc.IV50=ir50_32.dll

; vidc.IV31=ir32_32.dll

; vidc.IV32=ir32_32.dll
MSACM.msgsm610=msgsm32.acm

EDIT---Okay I restarted and it randomly works now... Although.. While hearing them my PTT some times will not work and sometimes it will while the app Is ON TOP or Behind other apps... It will work for a little bit but it seems once somebody says something it will not allow me to speak again.. Using ALSA too..

---

### Post by weazx on 2009-01-26
I just tried installing Ventrilo on 8.1 -64 bit, and there does not seem to be an .exe file.  I tried re-downloading and re-installing a couple times, but no luck.  Can anyone help, or maybe just host the 64-bit .exe file somewhere?  

Unless I missed something in the guide...

Thanks.

---

### Post by Robert98374 on 2009-02-13
Heya Guys!

I got vent installed Etc, i can hear everyone fine, but vent cant seem to pick up my Mic at all :(

What might be the process for me to troubleshoot?

---

### Post by btallas on 2009-02-14
I've uninstalled anything related to pulsaudio.  I'm now running straight ALSA.  Finally have my mic working (tested through sound recorder).  I'm still unable to load the GSM 6.10 codec.  I've searched and tried everything on ubuntuforums and on appdb.winehq.org and nothing is working for me.  I copied over my msgsm32.acm from my vista partition and input the setting in the system.ini (with fully qualified path and without, also with MSACM in caps or lower case).  Nothing is letting me find this codec.  All the "use direct sound" boxes are checked.  All events are wave file (not text to speach).  As soon as I hit test when choosing the codec in ventrilo setup, I get the error "Codec initialization failed: Unable to find the specified codec.".  When I connect to the vent server, I get the following error:

Failed to get encoder for specified Codec.

Unable to initialize outbound codec (GSM 6.10 - 11 KHz, 16 bit): Unable to find the specified codec

I don't know why it's defaulting to the 11KHz, 16 setting.  I choose 8 KHz, 16 bit setting but it's never saved.  The audio is also crackly when I connect (if that makes sense).  Nothing else on my system has the crackly audio.  Anyone have any other clues?

OK, got it working by downloading the msgsm32.acm from the link and using it instead of the one from my vista partition.  I still have the crackly audio but I can hear people, they just can't hear me.  I believe I can get that fixed as I've see that issue from other posts.

---

### Post by lyghtkruz on 2009-03-06
Greetings!  I've been using linux for a few years but Ubuntu for a few months. I'm running the 32bit Wine (1.16) and Ventrilo(3.0.4). 

**Background** 
     I've installed Wine and Ventrilo successfully and removed pulse audio as it was causing my sound to go away after running the OS for a few days.  Eve Online and World of Warcraft work normally for the most part except the various crashing issues which I'm told is due to the 32Bit version of Wine not being able to handle the upper parts of the 4GB of RAM on my system. 

**Issue**
     On Ventrilo, I can hear everyone speaking normally but when I use the PTT key, nothing happens (The keybinding noise is not heard and my speaker on ventrilo does not turn green).  I've tried changing the PTT key to many other keys and none of them respond.  On other systems without a Mic, the speaker at least goes green.  My mic is recognized by my OS, but Ventrilo doesn't appear to recognize the PTT or MIC without the PTT key. (I've done the obvious, like Unchecking the Use Direct Input for the PTT Key)

**More Info**
I do have a 32Bit version of Ubuntu and it appears to work properly on my laptop.  I'm assuming it has to do with running the 64Bit OS with the 32Bit Wine/Ventrilo.

**Thanks!**
     If anyone has any insight on this, I would greatly appreciate it. 

-Kruz

-------
**Update April 10 2009. **

So I have made little progress.  

If I run wine with ALSA it recognizes some PTT keys, but it does not work with LEFT CTRL.  

If I run wine with both ALSA and OSS it does not recognize any PTT keys.    

If I use OSS, it recognizes all PTT keys and recognizes the INPUT device and I'm able to talk to people.  But I can't hear anyone. 

If I use AOSS to run winecfg and use "OSS" I have managed to get Ventrilo working properly once, but as soon as I try to launch any other application.  It doesn't have sound.  If I launch other applications before Ventrilo, it will tell me the sound device is in use. 

(*A BS Work around.  If I Run winecfg with AOSS and get one copy of ventrilo working where everyone can hear me, I run a separate Ventrilo using ALSA where I can hear everyone.  I mute myself on one copy so I don't get my own feed back.  This is annoying, and has to be set up pretty much any time you want it to work so I don't bother with it.  Sometimes I get the device is busy when I try this work around, and it seems to only work after a reboot.  I don't like rebooting any linux distribution, unless I'm compiling a kernel.*)

These issues are on Ubuntu 64 bit. The Audio is onboard Intel HD Audio.

The headset I was/am trying to use is a USB creative labs Fata1ty headset. Wine only seems to be able to detect it if I'm using OSS (In Ventrilo).

I ran all the Updates on my laptop so at least I would be running the same version of all the software.  I'm using a built-in audio and using the AOSS trick.  The only way Ventrilo works without focus is to make Wine run a "virtual desktop" and then it will work with any applications running inside the virtual desktop.  If you get out of the virtual desktop, it doesn't work. At least, not for me.

I've read many posts that say to just buy a new sound card because the onboards don't seem to work.  Well seeing as how my desktop doesn't have any available PCI-Slots, I'm SOL there.

---- Update 4-15-08
I resolved my issues... I HOPE.. *crosses fingers* 

I used padsp winecfg and unchecked Alsa and checked only OSS.  Now my Ventrilo recognizes the USB Mixer which is my headset and I am able to set it properly in ventrilo.  PTT still does not work if you are not in the same "desktop" or have ventrilo on Focus. 

I didn't try this before because PulseAudio causes my system to lose sound completely since Ubuntu Fiesty 7.04.  Multiple systems same issue.  My sound goes out and only a restart will fix it.

---

### Post by davenpro on 2009-03-08
If you're running wine 1.1.14 or newer there is a bug that prevents the GSM codec from working properly (Speex still works however).  For details on this and a patch to fix the issue see:

[http://bugs.winehq.org/show_bug.cgi?id=17397](http://bugs.winehq.org/show_bug.cgi?id=17397)

---

### Post by ResumeMan on 2009-03-31
> **lyghtkruz said:**
> 

[...]
     On Ventrilo, I can hear everyone speaking normally but when I use the PTT key, nothing happens (The keybinding noise is not heard and my speaker on ventrilo does not turn green).  I've tried changing the PTT key to many other keys and none of them respond.  On other systems without a Mic, the speaker at least goes green.  My mic is recognized by my OS, but Ventrilo doesn't appear to recognize the PTT or MIC without the PTT key. (I've done the obvious, like Unchecking the Use Direct Input for the PTT Key)

[...]



Hi all, 

I am in exactly the same boat. I'm not getting any codec errors, etc, and I can hear others fine, but Vent doesn't acknowledge my PTT key at all, whether or not Vent is in focus. Note that in the setup tab when I click in the hotkey window it DOES recognize that I have entered the key. But it doesn't register to actually transmit the mic.

I'm running a S76 Pangolin with Intrepid 64 bit. I have NOT disabled or otherwise played with PulseAudio. I'm willing to go there, but this doesn't feel like a sound issue, it feels like a keyboard input issue.

Thanks if anyone can help.

---

### Post by coolno9 on 2009-04-14
> **ResumeMan said:**
> Hi all, 

I am in exactly the same boat. I'm not getting any codec errors, etc, and I can hear others fine, but Vent doesn't acknowledge my PTT key at all, whether or not Vent is in focus. Note that in the setup tab when I click in the hotkey window it DOES recognize that I have entered the key. But it doesn't register to actually transmit the mic.

I'm running a S76 Pangolin with Intrepid 64 bit. I have NOT disabled or otherwise played with PulseAudio. I'm willing to go there, but this doesn't feel like a sound issue, it feels like a keyboard input issue.

Thanks if anyone can help.

first if you haven't already type in a terminal
```

sudo killall pulseaudio

```

then go into your ventrilo settings and disable play key clicks.  that's all i did to get it working, if that doesn't work make sure your mic works in other ubuntu programs.

Now if someone could make the speex codec not static-y anymore I would be happy :D

---

### Post by Nessa on 2009-04-28
> **evilpig said:**
> To make it work for me, I needed to put that line under the other ones.

msacm.imaadpcm=imaadp32.acm
msacm.msadpcm=msadp32.acm
msacm.msg711=msg711.acm
msacm.winemp3=winemp3.acm
**MSACM.msgsm610=msgsm32.acm**

Worked like a charm! Thanks!

---

### Post by creess1 on 2009-04-29
i have no idea how to fix this.  i can hear myself in my headset when i speak into my mic, so i know its "working", but when im in vent they cant hear me.  I can hear them, and i can hear myself.

Funny thing is i hear myself all the time, not just when i push the PTT button, and i have PTT enabled.

Also PTT doesnt seem to work unless vent is the active window.  

Can anyone help?  Ive already installed that msgsm32.acm file into the system folder, the system32 folder as well as the windows folder.  And i put the entry into the system.ini file.  I tried the line before and after all the other entries, neither way changed a thing.

I uninstalled vent, then reinstalled from scratch.  Still same problem.

Should i be using OSS or ALSA?  or something different or a combination of things?  What settings should i have in vent?  Please be specific, ive never set this up before on a linux distro. 

Under wine configuration in the applications tab, what should the windows version be set to?  I set it to winxp because thats what version of vent i downloaded and installed, the 32bit version. 

Things i need resolved.  Change the mic so it only records when i hit the PTT, not all the time.  Make the PTT button work when Vent is not the active window, and make it so other people can hear me when i do hit the PTT button and talk.

EDIT:  right now im getting this error in vent:  "Failed to open input device. Another program might have it open already. rc = -10"

---

### Post by risingsun on 2009-05-05
Would anyone know if it's possible to retrieve the msgsm32.acm file from a windows CD? I have my old CD for Windows XP but I don't have it currently installed and I don't want to have to install it solely for a single file. However examining the CD only reveals msgsm32.AC_ and  doubt simply renaming it would work. :)

---

### Post by risingsun on 2009-05-19
Well, for some odd reason I had this working in the past but since I recently blitzed my .wine folder and reapplied the instructions from this thread it no longer wants to run, providing the initialization error that others have had in this thread. (Running wine 1.1.21 and Jaunty, but I was running that setup yesterday when it was still working.)

However, I did notice that there appears to be no mention of msgsm610 in the registry, which it does have in a backup of the old reg file. I don't want to copy the reg file straight across (more trouble than it's worth) but I would like to know if people know of where the relevant registry entries should be/a way to force a check on the system.ini file that might add these lines to the registry? I'm thinking this lack of registry entries is what's behind Ventrilo's inability to find the acm file.

Thanks in advance. :)

---

### Post by m0rbidpercepti0ns on 2009-11-11
My issue is that..i cant hear anyone at all. Vent connects fine,and appears to be working..except i cant hear anyone. I dont have a mic,and dont care about being heard,i only want to hear so i can know whats going on...previously vent has ALWAYS worked for me,without anything being done to it. I didnt have to get that M$ file,or edit system.ini. I have added the file,and the line to System.ini,since Vent stopped working,still no luck. Everyones vent issues seem to start with "I can hear everyone fine,but..." Does anyone know of a solution? Any help is GREATLY appreciated.

---

### Post by ekilfoil on 2009-11-12
> **m0rbidpercepti0ns said:**
> My issue is that..i cant hear anyone at all. Vent connects fine,and appears to be working..except i cant hear anyone. I dont have a mic,and dont care about being heard,i only want to hear so i can know whats going on...previously vent has ALWAYS worked for me,without anything being done to it. I didnt have to get that M$ file,or edit system.ini. I have added the file,and the line to System.ini,since Vent stopped working,still no luck. Everyones vent issues seem to start with "I can hear everyone fine,but..." Does anyone know of a solution? Any help is GREATLY appreciated.

The solution is to use a version of Wine that supports PulseAudio:

[https://launchpad.net/~neil-aldur/+archive/ppa](https://launchpad.net/~neil-aldur/+archive/ppa)

And use a Ventrilo client that supports PulseAudio:

[http://www.mangler.org](http://www.mangler.org)

Ubuntu really needs to distribute a version of Wine with PulseAudio support by default.

---

### Post by m0rbidpercepti0ns on 2009-11-16
> **ekilfoil said:**
> The solution is to use a version of Wine that supports PulseAudio:

[https://launchpad.net/~neil-aldur/+archive/ppa]("https://launchpad.net/%7Eneil-aldur/+archive/ppa")

And use a Ventrilo client that supports PulseAudio:

[http://www.mangler.org](http://www.mangler.org)

Ubuntu really needs to distribute a version of Wine with PulseAudio support by default.



Ok,the problem with your solution is this A.Im using the most current version of wine,and Vent was working fine,and suddenly stopped without me changing anything. B.Im aware of Mangler,but theres no beta release,or stable release,so that really isnt an option until one is released. And C. Ubuntu/Cannocal doesnt produce Wine,they simple direct people to it because it usualy works. Also..i know the problem isnt Wine,because although i dont enable sound on WoW,i did to see if it would work,and it does.

---

### Post by joeelmex on 2009-11-16
Actually I think Mangler just released a stable client.

---

### Post by GeoPirate on 2009-11-16
I confirm the Mangler, the release client was released last week, and it works better for me than vent ever did, and I didn't have to tweak anything, just install it and good to go. They even have a .deb file on there so it's 2 clicks to install.

---

### Post by ekilfoil on 2009-11-17
> **m0rbidpercepti0ns said:**
> B.Im aware of Mangler,but theres no beta release,or stable release,so that really isnt an option until one is released.

RC1 was released last Friday

> And C. Ubuntu/Cannocal doesnt produce Wine,they simple direct people to it because it usualy works.

The deafult WINE distribution does not ship a version that uses PulseAudio.  Ubuntu ships the default version.  The PPA version I linked includes PulseAudio support.  For a more detailed explanation, go here: [http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=5.0](http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=5.0)

---

### Post by Vistz on 2010-04-18
Does this work with karmic?

---

### Post by dardack on 2010-04-24
> **Vistz said:**
> Does this work with karmic?

Mangler? or vent?

---

### Post by KEE on 2011-04-17
to op: your links to ```
msgsm32.acm
``` is dead and one is asking for credit cards and paypal payments....

---

### Post by yallbugin on 2011-09-23
Did anybody ever figure out hot to get vent working when its not in focus? mine has been working fine since install, but i hate having to switch out of something just to respond

---

### Post by Tweak42 on 2011-09-24
> **yallbugin said:**
> Did anybody ever figure out hot to get vent working when its not in focus? mine has been working fine since install, but i hate having to switch out of something just to respond

AFAIK [Mangler]("http://www.mangler.org/") works fine with 3.0.x vent servers.  Is there a specific reason you need to run vent on wine?

---

