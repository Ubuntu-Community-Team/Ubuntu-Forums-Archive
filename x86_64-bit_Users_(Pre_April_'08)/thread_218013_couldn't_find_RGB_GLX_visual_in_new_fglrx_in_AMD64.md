---
title: "couldn't find RGB GLX visual in new fglrx in AMD64"
date: 2006-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by rogeriovinhal on 2006-07-18
Hello, this is my first experience with AMD64 version of Kubuntu, but it soon looked to be a little had to make things right...

Starting from fglrx. I have a radeon 9600XT that worked very well with i386 and latest fglrx drivers.
I followed the same HOWTO to try to make it work on AMD64, but if I try to make an fglrxinfo, this is what I get:

```

Error: couldn't find RGB GLX visual!

```

I have searched a LOT for an answer to that, but I didn't get any answers with google and the forum...
Has anyone managed to get rid of this problem and can tell me how?

---

### Post by JerMe on 2006-07-18
Which drivers are you using?  You might have to do a little symlink magic to get the drivers to work.  Specifically, libGL.so.1.2 (and maybe libGL.so.1).

---

### Post by Kilz on 2006-07-18
I had to replace my monitor yesterday. So I had to battle the ati drivers because I was still using the 8.24.8 drivers and a rather old kernel.
First off the 64bit version of the 8.25.18 driver in the repos is one of the worst drivers ati has ever written imho. It was one of the reasons I didnt upgrade for so long. 
[I ended up following this howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually") after trying a few others and getting the same results when I tried glxgears to test it.
Just a note in case you have similar trouble. I noticed that when I tried to install xorg-driver-fglrx_8.26.18-1_amd64.deb I noticed that there was an error of not being able to replace the libGL.so.1.2 in /usrlib and /usr/lib32. I deleted the libs then and installed the package without errors. Then acceleration worked.

---

### Post by rogeriovinhal on 2006-07-18
I was trying the 8.26.18 version, but now I have just tried the 8.25.18 in the repos also, and it did exatcly the same problem.

I tried to delete all the "libGL"s and install again, I deleted every directory that had "fglrx" in it and reinstalled, and nothing seems to get me past this error with RGB GLX.

What is this error anyway? Seems that is not related to the driver version, as it should work with the repos out-of-the-box.

---

### Post by Kilz on 2006-07-18
> **rogeriovinhal said:**
> I was trying the 8.26.18 version, but now I have just tried the 8.25.18 in the repos also, and it did exatcly the same problem.

I tried to delete all the "libGL"s and install again, I deleted every directory that had "fglrx" in it and reinstalled, and nothing seems to get me past this error with RGB GLX.

What is this error anyway? Seems that is not related to the driver version, as it should work with the repos out-of-the-box.
I didn't suggest deleting all that. I don't suggest deleting anything but the 2 files mentioned because I am sure they are replaced. Sometimes deleting without knowing why is a bad thing.
I suggest rereading the howto I linked to, and looking at the troubleshooting sections below them. Also look at the terminal as things are installing, look for errors. I'm not sure why this isn't working for you, but it has worked for a lot of people.

---

### Post by rogeriovinhal on 2006-07-18
I tried to do exatcly what the HOWTO told again, and nothing different.

I think it may be a problem outside the drivers part, because EVERY driver gives the same error.
What is this RGB GLX, and why does glxinfo gives me only this output?
```

Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None

```

---

### Post by Kilz on 2006-07-18
> **rogeriovinhal said:**
> I tried to do exatcly what the HOWTO told again, and nothing different.

I think it may be a problem outside the drivers part, because EVERY driver gives the same error.
What is this RGB GLX, and why does glxinfo gives me only this output?
```

Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None

```

I'm not sure, my knowledge of this is only from banging my head into the wall for a day. ](*,) 
I will tell you I had nothing but trouble upgrading. I had to remove almost every fglrx package, source and the restricted modules. 
But that left me without a gui for a bit, I wouldn't suggest doing it that way to anyone. I'm lucky I have a small file server with a gui sitting next to my main comp. I was able to surf and get the reinstall info from a howto on it and type it into the the command line on my main comp. If not I would have been reinstalling.
Maybe someone else can give you some better ideas on how to fix this.

---

### Post by rogeriovinhal on 2006-07-19
I finally got it to work.
I don't know exactly what did the job because I did a lot of things at once, but I think that the main reason to it work is I deleting all libGLU.so and links, then installing fglrx drivers, then reinstalling the libglu packages.

---

### Post by xthaparian on 2007-01-10
GUYS I am very much excited to solve this problem after going through hundreds of GUIDE

The main Problem is the command

> [COLOR="Magenta"]sudo ./ati-driver-installer-xxxxxxx.x86_64.run --buildpkg Ubuntu/dapper[/COLOR]

With this command we are forcing ATI to create deb files using Original Ubuntu/dapper configuration, which the programmers of ATI has thought to be XORG version 6.8

Since now Dapper is using Xorg 7.0 , the Drivers will now work by using the above method, because we are forcing ati driver to build specific package for Dapper...which essentially means its thinking to use xorg 6.8

Now today I did this

> sudo ./ati-driver-installer-8.33.6-x86.x86_64.run

It open ATI driver windows and over there choose First Option (DONT USE DISTO SPECIFIC BUTTOn)

Hit continue

and then Choose Automatic installation...

And ATI driver build driver using your system Xorg which is 7.00 and BAM.......

Make sure your xorg.conf says fglrx and linux restricted modules are Disabled for fglrx

CTRL+DEL+BKSPACE

Bam....

Your 3d is working great ....

---

