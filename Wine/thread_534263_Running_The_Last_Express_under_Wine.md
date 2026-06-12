---
title: "Running The Last Express under Wine"
date: 2007-08-25
forum: Wine
---

### Post by imjustsomeguy72 on 2007-08-25
Hello

I'm trying to run the Smoking Car Productions game The Last Express under Wine. What little information there is under the Wine AppDB tells me it should be easy to get to run...

Installation worked fine. Executing the program gave me an error saying that it couldn't find the hard drive cache, but I got around this by using the autorun executable on the CD itself.

However, I got a DirectDraw error, which I traced back to my system running in too high a resolution (it requires 640x480 at 16-bit). I was unable to change the resolution from the native 1024x768 because my laptop is running an Intel Express Chipset. I followed advice else where and download the xorg-video-intel (or similar) program that gives control of resolution to the X window Manager, or something. I can now change res, however X reboots back to the login screen, at native resolution again. I am running via Wubi, which could perhaps be an issue? I posted on the Wubi forum. where I was told that it was likely not a Wubi issue

Any advice?

---

### Post by Black Sheep on 2010-09-08
This post is old enough to walk, but... were you successful?

Myself, I was able to install and run the game, but there are far too many graphical glitches for it to be playable.

Either way, a DOS version is also provided in the 1st CD, so you can simply use that one with the emulator DosBox. I have just copied the CD data over to the disk, and then mounted the thing with:
> mount c /home/.../express/disk
mount -t cdrom d /home/.../express/cd1
mount -t cdrom e /home/.../express/cd2
mount -t cdrom f /home/.../express/cd3

(The ellipsis indicates whatever path you want to use. You can use a relative path too, but then you can't run your BAT file from nautilus.)

You'll then have to install it: d:\dos\install. And from then on: c:\express\express

It will find the correct CD directory itself. I guess the game is programmed to iterate through your cd-drives, given that some people have more than one.

---

