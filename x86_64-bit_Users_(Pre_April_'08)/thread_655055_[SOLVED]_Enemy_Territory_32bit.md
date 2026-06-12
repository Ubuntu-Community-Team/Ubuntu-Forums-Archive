---
title: "[SOLVED] Enemy Territory 32bit"
date: 2007-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by ~LoKe on 2007-12-31
GRRRR!  Trying to install enemy territory, but it's 32bit and I'm using 64bit 7.10.  I've installed the linux32 package as well as the 32bit lib package (can't remember the exact name off hand).   I'm still getting this, though:

> This installation doesn't support glibc-2.0 on Linux / unknown
The setup program seems to have failed on unknown/glibc-2.0

What should I do?

---

### Post by Cappy on 2007-12-31
Did you try ```
linux32 sh installer.run
```

For the record, you only should install linux32 on non-Gutsy systems because on Gutsy it already comes installed.

---

### Post by ~LoKe on 2007-12-31
Same problem. :(
> The setup program seems to have failed on x86/glibc-2.0

---

### Post by SidewinderPro2 on 2007-12-31
Good luck getting it going. Coolest game ever, even though the graphics can't compare to anything on the Unreal 3 or Crytek 2 engines. The gameplay is simply unparalleled. I bought the game the day it came out and now I have an extra copy from my eVGA card.

Can someone running ETQW Linux play on/with ETQW Windows players and servers?

---

### Post by ~LoKe on 2007-12-31
I've read that et 2.60 works in x86_64, but I need 2.55 to play on my teams server.  I hope there's a way...

---

### Post by Cappy on 2007-12-31
Maybe
```
sudo apt-get install libc6 libc6-i386
```
and then running ```
linux32 sh installer.run
``` again will help.

I've seen someone say
```
export SETUP_LIBC=glibc-2.1
``` can help too.

Good luck!

---

### Post by ~LoKe on 2007-12-31
This is depressing.  People have been going on and on about how 32bit apps work "just fine" in a 64bit environment.  So I go through all this trouble getting 64bit installed, replacing my 32bit installations, and surprisingly the first 32bit app I try to run fails.

Great.

I've heard of chrooting to get it installed, which I'm willing to do...but how?

**EDIT**: Same problem, Cappy.  I've got the packages installed (from a different guide), still nothing.  I tried the export line, still the same error. :(

---

### Post by BogusJoe on 2007-12-31
> **~LoKe said:**
> This is depressing.  People have been going on and on about how 32bit apps work "just fine" in a 64bit environment.  So I go through all this trouble getting 64bit installed, replacing my 32bit installations, and surprisingly the first 32bit app I try to run fails.

Great.

I've heard of chrooting to get it installed, which I'm willing to do...but how?

**EDIT**: Same problem, Cappy.  I've got the packages installed (from a different guide), still nothing.  I tried the export line, still the same error. :(

Hey LoKe,
This worked for me with the help of Cappy and puccaso.  See thread here:
[http://ubuntuforums.org/showthread.php?t=655107](http://ubuntuforums.org/showthread.php?t=655107)

But this was on Hardy Heron 64    Going to try the Gutsy 64 tonight.
This was ET Quake Wars, but the same process should work for ET.

---

### Post by ~LoKe on 2008-01-01
> **BogusJoe said:**
> Hey LoKe,
This worked for me with the help of Cappy and puccaso.  See thread here:
[http://ubuntuforums.org/showthread.php?t=655107](http://ubuntuforums.org/showthread.php?t=655107)

But this was on Hardy Heron 64    Going to try the Gutsy 64 tonight.
This was ET Quake Wars, but the same process should work for ET.

Doesn't quite work for me.

> 
1. chmod u+x ETQW-demo-client-1.1-full.r5.x86.run
2. ./ETQW-demo-client-1.1-full.r5.x86.run (target folder: /home/user/etqw)
3. sudo cp -r --preserve=mode /home/user/etqw /usr/local/games
4. sudo ln -s /usr/local/games/etqw/etqw /usr/local/games/etqw/etqw-dedicated /usr/local/bin
I can't perform step 2...it fails with the glibc-2.0 error. =/

---

### Post by BreathEasy on 2008-01-01
> **~LoKe said:**
> I've read that et 2.60 works in x86_64, but I need 2.55 to play on my teams server.  I hope there's a way...
Why isn't your team's server running 2.60 (or 2.60b for that matter)? The patch has been around forever - any old mods would have been updated by now.

Not that it help your problem, I'm just curious.

---

### Post by ~LoKe on 2008-01-01
> **BreathEasy said:**
> Why isn't your team's server running 2.60 (or 2.60b for that matter)? The patch has been around forever - any old mods would have been updated by now.

The settings are different.  2.6/2.6b have more accurate shooting, which would be an extreme change for cultured 2.55 players.  I previously had a dual installation so I could play 2.6b as well as 2.55.

---

### Post by ~LoKe on 2008-01-01
Sad. :(

---

### Post by BreathEasy on 2008-01-01
OK, do you still want a solution? Cos I have one.

The problem you're having is the same one I had when I tried to install the binaries for RTCW - they wouldn't work at all on a 64-bit system and gave the same error message. My solution? Run the installer on a laptop I had available which had the **32-bit** version of Ubuntu, let it install its stuff to a directory I could easily access, then copy the files over to my 64-bit system.

The game worked just fine, it was the installer which couldn't start no matter what, even with the 32-bit libs available. So long as you can access a 32-bit Ubuntu (or any Linux for that matter) and can get files from it onto your system, you'll be fine. Run 32-bit Ubuntu in VirtualBox or something if you want.

---

### Post by ~LoKe on 2008-01-01
> **BreathEasy said:**
> OK, do you still want a solution? Cos I have one.

The problem you're having is the same one I had when I tried to install the binaries for RTCW - they wouldn't work at all on a 64-bit system and gave the same error message. My solution? Run the installer on a laptop I had available which had the **32-bit** version of Ubuntu, let it install its stuff to a directory I could easily access, then copy the files over to my 64-bit system.

The game worked just fine, it was the installer which couldn't start no matter what, even with the 32-bit libs available. So long as you can access a 32-bit Ubuntu (or any Linux for that matter) and can get files from it onto your system, you'll be fine. Run 32-bit Ubuntu in VirtualBox or something if you want.

So I can just copy over the /usr/local/games/enemy-territory folder from a 32bit environment and it'll actually run?  No issues?

---

### Post by BreathEasy on 2008-01-01
> **~LoKe said:**
> So I can just copy over the /usr/local/games/enemy-territory folder from a 32bit environment and it'll actually run?  No issues?
That's exactly what I did with Return to Castle Wolfenstein. It ran fine provided I had the 32-bit libs available to run 32-bit programs, but they were easy to install - just installed Wine and the relevant packages came along with it for example.

---

### Post by ~LoKe on 2008-01-01
Hm...

I ran the installer for 2.60 and downloaded et.x86 and etded.x86 for 2.55 and copied them over.  I can connect to noquarter server, so I know that works, but when I try to connect to etpub server, I get this error:

> ^5PunkBuster Client: Connected to Server 208.167.244.143:27960
********************
ERROR: Couldn't load an official pak file; verify your installation and make sure it has been updated to the latest version.
********************
copy /usr/local/games/enemy-territory/etmain/ui.mp.i386.so to /home/loke/.etwolf/etpub/ui.mp.i386.so
Sys_LoadDll(/home/loke/.etwolf/etpub/ui.mp.i386.so)... ok

I think I'm missing some important pak files for /usr/local/games/enemy-territory/etmain.  If anyone has 2.55 installed, could you do me a huge favor and make an archive of the four .pk3 files in that directory?  mp_bin.pk3 pak0.pk3 pak1.pk3 pak2.pk3?  I'd really appreciate it!

---

### Post by ~LoKe on 2008-01-01
Woot!  I chrooted, installed a bunch of packages, went through a world of hell, installed et 2.55!!! copied the folder from /chroot/usr/local/games/ and ran it.  IT WORKS!!!

Thank you, thank you!

---

### Post by Cappy on 2008-01-11
I was looking back at this thread and I decided to figure out a solution since this is about the only thing that may need a chroot sometimes.

Edit: Made a tutorial -
[http://ubuntuforums.org/showthread.php?t=667771](http://ubuntuforums.org/showthread.php?t=667771)

---

