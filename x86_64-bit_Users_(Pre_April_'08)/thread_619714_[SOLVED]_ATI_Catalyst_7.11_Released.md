---
title: "[SOLVED] ATI Catalyst 7.11 Released"
date: 2007-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-11-21
Has anyone tried this driver yet?

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html")

---

### Post by Kilz on 2007-11-21
> **crjackson said:**
> Has anyone tried this driver yet?

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html")

Not me , but I have been waiting for the release after 8.42.3 and this appears to be it, they are changing the numbering sequence though.

---

### Post by crjackson on 2007-11-21
> **Kilz said:**
> Not me , but I have been waiting for the release after 8.42.3 and this appears to be it, they are changing the numbering sequence though.

Me too.  This is the one I hope.  I'm at work and won't be able to try it for a few days.  I'm just hoping for a decent stable driver with desktop effects ability.  If you get it going and it seems solid, please post any special procedures so I can follow you on this.  I've got 7 systems running right now with ATI cards and Ubuntu.  I'd love to play with desktop effects without compromising stability and performance.

---

### Post by Kilz on 2007-11-21
> **crjackson said:**
> Me too.  This is the one I hope.  I'm at work and won't be able to try it for a few days.  I'm just hoping for a decent stable driver with desktop effects ability.  If you get it going and it seems solid, please post any special procedures so I can follow you on this.  I've got 7 systems running right now with ATI cards and Ubuntu.  I'd love to play with desktop effects without compromising stability and performance.

I have a ati x1050, its a budget card, and with 8.42.3 I was able to get effects running just fine on Feisty. I turned them off because they are annoying to me. The shaded panels that  when you remove the shade dont match up the wallpaper drives me nuts. I like the desktop wallpaper to look like it is one sheet.

---

### Post by crjackson on 2007-11-21
> **Kilz said:**
> I have a ati x1050, its a budget card, and with 8.42.3 I was able to get effects running just fine on Feisty. I turned them off because they are annoying to me. The shaded panels that  when you remove the shade dont match up the wallpaper drives me nuts. I like the desktop wallpaper to look like it is one sheet.

It's not something I'll probably run with on my personal desk/laptop systems, but I would love to have the option.  I hate feeling like my system is crippled because I run ATI.  ATI's have been dragged through the mud so much, I just want a level playing field.

I was going to try the 8.42.3 driver, but I've real lots of bad reports and memory leak issues so I didn't bother.  I was waiting for 8.42.3 +1 before tinkering again.  Right now, I'm only using the .37 driver that gets installed from the repos in Gutsy.  They work pretty good but I do have a couple of very small issues with them.

---

### Post by garoth2 on 2007-11-22
Acer Travelmate 4402WLMi laptop with ATI Radeon Mobility X700

With 8.42.3 I had the problem with video tearing/corruption when trying to use the hardware overlay (while Compiz was enabled)... and actually I recently was unable to play any video files at all even with Compiz disabled (not sure why).

Upgrading to this release
-Video playback works with Compiz enabled or disabled
-With compiz enabled, some flicker in video playback when NOT in full screen... when in full screen video plays fine with tolerable amount of tearing
-Scrolling in Firefox still a bit slow. In Firefox 3.0b1 it is tolerable, compared to Firefox 2

Overall I'm happier with this release - it has been an improvement, at least for me. I much prefer the look/feel of the desktop with being able to use Compiz - all of the fonts appear crisper to me and menus are more responsive, so this is important to me.

---

### Post by konas on 2007-11-22
Acer Aspire 5024 WLMi here, with x700 mobility. I installed the driver. There is still the flickering problem , firefox scroll not perfect , Xorg consuming more CPU (then 8.42.3). No other changes noticed

---

### Post by crjackson on 2007-11-22
I was hoping for better reports.  I'll wait a bit longer to try it.  What procedure did you use to install the driver?

---

### Post by Spydr4590 on 2007-11-22
Here is a lots of good feedback for you. [http://www.phoronix.com/forums/showthread.php?t=6583](http://www.phoronix.com/forums/showthread.php?t=6583) Eight pages long as of this post.

---

### Post by RavanH on 2007-11-22
I tried the new driver. First with ```
sudo sh ati-driver-installer-7-11-x86.x86_64.run

``` but that (strangly) did not get rid of the 8.42.3 driver. Then I followed the methode for Feisty (with adaptation for Gutsy and AIGLX) from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d13e3d64227835de55250d3ecabcca5e1532b751](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d13e3d64227835de55250d3ecabcca5e1532b751)

Now I get:
```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7059 Release
```

And the ATI Catalyst Control Center tells me I am using driver version 8.43.2 - which must mean I succeeded? What's up with that numbering anyway? How confusing can they make it :confused:

But that's all folks. Other than this proof, I see/feel/measure no difference from before :( Still jerky 3D, still no Suspend/Hibernate... maybe? Ok, just maybe a little improvement on browser scrolling ;)

Oh, and video playback? On my system all seems well now but that might have been caused by other tinkering: I set standard Video output in gstreamer-properties to 'X Window System (no Xv)' and in MPlayer preferences selected the Video driver 'x11' for example...

Anyone notice any improvement?

---

### Post by Kilz on 2007-11-22
It looks like all they did was change the version number. I installed it and got a very small boost on glxgears fps. But all the problems that started started with the new driver remain. Im thinking of going back to 8.40.4.

---

### Post by erfahren on 2007-11-22
my screensaver had a flickering to it (Atunnel). Thinking I might be able to deal with that I started desktop efffects to see how they'd work. Scrolling worked slow, kind of jumpy. I opened up the screensaver settings to try a different one and everything froze. I had to do a reset to restart.

I never seem to have much luck with the drivers newer than what's available in the repositories.

---

### Post by Kilz on 2007-11-22
> **erfahren said:**
> my screensaver had a flickering to it (Atunnel). Thinking I might be able to deal with that I started desktop efffects to see how they'd work. Scrolling worked slow, kind of jumpy. I opened up the screensaver settings to try a different one and everything froze. I had to do a reset to restart.

I never seem to have much luck with the drivers newer than what's available in the repositories.

The problem is that 2 releases ago ATI released a whole new driver code base. It wasnt just an improvement of what existed before. Those that are installing this new driver ( 8.41.7, 8.42.3 or 7.11) thinking that its going to be bug free and work flawlessly are only fooling themselves.

Like most things in linux, code is released when it has some functionality so that the users can find the bugs. Think of 7.11 as Alpha 3. Maybe by 8.06  we will start to see what it will really do.

---

### Post by crjackson on 2007-11-23
> **Kilz said:**
> The problem is that 2 releases ago ATI released a whole new driver code base. It wasnt just an improvement of what existed before. Those that are installing this new driver ( 8.41.7, 8.42.3 or 7.11) thinking that its going to be bug free and work flawlessly are only fooling themselves.

Like most things in linux, code is released when it has some functionality so that the users can find the bugs. Think of 7.11 as Alpha 3. Maybe by 8.06  we will start to see what it will really do.

I'm not going to bother with it.  I'll wait until it gets a little better.  I don't need the extra headache.

---

### Post by matt2ss on 2007-11-23
What about including a binary into Ubuntu updates? I've been waiting for pretty long time (since fglrx 8.37.6).

---

### Post by Kilz on 2007-11-23
> **matt2ss said:**
> What about including a binary into Ubuntu updates? I've been waiting for pretty long time (since fglrx 8.37.6).

You actualy have a pretty good driver installed then, keep it until you hear there is a reason to install a new one. That is unless you are fond of bugs and things that dont work.

---

### Post by Yellow Pasque on 2007-11-24
> **Kilz said:**
> I'm thinking of going back to 8.40.4.

That's what I did. The only positive thing I can say about the latest ATI driver is that it gives me a nice boost in glxgears (from ~600fps to ~1000fps) on my integrated X1250/690G. Unfortunately, the issue with the screen corruption (horizontal bars appear by my cursor and in the lower-right part of my screen) kept me from sticking with this release, just like it did with 8.42.3

---

### Post by macaholic on 2007-11-25
I've seen no real improvements to this dirver, but I might add it was a HUGE pain to get it finally working on my main 64-bit box. Another annoying thing, on my 32-bit fallback partition, not only was it easier to install, but it also is alot smoother then the 64-bit side of things.

---

### Post by Kilz on 2007-11-25
> **Temüjin said:**
> That's what I did. The only positive thing I can say about the latest ATI driver is that it gives me a nice boost in glxgears (from ~600fps to ~1000fps) on my integrated X1250/690G. Unfortunately, the issue with the screen corruption (horizontal bars appear by my cursor and in the lower-right part of my screen) kept me from sticking with this release, just like it did with 8.42.3

I did go back to 8.40.8 for now. I agree the only benefit was about a 400-500 fps boost in gears. But I dont notice the difference in the applications I use. Some of which didnt work right (or at all ) with the new drivers.

> **macaholic said:**
> I've seen no real improvements to this dirver, but I might add it was a HUGE pain to get it finally working on my main 64-bit box. Another annoying thing, on my 32-bit fallback partition, not only was it easier to install, but it also is alot smoother then the 64-bit side of things.

Being that the new drivers are imho early beta versions, dont put to much importance on how they are now on any version. Dont expect them to work right or install painlessly. This is only the 3rd release of a new code base. Linux drivers and applications are released as soon as they are so-so working so that the community can find the problems. That is whats happening now.

---

### Post by xiaoxin on 2007-12-02
> **Temüjin said:**
> Unfortunately, the issue with the screen corruption (horizontal bars appear by my cursor and in the lower-right part of my screen) kept me from sticking with this release, just like it did with 8.42.3

How to solve the issue:

In xorg.conf add the following lines to the "Device" section:
```
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "BlockSignalsOnLock" "on"
Option "UseFastTLS" "2"
Option "KernelModuleParm" "locked-userpages=0"
Option "no_accel" "no"
Option "no_dri" "no"
Option "EnablePrivateBackZ" "no"
Option "backingstore" "true"
Option "XAANoOffscreenPixmaps" "true"
Option "ForceMonitors" "notv"
```

---

