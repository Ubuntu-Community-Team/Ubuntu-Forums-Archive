---
title: "cedega in 32bit chroot: nothing happens"
date: 2005-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by zertox on 2005-01-16
I followed this guide to create my 32 bit chroot: [Building_a_clean_32bit_chroot_with_debbootstrap](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap)
except for the do_dchroot part.  I dchroot -d manually

now when i try to run anything  
for example; 
~ $ cedega /media/cdrom0/AutoRun.exe

thats all i see.  nothing happens. I tried it with other games and no luck.
when i "ctrl+C" to stop the process it keeps running in the background .. i cant kill it at all.

i ran Point2play and that works... but if i try to run a game with that i get the same result: nothing happens

glxgears works in the dchroot env.  mounting works too.. 

Any idea what this could cause and how to solve it?
Thanks

---

### Post by Dylanby on 2005-01-16
I have a similar problem with not being able to access my dvdrw from within the chroot.

If I copy the contents of the game disc to my hard drive (outside of the chroot) I can install it with Point2Play.

I'm just a newbie but I have a suspicion it has something to do with hal/dbus/gnomevfs & sockets.
Then again I could be wrong.

---

### Post by zertox on 2005-01-17
[QUOTE=Dylanby]I have a similar problem with not being able to access my dvdrw from within the chroot.

[/QUOTE]

Did you try to 
mount the drive outside root
unmount the /var/chroot/media/cdrom
mount /var/chroot/media/cdrom

that works for me for accessing my dvdrw drive

---

### Post by Dylanby on 2005-01-17
I actually did try the manual way & it did work.

---

### Post by subterrific on 2005-01-17
I installed cedega without a 32bit chroot and it works great. I've been running Steam, Half-Life 2, and CS:Source over a month now. I've been wanting to make a guide and create a dpkg for easy install, but I haven't had time yet. Here are my notes on what I did:

```
wget http://archive.ubuntulinux.org/ubuntu/pool/main/libp/libpng3/libpng12-0_1.2.8beta5-2_i386.deb
mkdir tmp
dpkg-deb -x libpng12-0_1.2.8beta5-2_i386.deb tmp/
mv tmp/usr/lib/libpng12.so.0* /usr/lib32/
ln -s /usr/lib32/libpng12.so.0.1.2.8beta5 /usr/lib32/libpng.so.3

wget http://archive.ubuntulinux.org/ubuntu/pool/main/x/xrender/libxrender1_0.9.0-0ubuntu3_i386.deb
mv tmp/usr/lib/libXrender.so.1* /usr/lib32/

dpkg --force-architecture --force-depends -i cedega_4.1.1-1_i386.deb
dpkg --force-architecture -i transgaming-fontinstaller_1.0_i386.deb

edit /usr/bin/cedega to add /lib32:/usr/lib32 to LD_LIBRARY_PATH
```

---

### Post by Psy on 2005-01-19
Thanks a lot! Now I also have a working cedega install without a chroot.  :grin:

---

### Post by dmatrix on 2005-01-19
Excellent I will have to test this. I am the original person that wrote up the 32bit chroot howto for Ubuntu/Debian on the TG Wiki. I will update it with these details after my testing.

If this works great then all I need a 32bit chroot for now is Firefox + Flash + mplayer/w32codecs. How hard would it be to get all the right 32bit libs in place for this? If I can accomplish a Firefox 32bit then I could rid myself of this 32bit chroot.

As well it sure would be nice if there was some debs to accomplish the same feat.

---

### Post by subterrific on 2005-01-21
I started learning how to create dpkg's, but I've been too busy the past few weeks to finish.

There are several things to note. Following my instructions you are polluting your system with files not controlled by package management. Since it is only one library, I don't think it is that big of a deal, but you certainly wouldn't want to try to install a large number of files this way. The Debian/Ubuntu developers are working on dpkg changes for "multiarch" package support to handle systems like amd64 that are able to execute binaries for multiple architectures (amd64 and i386). Gentoo developers are working on something similar for portage. So at some point there won't be any need for a 32bit chroot.

We could also submit a bug report to Ubuntu bugzilla asking for libpng to be added to the ia32-libs package.

I'd also like to note that I'm not able to run quake3 or ET on amd64 Hoary without a 32bit chroot. I've created a thread [http://ubuntuforums.org/showthread.php?t=11539](http://ubuntuforums.org/showthread.php?t=11539)  about it and opened a bug report. If anyone else has this issue, please post to the forum thread or bugzilla comments. I am 100% possitive that running quake3 and ET without a chroot is possible because I was able to do it on Gentoo. It worries me that I'm able to run win32 games, but not native linux games.

---

### Post by fromoze on 2005-01-22
I've problem with the non-chroot methode. I can't find the version you use of libxrender, may be is something like like that, but cedega doesn't find the hardware acceleration. The games starts, but too slow :)

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

Does anyone have the same problem??

---

### Post by subterrific on 2005-01-22
My method works for nvidia drivers, which doesn't use DRI. Since I don't have a card with DRI drivers that do 3d I can only guess, but here are a few guesses:

1) try adding this to the cedega script or just setting it in your shell before you run cedega:
export LIBGL_DRIVER_PATH=/usr/X11R6/lib/modules/dri:/usr/X11R6/lib32/modules/dri

2) maybe you need to install another 32bit lib similar to libXrender, something like libXdri? compare the /usr/X11R6/lib64 and lib32 directories to see if any libs missing from lib32 that look related.

---

### Post by fromoze on 2005-01-22
Well, my card is a gforce fx5200... I think it doesn't use dri;  I didn't think about before... I'll try to fix but, some help, would be nice :)

::EDITO::

More info, I just want to play Max Payne (on 32bit it works on wine)  and I'm on warty... but upgrading to Hoary, may be Xorg let it be

---

### Post by fromoze on 2005-01-23
IT ROCKS!! :D Just after upgrading to hoary every thing is going NIIIIIIICE! I'm shocked, now mi fx5200 gets 

603 frames in 5.0 seconds = 120.600 FPS

Before, just 530/5.0 :D

... and Max Payne now 'RUNS' I mean, literaly, Max runs along his killing way :)

Woah, and I like the new gnome and feeling the 64bit power. With Warty, I didn't see too much diferences between 32 and 64 bits, may wrong configuration, but now programs really speedup! I'm here to stay.

Yes, I'm really happy! Thanks ubuntu =D>

---

### Post by fromoze on 2005-02-04
Problems again :( Have you play Starcraft using cedega doing this trick?  I can't get starcraft working. I read abour x's config, but first I'd like to now if there's problems with 64 bits... 

... I don't like the game, is just because the friends on the appartement ask me to play with them ;)

---

### Post by dmatrix on 2005-02-05
Awesome. This method works well. On Hoary AMD64 I only needed to do a couple things as it appears the ia32-libs-gtk package for OO.org has the libpng and libXrender libraries included.

#Make sure libpng3 is all good
sudo apt-get install libpng3
sudo ln -s /usr/lib32/libpng12.so.0.1.2.5 /usr/lib32/libpng.so.3
#Install cedega and transgaming packages
sudo dpkg --force-architecture -i transgaming*
sudo dpkg --force-architecture --force-depends -i cedega*
sudo dpkg --force-architecture -i point2play-small*
#Edit /usr/bin/cedega to find lib32
Add: /lib32:/usr/lib32 to the $LD_LIBRARY_PATH

I tested with World of Warcraft, Half Life 2/Steam and a few other win32 games I had on my hard drive, everything appears to be working great.

---

### Post by subterrific on 2005-02-06
I did an update in Hoary last night that broke cedega for me. It segfaults on launch now. I'm still trying to track down what happened. Is anyone else using cedega without a chroot and having this problem now?

I wasn't really paying attention to what got updated, haven't looking for a log yet. I did notice that a lot of xorg packages were updated so I'm wondering if it might have something to do with libXrender.

---

