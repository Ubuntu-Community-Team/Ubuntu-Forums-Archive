---
title: "using 32 bit chrooted wine in ubuntu 64"
date: 2012-10-28
forum: Wine
---

### Post by terrifiedkiller on 2012-10-28
hello i am attempting to build a patched up wine from source so i can play league of legends properly on linux. I came accross a few issues. I have followed the instructions on this guide [http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit") with the exception of manually downloading the source and patching it.

currently whenever i try to launch something through wine or run wincfg i get this message

```
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

i also have a second question. In the guide it tells me to use programs from outside the chroot i would have to install wine seperately. but wouldnt that remove the purpose of building the 32 bit wine in the first place?

---

### Post by thatguruguy on 2012-10-28
I'm trying to understand why you're doing what you're doing. Why not just install Wine from the Wine repository, as normal? If it doesn't automatically pull all the 32 bit packages, installing them is as simple as opening a terminal and typing
```
sudo apt-get install ia32-libs
```

---

### Post by terrifiedkiller on 2012-10-28
> **thatguruguy said:**
> I'm trying to understand why you're doing what you're doing. Why not just install Wine from the Wine repository, as normal? If it doesn't automatically pull all the 32 bit packages, installing them is as simple as opening a terminal and typing
```
sudo apt-get install ia32-libs
```

im doing what im doing cause im using a patched version of wine so i can get a game i want to get running to run on it rather then have to deal with the issues it would have had otherwise the patches are to get what doesn't work in current versions of wine work on league of legends

---

### Post by Mr. Hibba on 2012-11-26
> **terrifiedkiller said:**
> hello i am attempting to build a patched up wine from source so i can play league of legends properly on linux. I came accross a few issues. I have followed the instructions on this guide [http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit") with the exception of manually downloading the source and patching it.

currently whenever i try to launch something through wine or run wincfg i get this message

```
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

i also have a second question. In the guide it tells me to use programs from outside the chroot i would have to install wine seperately. but wouldnt that remove the purpose of building the 32 bit wine in the first place?


Hi, 

I'm doing something sort of similar to you, except with Linux Mint being my host OS.  What I do is, after Wine is built and ready to go in the chroot, exit the chroot and access the Wine executable from my main OS (by the way, I'd recommend installing the package thatguruguy mentioned if you haven't already; not sure 32-bit Wine will work without it).

So, for example, I have my chroot in /mnt/SDCARD/chroot.  To use the Wine version that I built there, I would use /mnt/SDCARD/chroot/wine-git/wine from my main OS.

Hope this helps, and let me know if you have any questions. :)

---

