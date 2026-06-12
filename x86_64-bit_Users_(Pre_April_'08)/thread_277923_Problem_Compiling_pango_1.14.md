---
title: "Problem Compiling pango 1.14"
date: 2006-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by TDSP on 2006-10-15
Hi, I'm new to Ubuntu (convert from Debian) and I've had my first major problem trying to get something working. I have a copy of the AMD 64 server build which I apted the KDE ubuntu-desktop into. I have some non-DRM windows media video files I'm trying to play, so I'm trying to do a source install of the totem xine front end (so I can manually install the codecs I need) and I'm in the process of installing dependencies for totem. I try to do a make on pango 1.14 and I get the following error: 

/usr/bin/ld: /usr/local/lib/libz.a(inflate.o): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libz.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[4]: *** [libpangoft2-1.0.la] Error 1
make[4]: Leaving directory `/home/arvad/Desktop/pango/pango-1.13.0/pango'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/arvad/Desktop/pango/pango-1.13.0/pango'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/arvad/Desktop/pango/pango-1.13.0/pango'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/arvad/Desktop/pango/pango-1.13.0'
make: *** [all] Error 2

I've tried googling, I've tried searching the forum, I've tried a lot of different stuff and I'm stuck ](*,) 

Am I crazy to be trying to a manual install like this (I've done it before on debian without problems :( )? Is this a known issue? Help! 

Thanks, 
-Doug

---

### Post by RAOF on 2006-10-15
You're trying to build from the latest xine, with the new ffmpeg wmv3 support, right?

Why is the build looking in /usr/local/lib?  Ubuntu doesn't install anything in there, and you can get zlib1g-dev which provides *libz.a*.  If you built that copy of libz from source, you probably haven't enabled building PIC code, which is required for x86-64 shared libraries.

---

### Post by TDSP on 2006-10-21
Sorry for the bump, I've been busy at work for a bit and haven't had time to deal with this issue ](*,) 

RAOF: yes, that's what I was trying to do. Unfortunately, that explaination is a bit beyond me. ;) I have no clue what PIC code is. Thanks for the explaination anyway. I found a .deb that automatically installed all that stuff for Kaffine and I got it working, so I was happy. 

I have a new issue though: If I leave the machine on overnight, it will have hard drive read errors and won't re-find the drive upon re-boot. Nothing seems to work (including rescue, etc) but it will allow me to re-install and once I do that the thing works 100% fine till I leave it on too long again ](*,) The only time this doesn't happen is when I'm using Win XP, which I can use for a PVR using sageTV, but I'd rather use Myth. I also found that if I unplug the thing and leave it for more than a minute, it will allow me to boot normaly until I run into the same issue. 

I've tried multiple drives from multiple manufacturers (Western Digital, Seagate and Hitachi) thinking it might have been a bad drive or conflicting drive firmware: No difference.  I am 100% clueless as to why this happens, and I'm guessing it's likely a linux specific thing :-k Motherboard is an Asus K8N with an NForce 3 250. 

Any ideas for me? ](*,) ](*,) ](*,)

---

### Post by RAOF on 2006-10-22
> **TDSP said:**
> ...
I have a new issue though: If I leave the machine on overnight, it will have hard drive read errors and won't re-find the drive upon re-boot. Nothing seems to work (including rescue, etc) but it will allow me to re-install and once I do that the thing works 100% fine till I leave it on too long again ](*,) The only time this doesn't happen is when I'm using Win XP, which I can use for a PVR using sageTV, but I'd rather use Myth. I also found that if I unplug the thing and leave it for more than a minute, it will allow me to boot normaly until I run into the same issue. 
...

That's crazy!  It seems that there's some wierdness in your disc controller, which the WinXP driver works around.  You should file a bug on [launchpad]("https://launchpad.net"), against **linux-source** with this information and as much extra stuff as you can.  Particularly, you should state that you can reproduce the problem.  The fix will probably not be quick, but by bringing it to the devs attention, they can at least look at it (and possibly just send it to kernel.org) :).

---

