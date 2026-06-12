---
title: "loading libGL.so.1: Received signal 11"
date: 2005-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by subterrific on 2005-01-17
I'm running the most recent Hoary with the most recent nvidia-glx and whenever I try to run quake3 or enemy territory I get this:

*snip*
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Received signal 11, exiting...

I've tried passing +set r_glDriver /usr/lib32/libGL.so.1, I've tried setting various environment variables, nothing seems to work. I have a 32bit glxinfo installed, and when I run it, it shows the nvidia driver as being loaded. I also have cedega installed (not in a 32bit chroot) and I'm able to run Half-Life 2 and CS:Source with it.

Any ideas?

---

### Post by subterrific on 2005-01-17
This seems odd to me:

```
file /usr/local/games/quake3/quake3.x86
/usr/local/games/quake3/quake3.x86: ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), for GNU/Linux 2.0.0, dynamically linked (uses shared libs), stripped

ldd /usr/local/games/quake3/quake3.x86
        not a dynamic executable

ltrace /usr/local/games/quake3/quake3.x86 +set r_glDriver "/usr/lib32/libGL.so.1.0.6629"
ltrace: "/usr/local/games/quake3/quake3.x86" is ELF from incompatible architecture
```

---

### Post by subterrific on 2005-01-19
Updates today didn't fix the problem. I don't really want to bother the Ubuntu developers about this unless someone else is having this issue. Anyone?

---

### Post by subterrific on 2005-01-19
Well I talked to a few developers on irc and didn't really get anywhere so I opened a bug: [https://bugzilla.ubuntu.com/show_bug.cgi?id=5646](https://bugzilla.ubuntu.com/show_bug.cgi?id=5646)

---

### Post by subterrific on 2005-01-21
Finally made a break through in solving this issue: see bugzilla page.

---

### Post by norfenstein on 2005-02-16
For the record, I'm getting this same problem on Warty with a P4. It doesn't happen immediately though, I can start Quake 3 and run it fine for a while before having it crash spontaneously. This only started happening recently but I have no idea what I could have done to make it start.

---

### Post by Tichondrius on 2005-02-17
[QUOTE=subterrific]Finally made a break through in solving this issue: see bugzilla page.[/QUOTE]
 I'm getting the exact same problem, and can't get it to work using any of your breakthrus

---

### Post by penguinz on 2005-02-20
[QUOTE=subterrific]I'm running the most recent Hoary with the most recent nvidia-glx and whenever I try to run quake3 or enemy territory I get this:

*snip*
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Received signal 11, exiting...

I've tried passing +set r_glDriver /usr/lib32/libGL.so.1, I've tried setting various environment variables, nothing seems to work. I have a 32bit glxinfo installed, and when I run it, it shows the nvidia driver as being loaded. I also have cedega installed (not in a 32bit chroot) and I'm able to run Half-Life 2 and CS:Source with it.

Any ideas?[/QUOTE]
 I can confirm the same error using Hoary adm64 with amd64-default kernel and nvidia-glx, all current. I tried all the hacks in the bugzilla post. No luck.
One note is that Doom3 and UT2004 run fine, and quake-smp works as a workaround.

---

### Post by Pse on 2005-03-14
OK, I've resurrected this thread 'cause I've started to get into trying to get ET to work under AMD64 without chrooting =)
I've made the game start using the software renderer without chrooting (yeah, slow as hell).
Apparently, libGL.so.1 tells the game to start in that mode. Using fglrx_dri.so as the OpenGL driver makes the game forget about Software Rendering but still gets a Signal 11 and exits.
Subterrific, can you post an update on any progress or new discoveries you've made since the last post?
Oh, BTW, I have already tried everything (almost) discussed in the Bugzilla pages for this bug, so this is also a problem with ATI cards.

[EDIT] My guess is that we're getting some sort of dependency conflict. ET may be trying to use important libraries from /usr/lib thinking they are 32-bit. As of now, I don't know about a way to change this behaviour...I wonder if there is some sort of wrapper for this...mmm... My first candidate to wrap is glibc...

---

### Post by subterrific on 2005-03-14
No progress on my end. I only know that it currently works fine with Gentoo amd64 and they are using the same lib32/lib64/lib layout as Ubuntu. My only guess is that is has something to do with Ubuntu compiling 32bit and 64bit libraries differently. Possibly something to do with TLS/NPTL differences.

---

### Post by Pse on 2005-03-15
Subterrific, you should check the [Quake3 thread](http://www.ubuntuforums.org/showthread.php?t=19843&page=2), as I've gotten ET to run under AMD64 without chrooting using Hardware Acceleration. I've read that you have an nVidia card...so, you should look for nVidia's 32-bit OpenGL DRI driver and install it to the path that's mentioned in my last post for ATI's cards. If you're successful, then I'll update my instructions!

[EDIT] I've downloaded nVidia's 32-bit driver...go to the aforementioned thread and try what my new post says, to see if it helps you.

---

### Post by Ironi on 2005-05-28
[QUOTE=norfenstein]For the record, I'm getting this same problem on Warty with a P4. It doesn't happen immediately though, I can start Quake 3 and run it fine for a while before having it crash spontaneously. This only started happening recently but I have no idea what I could have done to make it start.[/QUOTE]
Did you ever resolve this problem? I'm also experiencing it on my P4 with breezy and nVidia's driver (7174)...

---

### Post by hammett111 on 2005-05-28
I followed their guides mate and I got quake3-smp to work a beauty however it has a problem, I cannot get the game to save that I have entered the CD key, or save any of the screen settings/game settings I have done AND when I exit back to the desktop the screen resoltuion is changed. I am working on these problems ASAP!! Will post how I go:

To get Quake3-smp running do this

If you have an Nvidia card go to the nvidia site and download the 32bit drivers for the kernel you have.

Extract the downloaded .run file only "filename" --extract--only
Then copy the files "libGLcore.so.1.0.7167" file and the "libGL.so.1.0.7167" file from "...[place where you unpacked]/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/lib" to "/usr/X11R6/lib32/modules/dri". Create the directory if needed.

THEN...
Edit the Quake3-smp script by adding:

LIBGL_DRIVER_PATH=/usr/X11R6/lib:/usr/X11R6/lib32
LIBGL_DRIVER_PATH=/usr/X11R6/lib/nvidia:/usr/X11R6/lib32/nvidia

It will look something like this

#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
export LIBGL_DRIVERS_DIR=/usr/X11R6/lib32/modules/dri
export LD_LIBRARY_PATH=/usr/lib32:$LD_LIBRARY_PATH:.

Then exit everything, except your terminal and type quake3-smp and WALLAH!!!!
Then you'll run into my problems maybe :-)

Cheers
Q

---

### Post by ripntime on 2007-03-05
hammett111

[I followed their guides mate and I got quake3-smp to work a beauty however it has a problem, I cannot get the game to save that I have entered the CD key, or save any of the screen settings/game settings I have done AND when I exit back to the desktop the screen resoltuion is changed. I am working on these problems ASAP!! Will post how I go:]

I think your CD KEY problem might be that you once ran quake3 installer with the [sudo] command then went straight to play when the installer finished and it's now owned by root,  look in your .q3a in your home dir and check the permissions on the file q3key
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

