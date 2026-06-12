---
title: "Gutsy 64-bit - First impressions"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by scourge on 2007-10-19
I was a happy user of Feisty 64-bit, and decided to do a clean install of Gutsy. Here's how it went. Please note that most of the things I say probably apply to 32-bit Gutsy as well, but I can't be sure so I post this here.


1. Installation

I booted from the Live CD and selected "Start or Install Ubuntu". Damn, no boot splash, the whole thing freezes. I had the same problem with Feisty, so I knew that I could get around this by disabling the splash. Still, it's ridiculous that this bug in the 64-bit VESA driver still exists. From now on I'll have to edit /boot/grub/menu.lst every time I update the kernel, or else Ubuntu won't boot. We already have Bulletproof X, so how about Bulletproof boot next?


2. First boot

Ubuntu started nicely with the boot splash disabled. Restricted Manager suggested that I install the proprietary NVIDIA driver. I complied and rebooted.


3. Second boot

Ubuntu started again, but this time with the fancy desktop effects enabled. Cool. I tried playing some MP3 files: Ubuntu found the right codecs right away, and I was in business. Next I tried VMW videos, which also played after some codecs were installed. Matroska HD videos played like crap though, so I needed a better video player. Installed MPlayer from the repos, but the damn thing would just segfault right away. So I decided to do what any Windows user would do; reboot.


4. Third boot

Tried MPlayer right away, and now it worked! Dunno why, but I don't care. Now I started to get annoyed by the tearing in videos and moving application windows. I knew it was because of disabled/incorrect Sync To VBlank settings. The right way to solve this was to disable Sync To VBlank (both XV and OpenGL) in nvidia-settings, and enable it in Compiz Fusion settings. Of course nvidia-settings is still the only thing that correctly detects the refresh rate of my monitor, so I had to change that setting in Compiz Fusion config as well. Problem solved, although not without wasting some precious time.

Next I tried Firefox. The non-free 32-bit Flash plugin got installed in a painless fashion. The "improved" totem-mozilla plugin however didn't impress: The "Full Screen" option just gave me a new smaller video window. Not what I wanted. Once again Totem and its Mozilla plugin had to let Mplayer and Mplayer-plugin to take their places.

Then I wanted to play some Chess. glChess (included in Gnome by default) is nice but really insufficient for any serious chess player. But that's not a problem. What is, is that Ubuntu forces me to either have Gnome games OR Gnuchess, but not both. glChess actually uses Gnuchess as its AI, but it's not the same Gnuchess that's in the repos. Gnuchess is just a simple C application; it pretty much only depends on libc, and nothing depends on it. There should be no acceptable reason for this conflict.


5. Conclusion

I truly believe that I'm now using the best operating system ever made. But it became the best only after I had made the needed changes.

---

### Post by tomdkat on 2007-10-19
Here are my first impressions.   :)

Installation:

First, I upgraded from Feisty Fawn to Gutsy Gibbon using the network install via the update manager.  I exited all my apps and started the upgrade process.  It took FOREVER to download everything (I would say at least 8 hours) but I can understand that with Gibbon being a "hot" item right now.  :)  Once everything was downloaded, the upgrade went very smoothly. I was asked about replacing a couple of scripts that had changed when I was running Feisty Fawn (I turned off some daemons) but other than that, my disk spun for about 45-60 mins or so.

Then came reboot #1.  When the system came back up, I had the [same video problem](http://ubuntuforums.org/showthread.php?t=235849) I had last time I installed Ubuntu from scratch (even though I was upgrading this time).  I was informed my screen resolution was too low and asked if I wanted to configure my graphics adapter then.  I opted not to and got the login screen.  I then decided to go ahead and configure the graphics adapter, so I rebooted with the hope I would be prompted to do so again.  No dice. I got a garbled screen on the reboot.

Reboot #2:
The garbled screen was not well received by me, to say the least.  To make a long story short, I managed to login from the command line, replace the xorg.conf that had been generated with xorg.conf-failsafe, reboot and was able to login to GNOME.    I tried the ATI proprietry/restricted driver that came with Gutsy Gibbon but it didn't work, so I used the OpenSource one and it worked just fine.  That's what I'm using now.

Overall use:
So far, Gutsy Gibbon has been running fine for me, with the exception of the video issue above.  I got Firefox 3 (Gran Paradiso) installed along with Gnash and all that worked fine.  I haven't tried everything out yet, like VLC or any kind of audio file player or CD burner, so we'll see how things go over the next week or so.  Gutsy Gibbon "felt" faster than Feisty Fawn at first but I don't feel that now.  Or, maybe I've already adjusted to the new performance level.

Conclusion:
So far, I'm a happy camper.  I like having Gimp 2.4.0 (RC3).  :)

Peace...

---

### Post by steveneddy on 2007-10-19
Let's see:

I upgraded with the update-manager -d command and it went beautifully.

I upgraded Wednesday evening when there was no load on the servers.

After ironing out the firefox crash isue with flash, it runs great.

Best Ubuntu yet.

My Bluetooth mouse even connects and stays connected all day with no disconnects.

:popcorn:

---

### Post by go_beep_yourself on 2007-10-19
> **scourge said:**
> 

1. Installation

I booted from the Live CD and selected "Start or Install Ubuntu". Damn, no boot splash, the whole thing freezes. I had the same problem with Feisty, so I knew that I could get around this by disabling the splash. Still, it's ridiculous that this bug in the 64-bit VESA driver still exists. From now on I'll have to edit /boot/grub/menu.lst every time I update the kernel, or else Ubuntu won't boot. We already have Bulletproof X, so how about Bulletproof boot next?



Nonsense!!! You do not have to edit the menu.lst each time. Edit your menu.lst. It looks like this.

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```

Change it to this by deleting splash. I've removed both of those default options in mine.

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=
```

Now run sudo update-grub, and you never should have to edit it again.

---

### Post by crjackson on 2007-10-19
I gave it a test run today and I was very pleased.  The only problem I had was the same old splash screen problem that seems to be the trademark for ubuntu.

After I got past that, I was pleased to find that without a doubt, it is more responsive than 7.04.

Now even my printer(s) and scanner (which never worked under 7.04) are detected and installed right off the bat.

Installation of the ATI restricted driver was a godsend.  I lost my desktop effects that depend on compositing, but I never had that before anyway.

Overall, it was an excellent upgrade from 7.04, but I have only had a few hours with it so far.  Only time will tell.  BTW my HD access is hella faster then before.  I'm lovin that...

---

### Post by go_beep_yourself on 2007-10-19
> **tomdkat said:**
> Here are my first impressions.   :)

Overall use:
So far, Gutsy Gibbon has been running fine for me, with the exception of the video issue above.  I got Firefox 3 (Gran Paradiso) installed along with Gnash and all that worked fine.  I haven't tried everything out yet, like VLC or any kind of audio file player or CD burner, so we'll see how things go over the next week or so.  Gutsy Gibbon "felt" faster than Feisty Fawn at first but I don't feel that now.  Or, maybe I've already adjusted to the new performance level.

Conclusion:
So far, I'm a happy camper.  I like having Gimp 2.4.0 (RC3).  :)

Peace...

How did you install Firefox 3? Where did you get it?

---

### Post by praxis22 on 2007-10-19
I've been running it at work as a clean install and it's great. However as an upgrade to feisty is sucks donkeys.

it helpfully uninstalled beryl, and now enabled compiz, which has window artifacts, and the popup windows from firefox, all appear off screen with the title bars unreachable. It uninstalled some media player codecs and stuff, and now I can get video but not sound, until I open an mp3, then I get a bust of audio from the video I was trying to watch then the mp3 begins to play.

Then of course windows keep turning grey, which is annoying. 

So far I'm regretting it, and there is no way on Gods green and pleasant earth I'm putting gusty on the laptop, feisty works just fine.

Arrrgh! ](*,)

---

### Post by tomdkat on 2007-10-19
> **go_beep_yourself said:**
> How did you install Firefox 3? Where did you get it?
Via the synaptic package manager.  I did a search on Firefox and Gran Paradiso was listed.  Or, I might have done a search on Gran Paradiso (I forget now) but my gut wants to believe I searched on Firefox.

Once I saw it, I selected it and installed it like any other app.   :)

Peace...

---

### Post by tomdkat on 2007-10-19
> **praxis22 said:**
>  the popup windows from firefox, all appear off screen with the title bars unreachable.You should be able to right-click on the side or bottom of the window frame and drag the window down to make the title bar appear again.

Peace...

---

### Post by Cappy on 2007-10-19
> **scourge said:**
> 
4. Third boot

Tried MPlayer right away, and now it worked! Dunno why, but I don't care. Now I started to get annoyed by the tearing in videos and moving application windows. I knew it was because of disabled/incorrect Sync To VBlank settings. The right way to solve this was to disable Sync To VBlank (both XV and OpenGL) in nvidia-settings, and enable it in Compiz Fusion settings. Of course nvidia-settings is still the only thing that correctly detects the refresh rate of my monitor, so I had to change that setting in Compiz Fusion config as well. Problem solved, although not without wasting some precious time.


Same for me. Luckily I read this before I upgraded myself =) It only happens with the compiz fusion enabled luckily. I thought it was some kind of codec problem at first because, like someone else mentioned, codecs were removed during the upgrade.

---

### Post by revidnus on 2007-10-19
Success!
I thought I would give the upgrade from 7.04 to Gutsy a try. It took a while for the packages to download but the install went without any problems. So far I haven't had any problems with any of the software and the 3D effects are awesome. It's going to be fun getting use to this version.

---

### Post by praxis22 on 2007-10-19
> **tomdkat said:**
> You should be able to right-click on the side or bottom of the window frame and drag the window down to make the title bar appear again.

Peace...

Yes, you **should** be able to, but you cant. I've completely pulled what remained of beryl, but that just screwed me even more. before with beryl manager I could reload the windows manager, and the apps would snap mack into the view pane. Now I have no way of doing that. I pulled emerald, and then installed more compiz stuff with synaptic. This given me the advanced menu. but it's pinned off screen and I cant move any windows. I try the the GL desktop, same issue.

So I figured it was just **** and not to be so I yanked the lot, no more compositing desktop for me.

---

### Post by Cappy on 2007-10-19
> **praxis22 said:**
> Yes, you **should** be able to, but you cant. I've completely pulled what remained of beryl, but that just screwed me even more. before with beryl manager I could reload the windows manager, and the apps would snap mack into the view pane. Now I have no way of doing that. I pulled emerald, and then installed more compiz stuff with synaptic. This given me the advanced menu. but it's pinned off screen and I cant move any windows. I try the the GL desktop, same issue.

So I figured it was just **** and not to be so I yanked the lot, no more compositing desktop for me.

I had that problem too. I did a 
```
 sudo apt-get install compizconfig-settings-manager compizconfig-settings-manager
```

and then I went to System --> Preferences --> Appearance --> Visual Effects --> Custom (Preferences button) (this will be there once you install those packages above). 

Under that I changed "Place Windows" and I picked "Centered". I haven't had the problem again so it may have fixed it.

---

### Post by barkej on 2007-10-19
Fresh Install went well. Only problem I had was with my ATI card. I just copied my old xorg.conf I keep on a flash drive via the cli installed the restricted drivers and upon reboot I was set. I am noticing some speed improvement from Feisty. Barring the ATI problems I believe this is one of the best linux releases that I have used.

---

### Post by praxis22 on 2007-10-19
I think the lesson here is install from scratch, do not try to upgrade a heavily optimised Feisty install, you're just asking for trouble. 

My work box works fine, and I installed that from one of the tribe alpha's, but I'm running that to reflections X on a W2k box, so I don't get compositing anyway. 

Having futzed around for the past 6 hours or so, I finally got it working, (it's 2:27am  here)  These two pages are useful:

[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

They're for Feisty, but you can configure it the same:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

basically, I had to remove everything, engines, window decorators, beryl & compiz, everything, (except the config files) . Then you can run:

**sudo apt-get install compiz emerald **and it'll install a load of new stuff.

Then I had to manually kill the existing windows manager, and little by little pulled it back.  Of course, in my travels I must have replaced a good few hundred packages. 

It will be interesting to see if it all comes back up when I reboot. Compiz is still artifecting too, but I'll work on that tomorrow. time for bed methinks.

---

### Post by dada1958 on 2007-10-20
I did a fresh install, everything went fine ... I have encountered one issue so far: I can't log off, reboot, shutdown with the System menu and the icon in the upper right corner of the top panel, my desktop freezes so I have to do it with Ctrl-Alt-Backspace or from gnome-terminal.

---

### Post by old_salt on 2007-10-20
Nothing seems to be working for the HP9000 laptop users. 

- USB doesn't work, you have to boot up with the device plugged in before it's recognized. Unplug and re-plug and nothing.
- Video External monitor no longer works
- K3b won't read media used under Feisty
- Sound is faint and tinny
- complete lack of source code to satisfy dependencies. 

I edit video and I can't get MythTV or anything else running because trying to compile fro source forces a dependency hell situation.

I think Gutsy is for Dell only. Nothing on my system works so I have no choice to revert back to feisty just to use a stinking mouse. What a joke. 

BEFORE ANY release is made, ALL FLAVORS, ARCHITECTURES and ENVIRONMENTS need to be at the same level PRIOR TO RELEASE!!!!!I just installed Ubuntu32 and I got the auto codec install routine, go to Kubuntu64 and this isn't so. 

VERY VERY disappointed in this release as it's a step back for anyone on an HP platform.

Just my FYI

---

### Post by morghi76 on 2007-10-20
I did the network upgrade and everything looked fine at the end... except one thing. If I click on GL Desktop icon in the preferences menu it takes ages before it opens and it does look like the compiz menu I used to have before emerald. Actually, I don't have any emerald icon in the taskbar... I'm just wondering if both systems are living together in my new 7.10..

---

### Post by Mochino on 2007-10-20
I tried upgrading using the upgrade manager, but i get this error:

am i doing something wrong?

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)

---

### Post by Mochino on 2007-10-20
> **Mochino said:**
> I tried upgrading using the upgrade manager, but i get this error:

am i doing something wrong?

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
I also tried using the 7.10 cdrom but when inserting it, it doesn't show any dialog, and when i try:

Alt+f2
gksu "sh /cdrom/cdromupgrade"

nothing happens.

---

### Post by Dahito on 2007-10-20
> **Cappy said:**
> I had that problem too. I did a 
```
 sudo apt-get install compizconfig-settings-manager compizconfig-settings-manager
```

and then I went to System --> Preferences --> Appearance --> Visual Effects --> Custom (Preferences button) (this will be there once you install those packages above). 

Under that I changed "Place Windows" and I picked "Centered". I haven't had the problem again so it may have fixed it.

I've done the same, but used the "smart" option.
Anyway... nobody here mentioned that in **GNOME** you can **drag and resize any window** just moving your mouse on it (in any position) and pressing ALT + MOUSE BUTTON. Left button for drag and central for resize (right bt for KDE).

Any Windows Manager for linux has such features for a long time....  and these + multi desk, shaded windows , unix style copy/paste ....etc ... make me love the linux desk!! .. more than other mac and win stuff.... :mrgreen:

---

### Post by Mochino on 2007-10-20
> **Mochino said:**
> I also tried using the 7.10 cdrom but when inserting it, it doesn't show any dialog, and when i try:

Alt+f2
gksu "sh /cdrom/cdromupgrade"

nothing happens.

i can't believe i'm so dumb,i was using the live-cd, downloading the correct one right now. sorry guys

---

### Post by sixstorm on 2007-10-20
This is the first time that I've ever installed or even tried a 64-bit version of Ubuntu and I'll have to say a few things:

I've always had a decently fast PC, therefore Ubuntu has always been fast for me.  64-bit Ubuntu is not any faster than 32-bit Ubuntu.  

Ubuntu 7.10 x64 is stable and fast.  Good job Ubuntu!

I just bought a laptop at Best Buy earlier this week and had planned on installing Ubuntu at some point.  Thinking that I was going to have a troubled time getting drivers on this thing, I really only had to install two drivers to get wireless and Compiz Fusion to work.  Good job Ubuntu!

I've also got 7.10 x64 installed on my Quad Core rig at home, works great out of the box . . . well, after the first boot I should say.

Finally, I just wanna say that this has been the best release ever.  Great driver/hardware support, great features and great stability in this release.

---

### Post by stbub on 2007-10-20
Trying to install 64bit ubuntu, it detected all sorts of weird things with my video card/monitor.  One time the cd booted at 800x600, other times at 1152x??? or 1280x1024.

Ran into the dreaded "82%" bug (or misfeature, or whatever we ought to call this).

Eventually got a 64bit version installed (I'm using this now).  However, as much as I try to use System->Administration->Screens and Graphics (aka displayconfig-gtk) to pick the correct monitor, and the resolution I want, it's getting me nowhere.  The tool is behaving eractically at best.

And those aren't the only problems I have.

So, basically a big thumbs down.  This has got to be my worst GNU/Linux experience in at least 5years.

---

### Post by distroman on 2007-10-20
> **stbub said:**
> Trying to install 64bit ubuntu, it detected all sorts of weird things with my video card/monitor.  One time the cd booted at 800x600, other times at 1152x??? or 1280x1024.

Ran into the dreaded "82%" bug (or misfeature, or whatever we ought to call this).

Eventually got a 64bit version installed (I'm using this now).  However, as much as I try to use System->Administration->Screens and Graphics (aka displayconfig-gtk) to pick the correct monitor, and the resolution I want, it's getting me nowhere.  The tool is behaving eractically at best.

And those aren't the only problems I have.

So, basically a big thumbs down.  This has got to be my worst GNU/Linux experience in at least 5years.
That sounds too bad.
Anyway if you use 64 bit you should expect spending some time looking for workarounds. 
If you're set on running a 64 bit system I would suggest trying another distribution, I know I do/will. 
Otherwise maybe give gutsy 32 bit ago.

btw good to see some make it work for them more power to you :-)

---

### Post by FredB on 2007-10-21
> **distroman said:**
> That sounds too bad.
Anyway if you use 64 bit you should expect spending some time looking for workarounds. 

Such as ?

> If you're set on running a 64 bit system I would suggest trying another distribution, I know I do/will. 

Why ? I have one little problem with 64bits AMD : no java plugin. And that's all !

> Otherwise maybe give gutsy 32 bit ago.

btw good to see some make it work for them more power to you :-)

Did you ever try gutsy 64bits before writing that ?

Flash => flashplugin-nonfree package

Ubuntu restricted extras : mp3 and many restricted format without a fight...

Why people are always saying (and it's false) : 64 bits == neverending problems ?

---

### Post by John Jason Jordan on 2007-10-21
I've been using Ubuntu amd64 on my laptop since Hoary. Back then I had to run a chroot to get a couple things working. I have just now now made a fresh, clean install of Gutsy amd64, and I can tell you that there is no longer any difference. Everything that works on 32-bit Gutsy now works exactly the same on 64-bit Gutsy. If you run 32-bit Gutsy on a 64-bit CPU you are shortchanging yourself.

---

### Post by FredB on 2007-10-21
> **John Jason Jordan said:**
> I've been using Ubuntu amd64 on my laptop since Hoary. Back then I had to run a chroot to get a couple things working. I have just now now made a fresh, clean install of Gutsy amd64, and I can tell you that there is no longer any difference. Everything that works on 32-bit Gutsy now works exactly the same on 64-bit Gutsy. If you run 32-bit Gutsy on a 64-bit CPU you are shortchanging yourself.

My friend :)

Been on 64bits version since edgy, and it is simpler and simpler to use 64bits versions.

Why those urban legends are still alive ?

---

### Post by conjur3r on 2007-10-21
Have you guys got flashplugin-nonfree working WITH sound on your native firefox?  Videos are fine but no sound?

---

### Post by xieu90 on 2007-10-21
after installing gutsy + a bit of researching
I managed to install everything
but somehow I feel that gutsy is slower than feisty (both of mine were 64 bit)

and somehow it is so hard to run
in feisty after clicking of mouse the application show up immediately
in gutsy i took me around 4 seconds and it drink my ram like water !! (my ram is only 512 (quite small !))

and I hardly saw my cpu has to run this much, sometimes 64% (only firefox)
in feisty I had to use only around 40 % (only when I use a damn lot of  programs at the same time)

---

### Post by Footer on 2007-10-21
> **conjur3r said:**
> Have you guys got flashplugin-nonfree working WITH sound on your native firefox?  Videos are fine but no sound?

flashplugin-nonfree NOT working here.  See post #403 in this thread for details:

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

I'm curious what the original poster of this thread means by this:

> **scourge said:**
> Next I tried Firefox. The non-free 32-bit Flash plugin got installed in a painless fashion.

Is that referring to flashplugin-nonfree???  If so, I'm curious how it's working ... ?  I installed in painless fashion as well.  However, I'm definitely :confused: on this topic since mine is NOT working.

And finally, Gutsy seems to keep my CPUs a lot busier than Feisty did.  Mostly appears due to Xorg and Firefox (viewed with top).  I'm using the restricted drivers that came with Gutsy but thinking about going with the prop. drivers right from Nvidia (I have the GeForce 7600 GS).  But would that make any difference?  The restricted driver is the current one (100.14.19).

---

### Post by Super Nade on 2007-10-21
**atl1** is broken in the 64-bit distribution. Also, the install hangs and I'm unable to load X. No such problems with the x86 version. Running smooth as a whistle as we speak. :D

With the 64-bit version:

```
 goonda@Goonda:~$ sudo dmesg|grep -i atl1
[   34.831321] atl1 0000:02:00.0: version 2.0.7
[   38.869912] atl1: probe of 0000:02:00.0 failed with error -5
goonda@Goonda:~$ 
```

---

### Post by tooter666 on 2007-10-21
I'm pretty new to ubuntu, having tried various versions in the past but never really sticking with them.  I installed  7.10 64-bit onto an old raptor I had lying around, using a new gigabyte ds2R mobo, currently using on-board video, and running an e6750 at 3.60GHz.  All in all, no hitches except my time is off by about 6 hours, and if I change it here it screws up when I go back to XP (on a separate hdd).  So I'm going to leave it.  But on this hardware, the system flies.  Everything works: my scanner, printer, camera, video and audio run fine once I downloaded the codecs as prompted to do so.  

I'll be mostly in the beginners forums.  I'm very comfortable with Windows, and I build my own systems so I'm very comfortable with hardware.  But linux and Ubuntu always have been brief projects in the past, never stuck with them.  However, having the luxury of installing 7.10 64-bit on its own 74 gig raptor has been great. I actually did some work last night using Calc.  All in all, makes me want to sing.  :guitar:

marty

---

### Post by hajk on 2007-10-21
I've used Ubuntu in the past (Breezy, Dapper), but later returned to Debian unstable (Sid) as it had better/faster support for some of the 64-bit stuff I wanted and needed. I kept up-to-date on Ubuntu/Kubuntu developments, though, and felt now was the time to install 64-bit Gutsy on my AMD Opteron 165 desktop.

Installation from the alternate CD, using the familiar text-based Debian Installer, went without any problems whatsoever. In fact, I installed three times, finally ditching Kubuntu for Ubuntu: the Compiz-based effects (after installing the restricted nVidia graphics driver) of the Gnome desktop make the KDE desktop look clunky in comparison (it hurts me to say this, I'm still using KDE in Debian).

I'm also impressed with the smooth integration of many administrative tasks, including doing away with the root user altogether -- this works well, even though I think that many Debian users may reject this on principle.        

I was able to implement the multimedia experience in 64-bit Gutsy by following appropriate instructions in the Ubuntu Community Wiki. All my favourite media sources work in Totem-Xine: content-scrambled DVDs, Windows streaming media (WMV and ASF), Real Media, and Ogg Vorbis and Theora. Furthermore, Flash content plays on Firefox through the nspluginwrapper package and flasplugin-nonfree. Adobe Reader has been installed in 32-bit compatibility mode.

A little tweaking was all that was left: 11pt font size (instead of 10pt); NTP synchronization of date/time; default options in /etc/fstab for removable media and other HD partitions changed to "users,noauto" (and self added to users in /etc/group). My network printer was automatically detected and installed with no more than five (!) mouse clicks.                                               

Best Ubuntu ever!

---

### Post by mb108 on 2007-10-21
I did a clean install, switching from Fiesty 32-bit. Installation was flawless! The only problems I had was some small things with Compiz. I had to do the vsync stuff in nvidia-settings and the Compiz panel, and change the Compiz refresh from 50 to the correct 60hz for my monitor... but it was cosmetic, the functionality was all there. The Desktop Wall effect had some tearing, but I prefer the cube and it works perfectly.

Restricted Device Manager installed and configured my nVidia 8600gt correctly, non-free codecs installed themselves when I clicked on an mp3, and Flash also handled itself just by clicking "install missing plugin" in Firefox -- sound & video are working in Flash. DVDs are fine as well. 

The only thing that was non-intuitive was activating 5.1 sound, and even that I did through the volume control applet, no fussing with ALSA. Oh, and enabling extra mouse buttons. I was in xorg.conf for that.

I even installed the new Enemy Territory: Quake Wars Linux client and have it running with ia32-libs. I guess that was fairly non-intuitive, but also not exactly part of the "default" installation.

Hardware:
ASUS A8N-VM CSM
Athlon X2 4200+
2GB RAM
nVidia 8600GT 512mb
Audigy4-based Soundcard (I forget which exactly)


Sorry to hear people are having problems.

---

### Post by scourge on 2007-10-21
> All in all, no hitches except my time is off by about 6 hours, and if I change it here it screws up when I go back to XP (on a separate hdd).

That happened to me once too. The problem was that Windows assumed the system clock was in local time, and Ubuntu was using UTC. To fix it, uncheck "Use UTC" in Clock Preferences.

---

### Post by sweRocker on 2007-10-21
Being a supernoob I was expecting loads of trouble when upgrading, but I was wrong!

Anywho, after downloading the alternate iso (the update manager did not work, I guess the servers were down) and burned it on a dvd. 

The burning was fast and silent so i did not notice when it finished. Coming back refreshed by coffe I accidently pushed the dvd back into the system and initiated the installation. Perhaps it would have been a good idea to check the dvd for defects, but I am lazy. 

Things are running smoothly without any problems at all. 

Ahh...

MSI K9N6SGM-V
GeForce 7300GS
2 GB RAM
AMD Athlon 64 X2 4200+

---

### Post by Pancetilla on 2007-10-21
I did a clean install, after half a year with Etch 64 bits. I had a not-so-pleasant upgrade to lenny a week or so ago and I decided to return to Ubuntu (i have been using Ubuntu since 5.04) and give Gutsy 64 bits a go (no bad feelings against Debian, etch has been great).

Painless install, everything works and it have taken me about 1/2 hour to do the set-up. Great job with this, Ubuntu team, at least from my experience! 

I also upgraded my girlfriend's laptop from feisty to gutsy, another success (but 32-bits)

---

### Post by GSF1200S on 2007-10-23
I installed the 64bit Buntu kernel, and built the GUI with apt. I installed KDE base, and literally built my entire setup from scratch.

You know, everyone always talks about Java not working in 64bit. Have any of you heard about Swiftweasel? You can use blackdown 1.4 java with swiftweasel and it will run great. Keep in mind that swiftweasel accepts all the same plugins as firefox, and is optimized for 64bit and 32bit systems. 

Im attaching a screenshot of my ```
about:plugins
``` to show you my java/flash.

64bit shows a nice performance boost, ESPECIALLY copying my cds and such. Seems nice and stable, and both my wireless and my video worked with the restricted drivers manager... Overall, at least for my main, Gutsy was a FANTASTIC upgrade. 

My alt lappie is having problems in Gutsy (as it does with Feisty), thanks to a Radeon Xpress 200M, and a broadcom wireless card. Anyways, Gutsy64 seems like a nice step ahead..

---

### Post by nirkir on 2007-10-23
I way running 64 bit 7.04 + Beryl

Upgraded via update manager to 7.10 64 bit - no problems with installation, nVidia driver works perfectly, flash works great, amd sp forth

The new features built into compiz are great. This works A LOT FASTER than 7.04 + Beryl

Still have a minor problem with USB 2.0 devices sometimes recognized as USB 1.0 but other than that I AM REALLY HAPPY with Gutsy.

Way to go Ubuntu

---

### Post by ecowarrior on 2007-10-23
I've been running Gutsy for about two or three weeks now - since beta.  It's running just fine, no real problems that I can think of ('cept power saving).

I like the idea of running a 64-bit OS on a 64-bit processor, but b*gger me if I know how to use all of it's power!  I mean all I ever really run is firefox!!! :)

If I nailed down what I use a PC for it comes down to this:

a bit of word processing (which I still use Windows for because I can't print to my Lexmark Z617 on Ubuntu 64 - I really need to get a new, and supported, printer!).

a bit of picture editing (I prefer Photoshop Elements for this, though I'm starting to get the hang of GIMP)

a bit of occasional video editing (can anybody recommend a good linux video editor?  I have Pinnacle Studio 9 on Windows, which I normally use)

music and dvds

and firefox for surfing.

All my software development is done on MS Visual Studio and .NET on my Windows laptop for work (however good Linux is [and mono], nothing in my opinion beats the whole VS/.NET/C# for development).

So for all the power I have available to me, I ain't really using a lot of it, which is a shame.  Still, at least I don't need anti-virus, my firewall protection (firestarter) seems rock solid (according to the shields-up website), and I ain't worrying about spyware infections.  And frankly, now I've made the switch Ubuntu is still a much nicer place to be than Windows, and about £200 cheaper than upgrading to Vista too!

---

### Post by drs305 on 2007-10-23
Initially upgraded from Feisty with the RC version, then later a clean install from the release version. 

Everything went very well except an HP printer issue, but even that finally started working about the fourth time I tried installing it. Didn't need gnome-cups-manager to get it to work, by the way.

Very pleased with Gutsy so far!

---

