---
title: "How do I get x64?"
date: 2009-05-10
forum: x86 64-bit Users
---

### Post by Yemmo2008 on 2009-05-10
I'm runnig 9.04. I typed the command 'uname -a' into the terminal and it came up with 

"Linux conor-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux"

Does this mean I've got x86 or x64? If so how do I get x64?

---

### Post by Yemmo2008 on 2009-05-10
Just browsed the forums a bit more. Turns out the edition I ordered was x86.

---

### Post by Idefix82 on 2009-05-10
You can download the 64 bit image from the Ubuntu website. Make sure your computer architecture is 64 bit. How much RAM do you have?

---

### Post by sanderj on 2009-05-10
> **Idefix82 said:**
> You can download the 64 bit image from the Ubuntu website. Make sure your computer architecture is 64 bit. 

You can check your CPU's bitness with
```
grep ' lm ' /proc/cpuinfo
```
If that command gives output, your CPU is 64-bit.

After downloading the 64-bit Ubuntu version, you should reinstall 64-bit Ubuntu.

---

### Post by Yemmo2008 on 2009-05-11
I've got an Intel core2 Quad 8200 4 gigs of 1066mhz ram. I'm certain It's 64 bit hardware as I'm running vista 64 bit. I just downloaded the x64 version but it had an error so I'm going to write the cd again.

---

### Post by stchman on 2009-05-11
> **Yemmo2008 said:**
> I've got an Intel core2 Quad 8200 4 gigs of 1066mhz ram. I'm certain It's 64 bit hardware as I'm running vista 64 bit. I just downloaded the x64 version but it had an error so I'm going to write the cd again.

Perfect for running 64 bit OS.

---

### Post by cybrsaylr on 2009-05-11
You can download the 64 bit image from the Ubuntu website.
I did the same, then burned it to disc, then installed it on my laptop.

Only problems so far is Adobe Flash won't run and I can't play mp3s as I do with my desktop running 32bit 9.04.

32bit 9.04 plays both Adobe and mp3s with no problems.

---

### Post by oldos2er on 2009-05-11
[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html) should get 64-bit Flash working.

---

### Post by jespdj on 2009-05-11
> **cybrsaylr said:**
> Only problems so far is Adobe Flash won't run and I can't play mp3s as I do with my desktop running 32bit 9.04.
Really, why not? Adobe Flash runs normally on 64-bit Jaunty, exactly the same as on 32-bit Jaunty.
```
sudo apt-get install flashplugin-nonfree
```
Also, ofcourse you can play MP3s, but you do need to have the right codecs installed. Install w64codecs from [Medibuntu](http://www.medibuntu.org).

---

### Post by cybrsaylr on 2009-05-11
> **jespdj said:**
> Really, why not? Adobe Flash runs normally on 64-bit Jaunty, exactly the same as on 32-bit Jaunty.
```
sudo apt-get install flashplugin-nonfree
```
Also, ofcourse you can play MP3s, but you do need to have the right codecs installed. Install w64codecs from [Medibuntu](http://www.medibuntu.org).
jespdj,
Thanks.
Got Flash running on Firefox but it's still a little balky with Opera browser.
Opera plays some video but wont play UTube video clips for some reason.

Just installed the mp3 64bit codecs from the repos. Funny they were listed today but when I checked the other day there were none available in the repos???

Mp3s play fine now.

---

### Post by Yellow Pasque on 2009-05-11
jespdj,
w64codecs has nothing to do with MP3's.  w64codecs only contains 3 shared libraries for Mplayer that can't be distributed because they're owned by RealNetworks.
For example:
cook.so: [http://en.wikipedia.org/wiki/Cook_Codec](http://en.wikipedia.org/wiki/Cook_Codec)

---

### Post by jespdj on 2009-05-12
Ok, sorry... here are instructions: [How to install MP3 playback in Ubuntu](http://www.psychocats.net/ubuntu/mp3).

---

### Post by Yomny on 2009-05-12
If i install an application like advant window nagivator and im not sure if its 32/64 bit should i run getlib first, or is getlibs something you run/install once?  thanks

---

### Post by sanderj on 2009-05-12
> **Yomny said:**
> If i install an application like advant window nagivator and im not sure if its 32/64 bit should i run getlib first, or is getlibs something you run/install once?  thanks

Just install software via Add/Remove Programs (or "sudo apt-get install <package name>", and Ubuntu will take care of it all. No worries.

---

### Post by Yomny on 2009-05-12
so add/remove then look for the download application? I already have it download to a folder?  When you say to enter the name of the application in the terminal you mean the whole name of the application just as it appears in the folder that i downloaded it to?  thanks a lot

---

### Post by sanderj on 2009-05-12
> **Yomny said:**
> so add/remove then look for the download application? I already have it download to a folder?  When you say to enter the name of the application in the terminal you mean the whole name of the application just as it appears in the folder that i downloaded it to?  thanks a lot

No. Do not download files yourself. Let Ubuntu take care of that. Just go to Add/Remove Programs and select what you want to install. Ubuntu will then take care of it.

---

### Post by Yomny on 2009-05-12
so ubuntu knows or can find every and any application out there.  Is the add/remove software any good or is there any other that i should use to install applications i find online.  If i go through terminal, how will i know that im typing the correct name of the file?  thanks

---

### Post by sanderj on 2009-05-12
> **Yomny said:**
> so ubuntu knows or can find every and any application out there.  Is the add/remove software any good or is there any other that i should use to install applications i find online.  If i go through terminal, how will i know that im typing the correct name of the file?  thanks

Ubuntu has about 25.000 pacakages in it's repository. See the exact number in the bottom line of the Synaptic screendump. I think 25.000 is asymptoticly close to "every and any".

If you want to install 'avant' (note the spelling), go to Add/Remove Programs, make sure you have selected All Available Applications, and type in 'avant'. Ubuntu will find it for you. Then confirm you want to install.

If something is not in the standard repository, check the PPA repository (see [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)).

My rule of thumb: if software is not in one of the Ubuntu repositories, try to find an alternative that *is* in the repository. It will save you a lot of trouble.

---

### Post by stchman on 2009-05-12
> **cybrsaylr said:**
> You can download the 64 bit image from the Ubuntu website.
I did the same, then burned it to disc, then installed it on my laptop.

Only problems so far is Adobe Flash won't run and I can't play mp3s as I do with my desktop running 32bit 9.04.

32bit 9.04 plays both Adobe and mp3s with no problems.

64 bit will do Flash 10 and MP3 no problem.

CODECs
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Flash 10
[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

The flashplugin-nonfree package is 32 bit, use my procedure to get a true 64 bit plugin.

---

### Post by Artemis3 on 2009-05-13
> **cybrsaylr said:**
> Only problems so far is Adobe Flash won't run and I can't play mp3s as I do with my desktop running 32bit 9.04.

32bit 9.04 plays both Adobe and mp3s with no problems.

You fix mp3 and flash the same way you do with 32 bits: Install the package: **ubuntu-restricted-extras**

But now flash has something better, there is a 64 bits beta version in their page, so you can now remove the flash ndiswrapper packages, download the beta and put the .so in your ~/.mozilla/plugins folder.

I would advise you guys to stop using the term "x64". That architecture does exist, and its not the one you think... It is the abandoned Itanium 64 bits architecture Intel tried before AMD made their 64 bits x86 extension, which Intel later adopted as EMT64. The kernel correctly uses: "x86_64". See the difference?

---

