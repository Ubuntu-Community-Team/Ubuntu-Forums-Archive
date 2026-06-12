---
title: "wine error Segmentation fault (core dumped)"
date: 2007-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by darknightuk on 2007-06-09
am having problems getting wine to run i've compiled that latest and tried the latest deb from winehq but i get an error Segmentation fault (core dumped) when i try to run a program or even winecfg, any suggestions?

edit:-does the above in all 64bit wine versions and ALL forced i386 versions

---

### Post by darknightuk on 2007-06-09
done a clean install and installed from the wine repo and everything is working now dunno why i did nothing diff as far as i know, the more i use this 64bit ubuntu the more i think it's beta quality at best more attention needs to be paid here we've got a unique opportunity now to beat Microsoft to the 64bit desktop and canonical are wasting it!!!

---

### Post by penvzila on 2007-07-01
I'm having the same problem, but with the default repo versions as well.

---

### Post by praxis22 on 2007-07-01
A segmentation fault happens when a program tries to write across a memory boundary, or outside of it's mapped area.

It's a very basic program error.

Did you recompile wine properly for the intended platform?

You do realise that if you compile wine in 64bit you can only run 64bit windows binaries, right?

---

### Post by penvzila on 2007-07-19
> **praxis22 said:**
> 
You do realise that if you compile wine in 64bit you can only run 64bit windows binaries, right?

That doesn't sound right.

---

### Post by revolution_mac_usr on 2007-07-22
If compiled properly it should run x86-64 code fine. Unless it's something weird like an Itanium o.O

---

### Post by lsoltero on 2007-07-31
I have the same problem...

Here is my config Quad Mac Pro Ubunty 7.04

I added the following lines to sources.list

## WineHQ - Ubuntu 7.04 "Feisty Fawn"
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

and did an apt-get install wine

winecfg core dumps.

I then downloaded the tar ball and tried to compile it using 

[http://wiki.winehq.org/WineOn64bit#head-08d4087d863019523214064680fcf26721c9a1af](http://wiki.winehq.org/WineOn64bit#head-08d4087d863019523214064680fcf26721c9a1af)

and

[http://ubuntuforums.org/showthread.php?t=291620&page=3](http://ubuntuforums.org/showthread.php?t=291620&page=3)

and the same result.  

I have a nagging suspicion that it has something to do with libicu36-dev_3.6

i have the 64bit version of the library installed.  I downloaded the 32bit deb from
[https://launchpad.net/ubuntu/feisty/i386/libicu36-dev/3.6-2build1](https://launchpad.net/ubuntu/feisty/i386/libicu36-dev/3.6-2build1)
extracted the libraries from it and moved them into /usr/lib32

I then did the following to make sure that we were using the correct library

edit the Makefile in wine-X.X.XX/dlls/gdi32/Makefile I used pico - you can use vi or text editor or whatever.

and modify the line with "EXTRALIBS" to read:

EXTRALIBS = /usr/lib32/libsicuuc.a /usr/lib/libsicudata.a -lstdc++ -lgcc_s

Still no go...

anyone have any ideas how to begin to debug this?  I suspect that people have been able to get it to work when doing a clean install by avoiding some library conflict.

Any thoughts? Sure would like to get this working.

--luis

---

### Post by MateaMatt on 2007-08-05
I did something similar to lsoltero and I couldn't get either the repo version or a self compiled version to work.  Each time when I typed winecfg I would get a segmentation fault.  Running Feisty Fawn 64bit on a Quad Core Intel CPU.

---

### Post by stmiller on 2007-08-05
> **praxis22 said:**
> A segmentation fault happens when a program tries to write across a memory boundary, or outside of it's mapped area.

It's a very basic program error.

Did you recompile wine properly for the intended platform?

You do realise that if you compile wine in 64bit you can only run 64bit windows binaries, right?

This is not true. 

But back to the topic: open synaptic and install all of the ia32 packages.

---

### Post by MateaMatt on 2007-08-05
Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=432604](http://ubuntuforums.org/showthread.php?t=432604)

I think the problem is between wine and the nvidia display driver.  After reinstalling the driver all of my segmentation faults appear to have disappeared (this with the package install).

---

### Post by leespa on 2007-08-08
i tried the following procedure and still dont make it far enough to reinstall nvidia drivers.

it segfaults at wineprefixcreate. :(

installing from official repo, installed all ia32* packages available, even did a apt-get build-dep wine to dload 330 mb of packages and same grief...

========================

sudo apt-get remove wine
sudo apt-get install wine
sudo apt-get install kde-guidance
wineprefixcreate
winecfg (then close)
wineconfig (then close)
mkdir ~/.wine/drive_c/windows/profiles
mkdir ~/.wine/drive_c/windows/profiles/$USER

Then reinstall your NVIDIA driver.
Not sure why, but this seems to fix it.

---

### Post by simon2490 on 2007-08-15
i tried all this as still get the same core dump...i am a newbie to linux so be gentle please.

i am running 
gcard gts8800 BFG  latest drivers

---

### Post by revenant138 on 2007-08-18
I'm having the same problem. tried apt sources and right from the winehq site. running amd64. want to get wow going \\:D/

---

### Post by creatorlarry on 2007-12-20
I had the same problem. I was running winecvs on 64 bit gutsy gibbon with nVidia beta driver.

Though it seemed bizarre to me, but reinstalling nVidia beta driver do make wine work. I can comfirm this.

While installing, the driver install said that some of the previous installed file was modified. This is really a strange problem.

---

### Post by SorinN on 2008-02-17
Hardy Heron up to date. wine 0.9.55 ==  Segmentation core dump.
No way to reinstall or compile or install from pre_prepaired debs.

then I go to [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) 
I downloaded wine_0.9.54~winehq0~ubuntu~7.10-1_i386.deb (for Gutsy)
and ..voila    All windows apps. back again.

Consider this step as a  solution until the good guys will erase the bug

---

### Post by soxs on 2008-02-17
> **praxis22 said:**
> 
You do realise that if you compile wine in 64bit you can only run 64bit windows binaries, right?
Wrong, wine will always stay 32 bit, no matter if you compile it on 64 or 32 bit os, it will just point to the right libs and *shloud* work correctly.

Btw. I have the exact same problem: No matter what I do I get: ```
~$ winecfg
Segmentation fault (core dumped)

``` I did 2 fresh installs, tried compiling myself, the gutsy repo from winehq.org and finally I use the one from the ubuntu hardy repo. But always get that error.

EDIT: wine 0.9.54 nor 0.9.53 nor any previous verions are an real option, I need the up-to-date dx9 support... HL2, TF2

---

### Post by another_sam on 2008-02-27
same problem here.

---

### Post by bismark on 2008-03-01
> **SorinN said:**
> Hardy Heron up to date. wine 0.9.55 ==  

then I go to [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) 
I downloaded wine_0.9.54~winehq0~ubuntu~7.10-1_i386.deb (for Gutsy)
and ..voila    All windows apps. back again.

Consider this step as a  solution until the good guys will erase the bug

Thanks, this worked.  I reverted back to the gutsy 0.9.54 version and it seems to be working.

---

