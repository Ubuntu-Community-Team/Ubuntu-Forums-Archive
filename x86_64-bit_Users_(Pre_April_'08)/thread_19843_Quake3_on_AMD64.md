---
title: "Quake3 on AMD64"
date: 2005-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by mthaddon on 2005-03-14
Hi Folks,

Don't know if I'm tempting fate here, but... trying to install Quake3 on a laptop with an Nvidia card that's configured fine -  I have UT2004demo working fine, but, I actually own Quake3, and am trying to install it. It was giving me a bunch of messages saying that it wasn't compatible with AMD64, but I changed the startup script to fool it into installing for me (I basically manually set the ARCH and GLIBC variables). Problem is, now when I start up I get the following. Is this just a case of it won't work on AMD64 - only it seems like some folks have got it working and I was hoping to be able to as well.

Thanks, Tom


Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/mthaddon/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Received signal 11, exiting...

---

### Post by Pse on 2005-03-14
You could try installing first the ia32-libs that are required...and then pointing to them by doing:
```
LD_PRELOAD=/usr/lib32/libGL.so.1 quake3
```

(Of course, /usr/lib32 is a placeholder for the directory where you put the 32-bit libGL.so.1, and "quake3" is the name of your executable)

BTW, I remember seeing a page discussing how to set up Quake3 on an AMD64 system...I just can't find it right now, I'll look into it and post the link...

---

### Post by Pse on 2005-03-14
Also, if nothing else works, try this:
```
+set r_gldriver /usr/lib32/libGL.so.1
```
Use that line as a parameter for the binary file of Quake3...example: "./quake3 +set_rgldriver /usr/lib32/libGL.so.1"

---

### Post by Pse on 2005-03-14
OK, I've been trying to do it myself with Enemy Territory...and I'm still getting the same error as you. Sofware Rendering can still be used to load your game if you want, by using the "+set r_allowSoftwareGL 1" parameter... Quake3 should load. The problem seems to be the 64-bit OpenGL lib... I'll try to get a 32-bit libGL.so.1.2 and use that.
BTW, when I try to use the 64-bit libGL that is located in /usr/X11R6/lib, the system tells me it doesn't exist, even though it's totally there! Even if I move it, it still tells me it isn't there! LOL!

---

### Post by Pse on 2005-03-14
OK, as far as I can tell, we shouldn't be trying to use libGL.so.x.x 'cause it's the software renderer (??). I've trying to load fglrx_dri.so instead as the GL driver in ET, now I get Signal 11 without the Software Rendering notice, without errors loading. I'll keep testing.

---

### Post by mthaddon on 2005-03-14
Thanks for the replies! Let me know if you get a working solution. In the meantime I'm going to look into the ia32libs package and see if that can get me anywhere.

Thanks, Tom

---

### Post by Pse on 2005-03-14
I've read in a post made by subterrific that using Quake's SMP binaries work for uniprocessor (!!!) AMD64 systems (how about that!). Try it, I can't 'cause there are no SMP binaries for ET :(

---

### Post by Tichondrius on 2005-03-14
[QUOTE=mthaddon]Thanks for the replies! Let me know if you get a working solution. In the meantime I'm going to look into the ia32libs package and see if that can get me anywhere.

Thanks, Tom[/QUOTE]
 yeah, lots of people are having the same problem when trying to run enemy territory or RTCW on AMD64. I also tried out a few things to get it to load the correct library, but did not manage to get it to work. Please update if anyone makes a breakthru on this.

---

### Post by Pse on 2005-03-14
[http://www.ubuntuforums.org/showthread.php?p=93812#post93812](http://www.ubuntuforums.org/showthread.php?p=93812#post93812)

Check that post as well. Anyone who hasn't tried any of the possible solutions proposed should try them. Check the bugzilla BUG as well.

As I said in that other thread, I guess ET is trying to load libraries from /usr/lib...when it should be trying to load them from /usr/lib32... I haven't been able to change that so far.

---

### Post by Kareema on 2005-03-14
Add these lines to your start script (doom3 or et) to get Doom 3 or Enemy Territory working on AMD64:

export LIBGL_DRIVERS_DIR=/usr/X11R6/lib32/modules/dri
export LD_LIBRARY_PATH=/usr/lib32:$LD_LIBRARY_PATH:.

And be sure to have all libraries starting with "ia32-libs" installed. If this still doesn't work look for "ia32-libs-more" in this forum, download and install the package.

This worked for me and I hope it will work for you, too.

---

### Post by Pse on 2005-03-14
Thanks for the tip, Kareema, I'll try it right away.

---

### Post by Pse on 2005-03-15
I'm afraid I have to say the problem's still there. I have added the package your described, but I still get Signal 11.
I take you're not running a chroot for ET/Q3 or for Doom3...and they work?
Could you please tell me *exactly* which were the steps you followed.
Could you post the output from the ET/Q3 console when you start the game?

BTW, I have not added "export LD..." to my initscripts, of course, I have just ran them in a console and then started the game.

---

### Post by Pse on 2005-03-15
SUCCESS! GUYS, I GOT ET TO WORK UNDER AMD64 WITHOUT CHROOTING USING HARDWARE ACCELERATION!
I'll post what I did in a couple of secs while I finish moving some libs around!

---

### Post by Pse on 2005-03-15
So, here's what I did:
1) Get all ia32 packages from synaptic.
2) Install package "linux32" (it's a uname wrapper :-D)
3) Install ia32-libs-more from **Subterrific**'s package.
4) Get 32-bit OpenGL DRI libs for your graphics card.
4.1) (ATI cards only) Go to [www.ati.com](www.ati.com) and download the 32-bit rpm of your driver (same version as 64-bit).
4.2) (ATI cards only) Unpack "fglrx_dri.so" (should be under "/./usr/X11R6/lib/modules/dri/" inside the package).
4.3) (ATI and nVidia cards) Put it in "/usr/X11R6/lib32/modules/dri". That directory should not exist, so you have to create it.
5) Run the latest ET setup binary (2.56) by doing "linux32 sh et-linux-2.56.x86.run".
6) Follow the setup instructions and complete the installation process.
7) Put **Kareema**'s lines (the bold ones) in your startup script ([game's install path]/et):
```

#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
[b]export LIBGL_DRIVERS_DIR=/usr/X11R6/lib32/modules/dri
export LD_LIBRARY_PATH=/usr/lib32:$LD_LIBRARY_PATH:.[/b]
cd "/mnt/XFS-Drive/games/enemy-territory/"
./et.x86 $*
exit $? 

```
8 ) Fire up the script by doing "linux32 sh et" (it should work without doing "linux32", but I haven't tried it yet).

[EDIT] Step 3 should be optional, but it can't hurt to have a few more 32-bit libs lying around ;) I haven't tried removing them.
Also, setting LD_LIBRARY_PATH should be optional, I haven't tried it yet.

These procedure should also work for Q3, but I haven't tried that...

---

### Post by Pse on 2005-03-15
For those of you running nVidia hardware, you could try these steps:
4.1) (nVidia only) Go to [www.nvidia.com](www.nvidia.com) and download the 32-bit linux driver (get the same version as your current 64-bit driver).
4.2) Only unpack it by doing "$ sh NVIDIA-Linux-x86-1.0-7167-pkg1.run --extract-only" 
4.3) Copy both the "libGLcore.so.1.0.7167" file and the "libGL.so.1.0.7167" file from "...[place where you unpacked]/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/lib" to "/usr/X11R6/lib32/modules/dri". Create the directory if needed.
Continue with the remaining steps and post back your results, so we can know if it works!

---

### Post by subterrific on 2005-03-15
I can tell you without trying them that those instructions will not work for nvidia. nvidia drivers do not use dri, and as far as I know LIBGL_DRIVERS_DIR has no effect with the nvidia drivers because of that.

EDIT: also, the amd64 nvidia drivers include 32bit GL libraries already, and they're installed by the nvidia-glx package.

---

### Post by Pse on 2005-03-15
I know you have already tried very similar procedures, but I still think it's worth the shot downloading the 32-bit binaries and do this...
Even if nVidia's drivers do not work using DRI, they still must provide a library that games must use for them to work...I just said "DRI" 'cause of the name in the ATI file. My guess is that those two libraries I mentioned are the ones that handle the OpenGL API...If I had a nVidia card on another AMD64 system, I'd try it...

[EDIT]Furthermore, LIBGL_DRIVERS_PATH should work even if nVidia's drivers are not DRI...They *must* use some sort of library, otherwise they'd brake compatibility with every application that tries to use OpenGL.
Look at the output from the game when it tries to start...it should say which library is being loaded for OpenGL support; it should even tell you what driver is being used (GL_RENDERER section).

---

### Post by Boomstickz on 2005-03-15
No luck with Nvidia, Subterrific was right about that. I also tried some other things along the lines of what you were doing, and I again, had no luck, but i'll continue trying different things, what I did try before though, was setting the LIBGL_DRIVERS_DIR= path to different things, I tried every directory in my system that contained the libGL or anything to do with it, and that didn't change anything.

Hopefully one of us will figure this out, nvidia seems to be a bit more complicated to get working than the ATI as far as this.

---

### Post by Pse on 2005-03-15
You did try using the 32-bit libGL.so lib, right?

---

### Post by Boomstickz on 2005-03-15
yup sure did, I tried the way you said, and I tried the ones that came with the nvidia-glx drivers, no worky, has anyone with a nvidia card gotten this to work?

---

### Post by skumlex on 2005-04-18
Here is the solution to the ET/Quake3 problem on nVidia hardware (probably works with ATI as well) in  /usr/local/bin (or whereever you installed it) open "et" and add the line export LD_ASSUME_KERNEL=2.4.2
ET loads up fine an works with hardware accleration.
Kudos goes to this site [http://www.nerdarium.com/archives/2005/03/14/update-enemy-territory-without-the-chroot/](http://www.nerdarium.com/archives/2005/03/14/update-enemy-territory-without-the-chroot/)

---

### Post by Fascination on 2005-05-15
My problem is that I cant even get Quake 3 installed, and Im presuming I need to set up a 32 bit chroot first;

```
fasc@balamb:/media/cdrom0$ sudo sh setup.sh
This installation doesn't support glibc-2.0 on x86_64

Please contact Loki Technical Support at support@lokigames.com
```

If anyone knows of another method, I would be pleased to hear it. :)

EDIT: Just realised that this is under the Warty section, and Im on Hoary - much apologies.

---

### Post by hammett111 on 2005-05-28
Okay "FASCINATION" had the same problem and this is what you should do.

Download all the IA3 crap from Synaptic this will allow you to use the command linux32 I think.

Then type linux32 ./setup.sh and it will bypass that glibc crap, its a 32bit vs 64bit error, the linux32 command will omit that and allow ti to run.

Kapeesh!!

---

### Post by Fascination on 2005-05-29
Found the linux32 as a seperate package (called 'linux32') and once installed it did the trick - cheers. ;)

---

### Post by psycho0815 on 2005-05-31
Just tried out the LD_ASSUME_KERNEL thing with et and it really did the trick.

---

### Post by hammett111 on 2005-06-09
That export LD_ASSUME_KERNEL=2.4.2 made it run, but its slow as a bi$@&!!! Am I supposed to add all that export lib stuff as well, because its pretty bad!!!!!!!!

---

### Post by hammett111 on 2005-06-09
[QUOTE=hammett111]That export LD_ASSUME_KERNEL=2.4.2 made it run, but its slow as a bi$@&!!! Am I supposed to add all that export lib stuff as well, because its pretty bad!!!!!!!![/QUOTE]

Can I change the assume kernel to another version??

---

