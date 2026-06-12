---
title: "Encrypted DVD backing up"
date: 2006-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2006-07-12
Hi i wanted to backup some vob files from encrypted dvds but this doesn't seem possible under dapper 64 whatever i've tried.

i've tried dvd::rip
thoggen
vobcopy etc etc and nothing seems to work

also i've even tried dvddecrypter for windows under wine and this won't work either!

it must be easier than this? can anyone guide me please?

---

### Post by RAOF on 2006-07-12
I find it odd that dvddecrypter under wine wouldn't work.

Anyway, the first rule of getting useful responses on the Ubuntu forums is "post any error messages, please" :)

When you try the programs, what happens?  If you try them from a console, what errors get reported?

However, my first guess would be that you don't have libdvdcss installed.  That's the deCSS library, which decrypts the vobs.  I've got the latest version in my repository.  Check out (the mirror at) [ubuntu.moshen.de](ubuntu.moshen.de) for how to add the repository to your sources.list, then run
```

sudo aptitude update
sudo aptitude install libdvdcss

```

---

### Post by MetalMusicAddict on 2006-07-12
Which DVD is it? Some new DVDs use ARccOS. A new protection that (from what Ive seen) no rippers in linux have tackled yet.

---

### Post by jonah1980 on 2006-07-13
> **RAOF said:**
> I find it odd that dvddecrypter under wine wouldn't work.

Anyway, the first rule of getting useful responses on the Ubuntu forums is "post any error messages, please" :)

When you try the programs, what happens?  If you try them from a console, what errors get reported?

However, my first guess would be that you don't have libdvdcss installed.  That's the deCSS library, which decrypts the vobs.  I've got the latest version in my repository.  Check out (the mirror at) [ubuntu.moshen.de](ubuntu.moshen.de) for how to add the repository to your sources.list, then run
```

sudo aptitude update
sudo aptitude install libdvdcss

```

http://ubuntu.moshen.de/dists/dapper/{All/binary-amd64/Packages.gz: 404 Not Found
http://ubuntu.moshen.de/dists/dapper/Sections}/binary-amd64/Packages.gz: 404 Not Found

---

### Post by jonah1980 on 2006-07-13
> **MetalMusicAddict said:**
> Which DVD is it? Some new DVDs use ARccOS. A new protection that (from what Ive seen) no rippers in linux have tackled yet.

This is what i get from DVD Decrypter log:

I 10:44:30 DVD Decrypter Version 3.5.4.0 started!
I 10:44:30 Microsoft Windows NT Workstation 4.0 (4.0, Build 1381 : Service Pack 6a)
I 10:44:30 Initialising SPTI...
I 10:44:30 Searching for SCSI / ATAPI devices...
W 10:44:30 No devices detected!

---

### Post by RAOF on 2006-07-13
> **jonah1980 said:**
> http://ubuntu.moshen.de/dists/dapper/{All/binary-amd64/Packages.gz: 404 Not Found
http://ubuntu.moshen.de/dists/dapper/Sections}/binary-amd64/Packages.gz: 404 Not Found

Aaah, you've added the wrong thing.  Sorry.  You should replace what you put in with:
```
 
deb http://ubuntu.moshen.de/ dapper all
deb-src http://ubuntu.moshen.de/ dapper all

```

Then try again.

---

### Post by jonah1980 on 2006-07-13
ok so what do i need to do next?

i think i've got the newest ones, this is what happened:

jonah@jonah-desktop:~$ sudo aptitude install libdvdcss
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  ffmpeg libcairo2 libdrm-dev libdrm2 libgl1-mesa libgl1-mesa-dri libglitz1
  libglu1-mesa libgpod0 libtunepimp2c2a libwnck18 rhythmbox xserver-xgl
  xserver-xorg-driver-i810
0 packages upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by RAOF on 2006-07-13
Ok.  So it looks like you've lot libdvdcss.  Good.  Do any of the DVD-backup tools work now?  If not, could you run them from a terminal, and see what sort of errors get returned?

---

### Post by jonah1980 on 2006-07-13
well vobcopy looks good but doesn't get past 0% !!
-------------------------------------------------------

jonah@jonah-desktop:~$ vobcopy
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/hda
libdvdread: Using libdvdcss version 1.2.9 for DVD access
name of dvd: BROTHERS_GRIMM
There are 23 titles on this DVD.
There are 80 chapters on the dvd.
Most chapters has title 1 with 23 chapters.

There are 23 angles on this dvd.
Using Title: 1
Title has 23 chapters and 1 angles
Using Chapter: 1
Using Angle: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000002ca
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00017c41
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00026af8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002e6292
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e63f8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e6bad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00305880
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0038c7f3
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0

DVD-name: BROTHERS_GRIMM

Outputting to /home/jonah/BROTHERS_GRIMM1-1.vob

   0MB of 5628MB written (0 %)

---

### Post by Iesos on 2006-07-23
Hi, I have the same problem... I think.
When using vobcopy, it will get past 0% but it takes a loooong time! (it took 24 hours to get to 30% on my 7GB DVD).
But the relevant error is this (I suppose):

```
$ mplayer dvd://
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices  (Family: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
Couldn't open DVD device: /dev/dvd
[file] No filename
Failed to open dvd://

Exiting... (End of file)
```

Which was the error I got after adding the sources (the .de - ones) from this thread. And the following message I got before that

```
$ mplayer dvd://
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices  (Family: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://.
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread3/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
Reading disc structure, please wait...
There are 3 titles on this DVD.
There are 19 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
```

And this last error is very confusing since I've got libdvdrad3 installed (according to synaptic).

And I get all the same problems with mplayer/mencoder/thoggen and vobcopy & dvdbackup are just very slow.

---

### Post by JoWilly on 2006-07-23
dvdbackup (in the universe repo) has always worked fine for me.

---

### Post by jonah1980 on 2006-07-23
thanks for helping out guys, managed to get dvdshrink 3.2 working under wine, so now i can back a disc up to .iso and then just burn that. so i'm happy enough.

it's great cos i've got the 3 windows apps i need working, RAOF has added other stuff like scribus-ng and tellico - so i've got everything i need and no longer have windows or need it at all which is really liberating at last as i've been aiming to completely move over to linux for a while now.

---

### Post by one_stinky_bum on 2006-08-12
> **jonah1980 said:**
> thanks for helping out guys, managed to get dvdshrink 3.2 working under wine, so now i can back a disc up to .iso and then just burn that. so i'm happy enough..

How did you do it? I have the same "devices not recognized" error.

---

### Post by Kilz on 2006-08-12
> **one_stinky_bum said:**
> How did you do it? I have the same "devices not recognized" error.

How did you install/setup wine? You do know there is a great program called k9copy that has all of dvdshrinks functionality in the repositories.

---

### Post by one_stinky_bum on 2006-08-12
I used this: [http://mrbass.org/linux/ubuntu/dvdshrink/]("http://mrbass.org/linux/ubuntu/dvdshrink/")

I'll give k9copy a spin to see if it works as well as good ol shrink.

---

### Post by Kilz on 2006-08-12
> **one_stinky_bum said:**
> I used this: [http://mrbass.org/linux/ubuntu/dvdshrink/]("http://mrbass.org/linux/ubuntu/dvdshrink/")

I'll give k9copy a spin to see if it works as well as good ol shrink.

The reason I asked is that in 64bit Ubuntu those install insteructions dont work for wine. I wrote the howto and modified a setup script to do the rest of the setup. One of the things it dose is setup the drives. Are you running the amd64 version of Ubuntu?

---

### Post by Emerzen on 2006-08-12
I'd second k9copy, works great and much like DVDShrink.  You could also try Tovid, but it's not in the repo's.

---

### Post by one_stinky_bum on 2006-08-12
tried it, but I like DVD shrink better. I'm running Ubuntu 6.06 on a Centrino 1.7GHz.

---

### Post by Kilz on 2006-08-12
> **one_stinky_bum said:**
> tried it, but I like DVD shrink better. I'm running Ubuntu 6.06 on a Centrino 1.7GHz.

what version of Ubuntu i386 or amd64?

[QUOTE=Emerzen]
I'd second k9copy, works great and much like DVDShrink. You could also try Tovid, but it's not in the repo's.[/quote] I'm going to have to give that one a try. I much prefer Linux applications. I remember happily deleting dvdshrink from wine when I found k9copy. If I didn't have to absolutely positively have to have IE for 1 web site to get a check I would have removed wine long ago. Those windows programs are just plain ugly imho.

---

### Post by one_stinky_bum on 2006-08-12
x86 here ... I don't have any AMD boxes.

the canine copying program doesn't have the frame by frame deletion that DVDshrink has under the re-author mode.

---

### Post by Kilz on 2006-08-12
> **one_stinky_bum said:**
> x86 here ... I don't have any AMD boxes.

the canine copying program doesn't have the frame by frame deletion that DVDshrink has under the re-author mode.

You may have to setup the wine drives type winecfg in a terminal and click on the drives tab.

---

### Post by one_stinky_bum on 2006-08-12
Nope, no worky. winecfg doesn't fix it whether run as root or normal user. I still get the "no devices found" error.

---

### Post by Kilz on 2006-08-12
> **one_stinky_bum said:**
> Nope, no worky. winecfg doesn't fix it whether run as root or normal user. I still get the "no devices found" error.

Just running winecfg isnt going to do anything. You have to open winecfg , click on the drivers tab, and add the drives. Running as root isnt going to do anything but setup a wine folder in roots home.

---

### Post by one_stinky_bum on 2006-08-12
That's exactly what I did. winecfg brings up a configuration pane for wine and I made sure that the drives H, C, D, Z, E were what they were supposed to be (H-> linux home, C-> wine root, D->media/cdrom, E->media/cdrom0, Z->linux root). After doing that, I checked with DVDshrink and DVDDecrypter and both didn't see the CD drive. I tried with sudo just to see if it would give me a different result.

---

### Post by Kilz on 2006-08-12
> **one_stinky_bum said:**
> That's exactly what I did. winecfg brings up a configuration pane for wine and I made sure that the drives H, C, D, Z, E were what they were supposed to be (H-> linux home, C-> wine root, D->media/cdrom, E->media/cdrom0, Z->linux root). After doing that, I checked with DVDshrink and DVDDecrypter and both didn't see the CD drive. I tried with sudo just to see if it would give me a different result.

Maybe the [Wine application Database page]("http://appdb.winehq.org/appview.php?iVersionId=2230") can give you more info or a fix to get it working.

---

### Post by makadam on 2006-09-01
Hello

The following steps worked for me.
Configure first wine to have access to all needed drives.
Then insert a DVD into your drive. It will be automatically mounted into your system. Configure DVD Decryptor. 
1) Start DVD Decryptor
2) Go to the menu: Tools -> Settings
3) Select the tabe I/O
4) Check in Interface : ASPI - WINASP32.DLL and confirm this change with OK.
5) Your DVD Drive should appear in the main window under Source.

That should help.
I hope I could help.

---

### Post by one_stinky_bum on 2006-09-02
Doesn't work for me... no drives detected. I configured the drives in winecfg and DVDFabDecrypter can see them but DVDdecrypter doesn't. DVDFabDecrypter doesn't work well for me on Ubuntu though.

---

