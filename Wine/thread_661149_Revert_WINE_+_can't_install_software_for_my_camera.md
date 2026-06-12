---
title: "Revert WINE + can't install software for my camera"
date: 2008-01-07
forum: Wine
---

### Post by niethslim on 2008-01-07
I was messing around with WINE a little and replaced some of the files on the c:/ drive.
Is there any way to revert c:/  to a fresh-install state (I don't have any programs installed, yet)?
I also have some trouble installing a program for my camera, but first I want to make sure the problem is not caused by me messing around with WINE.

Thanks,

---

### Post by happyhamster on 2008-01-07
A way of doing that is deleting the entire .wine folder. After that, run:

winecfg

in a terminal to create a new one.

---

### Post by bonzodog on 2008-01-07
yes, just delete your ~/.wine dir.

When you next start wine, it will recreate it.

---

### Post by niethslim on 2008-01-07
Thanks for the replies, guys, worked perfectly.
Now for the camera software.
I'm trying to install "EOS Utility 1.1" from a "Canon Digital Camera Solutions Disk v30" disc (other programs are included in the installer, but I deselected them).
The program, as far as I understand, should allow me (at least under Windows or Mac OS X) to control my camera through the computer.
The install doesn't finish because of an error (I attached the error log).

Any way to make the program install properly, or a suggestion for a Linux program with similar functionality would be appreciated.

Thanks,

---

### Post by minoruhackerguy on 2008-03-12
As far as I know, it isn't possible to install the EOS solutions software to linux. I do know of several alternatives to get things working. (I'm currently trying to get my Rebel XT to work, so some things may not work.)

Ok, to have your camera connect to linux, you need to make sure you have gphoto. Then you need to see if your camera has remote capure support through Gphoto. Look at the fallowing website to see if it does. (PS: Things would be easier if you told us what camera you have. ;) )
[http://gphoto.sourceforge.net/doc/remote/](http://gphoto.sourceforge.net/doc/remote/)

Then, if you're cameras "remote capture" feature is supported by gphoto, you need to find something to capture pictures with. :)

If you have a powershot camera, you can use capture.
[http://capture.sourceforge.net/](http://capture.sourceforge.net/)

I'm a command line sort of guy, so I just use the built-in features of GPhoto. Look at the man page of gphoto for info on remote capture.

Now, for a replacement of things like zoombrowzer, I'd recommend Picasa. It's not Open Source, but it's free and VERY cool. Type in "Picasa Linux" in google for info. *It uses wine to run off of linux and has a self executing .bin file for easy install*

For RAW file management, you should use UFRaw. It's VERY nice, has everything that Photoshop does and has the ability to plugin to Gimp.


A more proprietary way of doing things would be to use VirtualBox and install windows. You could then use the "Ctrl+L" to have it kind of intergrate into your desktop. That way, you install the Canon utilities and Photoshop. (if you have it.) This might be the easiest way of doing things if you're not used to Linux and the Command line.

I myself will just stick with linux. :cool: I truly hate microsh--- I mean microsoft. ^_^;;; Oh, and, there might be a lot of other GUI front ends for Gphoto, but I haven't looked. 

PS: Gphoto probably won't bring up anything in the command line. It' will probably be listed as 'gphoto2'.

---

