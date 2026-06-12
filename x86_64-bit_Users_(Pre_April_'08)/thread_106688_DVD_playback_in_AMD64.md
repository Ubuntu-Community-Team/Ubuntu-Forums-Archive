---
title: "DVD playback in AMD64"
date: 2005-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by handy on 2005-12-21
I installed "Automatix" & the "non-free audio/video codecs", I still could not play commercial DVDs?
I tried with both Totem & VLC.
So, after a little wiki roaming I found the following:

================================
Playing DVD's

Most commercial DVDs are encrypted with CSS (the Content Scrambling System). The movie players provided in Ubuntu are capable of reading DVDs that are not encrypted. If it is legal for you to circumvent CSS, then you can enable reading encrypted DVDs in vlc, mplayer, xine and totem-xine by installing libdvdcss2. Type in a terminal:

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

================================

I followed the instructions, checking for the installation of 3 required files, (you will see it if you do it) which were allready installed in my case.
  
A "C" compiler is required, I used "GCC 4:4.0.1-3".

It did it's thing & now DVD's play on Totem & VLC **[EDIT:] & gXine** ;-)

Wonderful  :) 

handy

---

### Post by DaveHope on 2005-12-21
Thanks! This should really be added into the Wiki or pinned :)

---

### Post by John Jason Jordan on 2005-12-21
[QUOTE=DaveHope]Thanks! This should really be added into the Wiki or pinned :)[/QUOTE]
Ubuntu-64 Breezy

I have installed gxine, mplayer, vlc and totem. Here is what happens when I try to launch them with a commercial DVD (a movie bought at Wal-Mart) in the drive:

gxine: window opens with Welcome screen. Regardless of whether I go through the wizards or not, as soon as I click on the Close button for the Welcome screen gxine displays something and then quits. It quits so fast I can't read what it displayed.

mplayer: The little control panel thing says "No media opened." Using the top button on the round thingy I try to select a file. But no matter what I try to select I get something else. Navigation is broken. I've never been able to get it to read the DVD drive.

vlc: Both Video and Navigation say "empty." If I go to File > Open File it can't seem to see anything in the DVD drive. I've poked at it for half an hour but can't figure out any way to tell it to look in the DVD drive.

totem: Appears on the screen, displays something too quickly to read it, then closes down.

I did exactly as Handy did, and everything seemed to install OK, but it made no difference.

---

### Post by handy on 2005-12-21
MPlayer, doesn't work for me either.      I havn't bothered trying to fix it.  
Does MPlayer work on AMD64?  I don't need MPlayer anyway I'll uninstall it.

I  tested VLC with a DVD residing on an ntfs drive.  It needs to be configured to work with my DVD drive, not done yet.  The VLC doc's aren't much help.
I would think that my VLC problem is to do with my "fstab" file, & how I point VLC at the DVD drive.  I want to sort out the VLC & DVD disks issue, because I like the features of VLC.  Any suggestions are welcome?

My fstab follows:
===================================================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc1	/media/winxp	ntfs	umask=0222	0	0
/dev/hdc5	/media/winwork	ntfs	umask=0222	0	0
/dev/hdc6	/media/winlin	vfat	umask=0000	0	0
/dev/sda1	/media/winbfast	ntfs	umask=0222	0	0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
====================================================

Totem works fine with disks in the DVD drive?

[Edit]  "gxine" works perfectly as well...

Cheers,

handy

---

### Post by scunc_dvl on 2005-12-22
D'oh, I shouldn't have done this. It broke a slightly buggy but WORKING install of Mplayer, and Totem still won't read DVDs the same way. Must UNDO!! x.x

I'll throw in my /etc/fstab, since I find so many Ubuntu 64 bugs on my Nforce-4 are with filesystems (1. won't mount a floppy drive since I switched to 64 bit, 2. DOS filesystems are buggy, and won't read some CD-ROMs or run in Dosbox properly)

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

64 bit has been so frustrating, I might as well switch back to 32 bit for a year, waiting for badram-64bit (I am just using mem=*xx* which is okay) , 32-bit graphics compatibility libraries...workarounds aren't working and every single DOOM old and new does not work :/

------(EDIT)
Oops that was the wrong DVD I tested, the patch didn't affect MPLAYER like I falsely thought. Patch still did nothing for me though, and that DVD, I have no hope of playing in Linux until the update fairy(TM) magically fixes it :P

---

### Post by John Jason Jordan on 2005-12-23
I've been thinking about this some more. As I noted previously, vlc and mplayer are just plain broken on my Ubuntu-64 Breezy computer. However, totem and gxine seem to work, but they both do the same thing -- that is, they open, display something on the screen too fast to read, and then disappear.

So what I'm thinking is that there is someplace where Linux stores error messages. Like what those two programs display on the screen might be logged somewhere and I can access the log to see what they said. Then maybe I could get a clue about what is wrong. However, I'm way too green at this Linux thing to know what to say on the command line to call up the log, if it even exists. Does anyone know how to do it?

---

### Post by MighMoS on 2005-12-25
I also had to apt-get install fakeroot.  You may want to add that to the install line.

---

### Post by handy on 2006-01-02
MPlayer has a 64bit option now, I installed it to find it still crashing?
I'll check out their site & see how to sort it out.

It's good news for sure...:KS 

handy

---

### Post by John Jason Jordan on 2006-01-02
[QUOTE=handy]MPlayer has a 64bit option now, I installed it to find it still crashing?
I'll check out their site & see how to sort it out. handy[/QUOTE]
Thanks for the alert. I just installed it. (Actually, already had Mplayer installed, but according to Synaptic it wasn't the new AMD64 version, so I uninstalled it first.)

After installing the AMD64 version I typed "mplayer" on a command line, and got a list of options. But before the list of options it said:
```
MPlayer 1.0pre6-3.3.6 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer (Family: 8, Stepping: 10)
Detected cache-line size is 64 bytes
Cannot test OS support for SSE, disabling to be safe.
```
So now the question is, what is SSE? How do I find out if I have it? If I do not have it, how can I get it and how can I tell Breezy-64 that it is installed?

---

### Post by ruudiculus on 2006-01-02
SSE is a feature which may or may not be in your processor hardware. You can't install it like software. I don't exactly know WHAT it does, but it probably has something to do with enhanced video performance on your machine (working very fast with floating point numbers for example).

Anyway, with the Gnome Device Manager you can't figure out whether you have it or not. But KDE has a program "Info Center" in which you can select the processor and look at its so called 'flags'. If SSE is mentioned there your CPU has this hardware feature.

Still following me?

Well I don't exactly know how to enable it in the video software you use. I couldn't find it in xine/totem anyway. So Maybe it is more a question of having an up-to-date kernel? 2.6+ or so.

That question can better be answered by somebody else ;)

---

### Post by John Jason Jordan on 2006-01-02
[QUOTE=ruudiculus]SSE is a feature which may or may not be in your processor hardware. You can't install it like software. I don't exactly know WHAT it does, but it probably has something to do with enhanced video performance on your machine (working very fast with floating point numbers for example)[/QUOTE]
Thanks. I've since been googling and evidently the lack of SSE is not the problem. Using SSE is just an option Mplayer was looking for, and it should run without it.

The problem turned out to be that I should have typed "gmplayer," not "mplayer." When I typed "gmplayer" it brought up the familiar Mplayer screen and control panel thingy. And this time there was no error on the screen about not finding something.

However, it still can't seem to find the DVD drive. It insists there is no media loaded and I can't figure out how to tell it that there is media in the drive. When I type "gmplayer" I get the following"
```
MPlayer 1.0pre6-3.3.6 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer (Family: 8, Stepping: 10)
Detected cache-line size is 64 bytes
Cannot test OS support for SSE, disabling to be safe.
vo: X11 running at 1680x1050 with depth 24 and 32 bpp (":0.0" => local display)
86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
```
The first error seems to be the "Linux RTC..." line. Not sure if the next line is a suggestion to fix it, or a different error. In any event, I don't know anything about startup scripts. I do know how to edit things with Gedit, though.
Then there seems to be a missing joystick. That could be because I don't have a joystick. :)
Then there is the LIRC support problem. I don't know what that is all about. Maybe this is why the control panel thingy doesn't work? Is the control panel thingy the "joystick" (the thing that looks like it was designed as part of a Teletubbies set)?

It would also be nice if that control panel thingy was usable by a human. Like balloon popups to explain what the buttons do. And a bigger skin so I could actually see it. But I can deal with that later.

---

### Post by dna on 2006-01-02
LIRC = Linux infrared remote-control...not important.

Looks like you don't have your cd/dvd player set up properly. If you can play other videos and just not dvds then that's what it probably is. The little wrench looking icon, preferences=>Misc.

---

### Post by John Jason Jordan on 2006-01-03
[QUOTE=dna]Looks like you don't have your cd/dvd player set up properly. If you can play other videos and just not dvds then that's what it probably is. The little wrench looking icon, preferences=>Misc.[/QUOTE]
OK. But how do I fix it? What do I put in Preferences > Misc?

I assume you are referring to the bottom two lines, where I am to put in the CD-ROM device and the DVD device. I changed them both to /media/cdrom0, buth that didn't change anything. This is a laptop with a DVD+RW drive. I have used it to burn files to a DVD, and it works fine reading data DVDs (e.g., Linux distro DVDs). Perhaps /media/cdrom0 is the wrong syntax? I am new to Linux and don't understand these things, although I am trying to learn.

Also, as for "if you can play other videos and just not dvds," well, I don't have any other videos, so I'm not sure it really is the DVD drive. I don't have any way to test that issue.

And as for the other items on that dialog window, Not being a video enthusiast, I have no idea what most of them are referring to. I don't know what postprocessing is, or auto quality, whether the cache (set to 1024) is appropriate, or what Autosync is. I'm not sure I want to know either. I just want to be able to buy a DVD of a movie, slap it in the drive, and watch the movie I paid for on the computer I paid for.

OK, that was so Windows-user-like of me. I do want to learn Linux. But at the same time I want it to work without requiring me to get a degree in Comp Sci. All my friends watch DVDs on their computers, and some of them barely know how to turn it on. Why can't I? 

I hope someone can help.

---

### Post by handy on 2006-01-03
JJJ, can you paste a copy of your /etc/fstab file for us to have a look at please.

It's 1:47 am & time for bed, I'll look here tomorrow (oops, I forgot it's allready tomorrow - who said it never comes?) & see if anything is obvious.

Cheers,

handy

---

### Post by dissdigg on 2006-01-03
Thanks for the post.

I can watch my DVDs now, but they play very choppy.  gxine or totem are only using about 20% CPU.  Seems like it's a read buffering/dvd drive problem because if I pause the video and restart it, it plays fine for a few seconds (cached data?) until the dvd drive spins up again to be read again - then it gets skippy or choppy playback, pretty much unwatchable.  Any ideas?

---

### Post by John Jason Jordan on 2006-01-03
[QUOTE=handy]JJJ, can you paste a copy of your /etc/fstab file for us to have a look at please.[/QUOTE]
Here it is:
```
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/sda2       /media/iPod     vfat    rw,user,noauto  0       0
#chroot 32 bits
/home /chroot/breezy/32bits/home none bind 0 0
/tmp /chroot/breezy/32bits/tmp none bind 0 0
/dev /chroot/breezy/32bits/dev none bind 0 0
/proc /chroot/breezy/32bits/proc proc defaults 0 0
/media/cdrom0 /chroot/breezy/32bits/media/cdrom0 none bind 0 0
/media/floppy0 /chroot/breezy/32bits/media/floppy0 none bind 0 0
/usr/share/fonts /chroot/breezy/32bits/usr/share/fonts none bind 0 0
```

I hope that helps. Thanks in advance for any further suggestions.

---

### Post by handy on 2006-01-05
Hi JJJ, 

I can't see any problems with your **fstab** file.

I expect your pretty well over **this** by now.

The only thing that I can suggest, ('cause I'm a Ubuntu noob, 2) is if you can get hold of a non-protected DVD, (this is the easier way) & copy it, or 1 or more **.vob** files onto your /home/temp or something, & play them with **VLC Media Player**, which is pretty intuitive for this kind of thing.

The hard way:  Is to rip a protected DVD onto your drive & play that with **VLC Media Player.**

You should then be able to get closer to determining if this is possibly a hardware problem that you have here.

I understand, this stuff, when it goes on can become a real pain.  We have to decide if the results are worth the cost?

If you choose to try playing the .vob file(s), let us know how you go?
 
All the best.  :KS 

handy

---

