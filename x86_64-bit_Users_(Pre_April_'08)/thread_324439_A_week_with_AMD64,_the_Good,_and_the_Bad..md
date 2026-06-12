---
title: "A week with AMD64, the Good, and the Bad."
date: 2006-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Brian Boyko on 2006-12-23
A week with Ubuntu AMD 64:

The Good:

[LIST]
[*]Installation was beyond easy. 
[*]Ubuntu notifies me of updates to all my software, like Apple's System Checker but much more powerful.  
[*]The Add-Remove Programs menu absolutely rocks; Windows could benefit from something like this (the existing solutions aren't nearly as powerful.) 
[*]I have had absolutely ZERO problems installing or connecting new hardware.  Everything I have just simply works; hardware compatibility and drivers aren't an issue.  There's less hand-holding (read: pop-up wizards) than in XP, but I didn't have a problem doing without.  
[*]AbiWord, so far, works great for word processing. 
[*]Watching Xvid files works perfectly.
[/LIST]

The Bad:

[LIST]
[*]The system hung on the reboot after installation, but a hard reset resulted in a clean Ubuntu system. 
[*]After running the system updater, the Gnome menu did not respond to mouse clicks and I had to reboot the system.  
[*]The Microsoft Fonts simply failed to install, no matter what I did. 
[*]I could only get my Samsung SyncMaster 204B to run at the native resolution of 1600x1200 by running "sudo dpkg-reconfigure -phigh xserver-xorg" - a command I only found by editing xorg.conf by hand; something that Granny should never have to do.  
[*]Obviously, Macromedia Flash does not work; I did not realize how much of the Web used Flash until I was forced to do without it.  Particularly, Google Analytics and YouTube both use flash. 
[*]I couldn't get DVDs working through Totem no matter what I did.  I did have success playing them in Ogle.  
[*]Using AcidRip, I was able to rip the movie to H.264 and Xvid formats, but the audio did not sync up to the video.  
[*]The computer refuses to boot if either my SanDisk Cruzer Titanium 2.0gB flash drive or 80 Gig USB external hard drive is connected.  
[*]I was able to get MP3s to play in Rythembox, but getting it to rip from CD from Rythembox was a chore; something I was only able to do with the help of "Ubuntu Linux for Non-Geeks"
[*]My Logitech Precision joypad is detected and works in SuperTux but I cannot figure out how to configure the buttons to my liking - I can't figure out how to configure them at all in GFCE NES emulator and GSNES9X.
[*]Kino cannot be used to control my DV camera - like it can in iMovie and to a much more limited extent in Windows Movie Maker.
[*]Kino crashed and was unstable.  When it did export DV to Xvid, the file simply failed to materialize on my hard drive; additionally, closing Kino does not close down the Mencoder processes - I had quite a few of them running when Kino crashed a couple of times, and when I closed down Kino. This threw my system load through the roof.  I had to end them manually.  
[*]Frostwire says my Java version is 1.4.2.-02 when I try to install it (which is too old for Frostwire to use) and Add/Remove says I've got 1.5.0-08-0ubuntu1 installed.  Is this version of Java simply not supported on AMD64?
[/LIST]

---

### Post by killkoy on 2006-12-23
> **Brian Boyko said:**
> Obviously, Macromedia Flash does not work; I did not realize how much of the Web used Flash until I was forced to do without it.  Particularly, Google Analytics and YouTube both use flash. 
I couldn't get DVDs working through Totem no matter what I did.  I did have success playing them in Ogle.  

for the flash problem you could try [this]("http://www.ubuntuforums.org/showthread.php?t=202537&highlight=firefox+32+howto") guide
or use [Nspluginwrapper]("http://www.ubuntuforums.org/showthread.php?t=277077")

I had the same problem with dvds, I solved it by using a xine backend for totem
```
sudo aptitude install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 totem-xine
```, it should ask to remove totem-gstreamer, this is fine (what we want)

---

### Post by Azakus on 2006-12-23
Try IceWeasel32, it is a 32bit browser built for the 64 bit OS that will work with Java, Flash, and video.

---

### Post by BIGtrouble77 on 2006-12-23
I suggest using automatix2 ( [www.getautomatix.com](www.getautomatix.com) ).

It will resolve a bunch of your problems.

---

### Post by Brian Boyko on 2006-12-24
> **killkoy said:**
> for the flash problem you could try [this]("http://www.ubuntuforums.org/showthread.php?t=202537&highlight=firefox+32+howto") guide
or use [Nspluginwrapper]("http://www.ubuntuforums.org/showthread.php?t=277077")

I had the same problem with dvds, I solved it by using a xine backend for totem
```
sudo aptitude install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 totem-xine
```, it should ask to remove totem-gstreamer, this is fine (what we want)

Killkoy, that worked like a charm.

---

### Post by pay on 2006-12-24
> **Azakus said:**
> Try IceWeasel32, it is a 32bit browser built for the 64 bit OS that will work with Java, Flash, and video.Why not firefox? If you use IceWeasel because the firefox artwork isn't open, then why use flash and java? You could always use gnash and blackdown java (closed source) with amd64 if needed.

---

### Post by Brian Boyko on 2006-12-24
> **BIGtrouble77 said:**
> I suggest using automatix2 ( [www.getautomatix.com](www.getautomatix.com) ).

It will resolve a bunch of your problems.

I've had mixed luck with Automatix but on your advice, I went back and was able to use it to get the latest version of Java, and that worked.

---

### Post by Azakus on 2006-12-24
> **pay said:**
> Why not firefox? If you use IceWeasel because the firefox artwork isn't open, then why use flash and java? You could always use gnash and blackdown java (closed source) with amd64 if needed.

I like Iceweasel. That's about the only reason I use it over Firefox. Also, gnash and blackdown have been REALLY buggy for me in the past, so I've decided to wait on them until I feel they are ready to replace the proprietary programs.

---

### Post by Brian Boyko on 2006-12-24
Okay.  Here's the deal.

I downloaded the Iceweasel .deb package.  It installs fine but launching it launched Firefox instead... I uninstall Firefox, only to find out that uninstalling firefox also uninstalls ubuntu-desktop, which includes Add/Remove programs.  

It seems I could use a step-by-step approach.  And yes, I would prefer to use Firefox instead of IceWeasel; I'm not picky about my software from a "freedom" perspective, I'm looking at it from an end-user, productivity perspective.

---

### Post by Azakus on 2006-12-24
You have to make the default browser Iceweasel. It can be done with a simple script.
```
sudo rm /usr/bin/firefox
sudo ln -s /usr/local/Iceweasel32/iceweasel /usr/bin/firefox
```

---

### Post by kuja on 2006-12-24
> **Brian Boyko said:**
> A week with Ubuntu AMD 64:]
[*]The Microsoft Fonts simply failed to install, no matter what I did. 
You were trying to install the msttcorefonts package from multiverse? or no? If it gave you trouble, try switching mirrors. It never gave me trouble before.

> **Brian Boyko said:**
> A week with Ubuntu AMD 64:]
[*]Obviously, Macromedia Flash does not work; I did not realize how much of the Web used Flash until I was forced to do without it.  Particularly, Google Analytics and YouTube both use flash.
You can pick up a reasonably recent version of flash here: [http://labs.adobe.com](http://labs.adobe.com), download the zip file, extract it, and put libflashplayer.so in you ~/.firefox/plugins folder. It's certainly not the fault of Ubuntu that support from closed source vendors has been so slow. 

> **Brian Boyko said:**
> A week with Ubuntu AMD 64:]
[*]I couldn't get DVDs working through Totem no matter what I did.  I did have success playing them in Ogle.
Try totem-xine if you like totem. It might have better luck, else, use something else. 
 
> **Brian Boyko said:**
> A week with Ubuntu AMD 64:[*]The computer refuses to boot if either my SanDisk Cruzer Titanium 2.0gB flash drive or 80 Gig USB external hard drive is connected.
[http://launchpad.net](http://launchpad.net) ... things like this need to be reported. Bugs like these need to be squashed.

> **Brian Boyko said:**
> A week with Ubuntu AMD 64:[*]Frostwire says my Java version is 1.4.2.-02 when I try to install it (which is too old for Frostwire to use) and Add/Remove says I've got 1.5.0-08-0ubuntu1 installed.  Is this version of Java simply not supported on AMD64?

You need to reconfigure ubuntu to use Sun Java instead of GCJ. Pull up a terminal and type in ```
sudo update-alternatives --config java
``` and select the sun jvm.

---

### Post by Brian Boyko on 2006-12-24
Still have no luck installing flash even with what I'm presuming to be the 32 bit version of firefox.

---

### Post by pay on 2006-12-24
> **Brian Boyko said:**
> Okay.  Here's the deal.

I downloaded the Iceweasel .deb package.  It installs fine but launching it launched Firefox instead... I uninstall Firefox, only to find out that uninstalling firefox also uninstalls ubuntu-desktop, which includes Add/Remove programs.  I believe that Ubuntu-desktop is just a meta package. And to use iceweasel you must have every instance of firefox closed.

---

