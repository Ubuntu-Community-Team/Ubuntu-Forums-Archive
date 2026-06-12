---
title: "Firefox32 With Flashplayer 9 Problems"
date: 2007-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by jlacroix on 2007-04-10
I'm sure there are topics about flash in the 64-bit forum every day but I didn't see my problem asked yet.

On my machine I have the firefox that ships with Ubuntu64, and I also followed the instructions [here]("https://help.ubuntu.com/community/Firefox2AMD64Flash9Java") to install firefox32. Flash works fine so far except one problem, it freezes one out of every three times I play a flash video. When it freezes, the firefox window stops responding so I have to do a "force quit". I only really use flash with Youtube so I don't know if I have problems at other sites. 

I am using Ubuntu Feisty, however I had this same problem before with Edgy, I just didn't think to ask you guys until now. If all else fails I can live with this, its not the worse problem in the world but it would rock if I can get it fixed. If I get this fixed I'll probably use firefox32 for everything.

---

### Post by Kilz on 2007-04-10
> **jlacroix said:**
> I'm sure there are topics about flash in the 64-bit forum every day but I didn't see my problem asked yet.

On my machine I have the firefox that ships with Ubuntu64, and I also followed the instructions [here]("https://help.ubuntu.com/community/Firefox2AMD64Flash9Java") to install firefox32. Flash works fine so far except one problem, it freezes one out of every three times I play a flash video. When it freezes, the firefox window stops responding so I have to do a "force quit". I only really use flash with Youtube so I don't know if I have problems at other sites. 

I am using Ubuntu Feisty, however I had this same problem before with Edgy, I just didn't think to ask you guys until now. If all else fails I can live with this, its not the worse problem in the world but it would rock if I can get it fixed. If I get this fixed I'll probably use firefox32 for everything.

Look in my signature, run script, problem solved. But you may have to do a little editing to fix a few Feisty issues. There is a Feisty section on that page.

---

### Post by jlacroix on 2007-04-10
That did it! I watched like ten flash cartoons in a row and had no freezing. Thanks a zillion!!!

---

### Post by jlacroix on 2007-04-16
It looks like I spoke too soon. Firefox32 is freezing sometimes when I load a flash video/animation. I have to force quit it or end the process. I'm beginning to think there isn't a viable flash alternative for x64, is there a way to (permanently) fix this problem?

---

### Post by Kilz on 2007-04-17
> **jlacroix said:**
> It looks like I spoke too soon. Firefox32 is freezing sometimes when I load a flash video/animation. I have to force quit it or end the process. I'm beginning to think there isn't a viable flash alternative for x64, is there a way to (permanently) fix this problem?

What site is freezing, and animation?

---

### Post by jlacroix on 2007-04-17
As of right now, Youtube is the only site I go to with flash.

---

### Post by Kilz on 2007-04-17
> **jlacroix said:**
> As of right now, Youtube is the only site I go to with flash.

Would you please type in ```
about:plugins
``` then copy the macromedia flash section and paste it into a post here.

---

### Post by NullHead on 2007-04-18
Hay tried your script and it worked great up until the "Mplayer Multimedia plugin for Edgy" part.
it just said "mkdir: cannot create directory `/usr/lib/win32': File exists" then poof ... any ideas??

---

### Post by Kilz on 2007-04-18
> **NullHead said:**
> Hay tried your script and it worked great up until the "Mplayer Multimedia plugin for Edgy" part.
it just said "mkdir: cannot create directory `/usr/lib/win32': File exists" then poof ... any ideas??

Please open a terminal, enter in this command

```
ls -al /usr/lib/win32
```

Copy the results and paste them into a reply here.

---

### Post by NullHead on 2007-04-18
hear they are.

```
total 22050
drwxr-xr-x   2 root root    2200 2007-04-17 23:52 .
drwxr-xr-x 169 root root   59672 2007-04-18 00:19 ..
-rw-r--r--   1 root root   61952 2007-04-17 23:53 acelpdec.ax
-rw-r--r--   1 root root   38912 2007-04-17 23:53 alf2cd.acm
-rw-r--r--   1 root root  118784 2007-04-17 23:53 aslcodec_dshow.dll
-rw-r--r--   1 root root   95292 2007-04-17 23:53 atrac3.acm
-rwxr-xr-x   1 root root   64912 2007-04-17 23:53 atrc.so.6.0
-rw-r--r--   1 root root   92160 2007-04-17 23:53 AvidQTAVUICodec.qtx
-rw-r--r--   1 root root   76800 2007-04-17 23:53 BeHereiVideo.qtx
-rw-r--r--   1 root root  312832 2007-04-17 23:53 CLRVIDDC.DLL
-rw-r--r--   1 root root  135168 2007-04-17 23:53 clrviddd.dll
-rwxr-xr-x   1 root root   42956 2007-04-17 23:53 cook.so
-rw-r--r--   1 root root   81920 2007-04-17 23:53 CtWbJpg.DLL
-rw-r--r--   1 root root   88464 2007-04-17 23:53 DECVW_32.DLL
-rwxr-xr-x   1 root root  321008 2007-04-17 23:53 drvc.so
-rwxr-xr-x   1 root root   69648 2007-04-17 23:53 dspr.so.6.0
-rw-r--r--   1 root root  199680 2007-04-17 23:53 iac25_32.ax
-rw-r--r--   1 root root  307200 2007-04-17 23:53 icmw_32.dll
-rw-r--r--   1 root root   98304 2007-04-17 23:53 imc32.acm
-rw-r--r--   1 root root  739328 2007-04-17 23:53 ir41_32.dll
-rw-r--r--   1 root root  755200 2007-04-17 23:53 ir50_32.dll
-rw-r--r--   1 root root  225280 2007-04-17 23:53 ivvideo.dll
-rw-r--r--   1 root root   90112 2007-04-17 23:53 jp2avi.dll
-rw-r--r--   1 root root  245760 2007-04-17 23:53 LCMW2.dll
-rw-r--r--   1 root root   81920 2007-04-17 23:53 LCODCCMW2E.dll
-rw-r--r--   1 root root   33040 2007-04-17 23:53 lhacm.acm
-rw-r--r--   1 root root  204800 2007-04-17 23:53 lsvxdec.dll
-rw-r--r--   1 root root  422912 2007-04-17 23:53 m3jp2k32.dll
-rw-r--r--   1 root root   57344 2007-04-17 23:53 mi-sc4.acm
-rw-r--r--   1 root root  167696 2007-04-17 23:53 msh261.drv
-rw-r--r--   1 root root  424960 2007-04-17 23:53 msms001.vwp
-rw-r--r--   1 root root   76112 2007-04-17 23:53 msscds32.ax
-rw-r--r--   1 root root   49664 2007-04-17 23:53 nsrt2432.acm
-rw-r--r--   1 root root   34304 2007-04-17 23:53 qpeg32.dll
-rw-r--r--   1 root root  225280 2007-04-17 23:53 qtmlClient.dll
-rw-r--r--   1 root root  563200 2007-04-17 23:53 QuickTimeEssentials.qtx
-rw-r--r--   1 root root  904704 2007-04-17 23:53 QuickTimeInternetExtras.qtx
-rw-r--r--   1 root root 4544512 2007-04-17 23:53 QuickTime.qts
-rw-r--r--   1 root root     870 2007-04-17 23:53 README
-rw-r--r--   1 root root  299008 2007-04-17 23:53 rt32dcmp.dll
-rwxr-xr-x   1 root root   62896 2007-04-17 23:53 sipr.so.6.0
-rw-r--r--   1 root root  175616 2007-04-17 23:53 tm20dec.ax
-rwxr-xr-x   1 root root   22472 2007-04-17 23:53 tokf.so.6.0
-rwxr-xr-x   1 root root   59696 2007-04-17 23:53 tokr.so.6.0
-rw-r--r--   1 root root  573440 2007-04-17 23:53 tvqdec.dll
-rw-r--r--   1 root root   76800 2007-04-17 23:53 VDODEC32.dll
-rw-r--r--   1 root root   82432 2007-04-17 23:53 vdowave.drv
-rwxr-xr-x   1 root root  319480 2007-04-17 23:53 vid_3ivX.xa
-rw-r--r--   1 root root  211968 2007-04-17 23:53 ViVD2.dll
-rw-r--r--   1 root root  122880 2007-04-17 23:53 vivog723.acm
-rw-r--r--   1 root root  155648 2007-04-17 23:53 vmnc.dll
-rw-r--r--   1 root root   56320 2007-04-17 23:53 voxmsdec.ax
-rw-r--r--   1 root root  466944 2007-04-17 23:53 vp4vfw.dll
-rw-r--r--   1 root root  372736 2007-04-17 23:53 vp5vfw.dll
-rw-r--r--   1 root root  438272 2007-04-17 23:53 vp6vfw.dll
-rw-r--r--   1 root root   49152 2007-04-17 23:53 vssh264core.dll
-rw-r--r--   1 root root  421888 2007-04-17 23:53 vssh264dec.dll
-rw-r--r--   1 root root   98304 2007-04-17 23:53 vssh264.dll
-rw-r--r--   1 root root  454656 2007-04-17 23:53 vsshdsd.dll
-rw-r--r--   1 root root  706696 2007-04-17 23:53 vsslight.dll
-rw-r--r--   1 root root  167936 2007-04-17 23:53 vsswlt.dll
-rw-r--r--   1 root root  409720 2007-04-17 23:53 wma9dmod.dll
-rw-r--r--   1 root root  410216 2007-04-17 23:53 wmadmod.dll
-rw-r--r--   1 root root  773368 2007-04-17 23:53 wmsdmod.dll
-rw-r--r--   1 root root  486504 2007-04-17 23:53 wmspdmod.dll
-rw-r--r--   1 root root  807032 2007-04-17 23:53 wmv9dmod.dll
-rw-r--r--   1 root root 1181944 2007-04-17 23:53 wmvadvd.dll
-rw-r--r--   1 root root  807528 2007-04-17 23:53 wmvdmod.dll
-rw-r--r--   1 root root   93184 2007-04-17 23:53 wnvwinx.dll

```

---

### Post by Kilz on 2007-04-18
> **NullHead said:**
> hear they are.

```
total 22050
drwxr-xr-x   2 root root    2200 2007-04-17 23:52 .
drwxr-xr-x 169 root root   59672 2007-04-18 00:19 ..
-rw-r--r--   1 root root   61952 2007-04-17 23:53 acelpdec.ax
-rw-r--r--   1 root root   38912 2007-04-17 23:53 alf2cd.acm
-rw-r--r--   1 root root  118784 2007-04-17 23:53 aslcodec_dshow.dll
-rw-r--r--   1 root root   95292 2007-04-17 23:53 atrac3.acm
-rwxr-xr-x   1 root root   64912 2007-04-17 23:53 atrc.so.6.0
-rw-r--r--   1 root root   92160 2007-04-17 23:53 AvidQTAVUICodec.qtx
-rw-r--r--   1 root root   76800 2007-04-17 23:53 BeHereiVideo.qtx
-rw-r--r--   1 root root  312832 2007-04-17 23:53 CLRVIDDC.DLL
-rw-r--r--   1 root root  135168 2007-04-17 23:53 clrviddd.dll
-rwxr-xr-x   1 root root   42956 2007-04-17 23:53 cook.so
-rw-r--r--   1 root root   81920 2007-04-17 23:53 CtWbJpg.DLL
-rw-r--r--   1 root root   88464 2007-04-17 23:53 DECVW_32.DLL
-rwxr-xr-x   1 root root  321008 2007-04-17 23:53 drvc.so
-rwxr-xr-x   1 root root   69648 2007-04-17 23:53 dspr.so.6.0
-rw-r--r--   1 root root  199680 2007-04-17 23:53 iac25_32.ax
-rw-r--r--   1 root root  307200 2007-04-17 23:53 icmw_32.dll
-rw-r--r--   1 root root   98304 2007-04-17 23:53 imc32.acm
-rw-r--r--   1 root root  739328 2007-04-17 23:53 ir41_32.dll
-rw-r--r--   1 root root  755200 2007-04-17 23:53 ir50_32.dll
-rw-r--r--   1 root root  225280 2007-04-17 23:53 ivvideo.dll
-rw-r--r--   1 root root   90112 2007-04-17 23:53 jp2avi.dll
-rw-r--r--   1 root root  245760 2007-04-17 23:53 LCMW2.dll
-rw-r--r--   1 root root   81920 2007-04-17 23:53 LCODCCMW2E.dll
-rw-r--r--   1 root root   33040 2007-04-17 23:53 lhacm.acm
-rw-r--r--   1 root root  204800 2007-04-17 23:53 lsvxdec.dll
-rw-r--r--   1 root root  422912 2007-04-17 23:53 m3jp2k32.dll
-rw-r--r--   1 root root   57344 2007-04-17 23:53 mi-sc4.acm
-rw-r--r--   1 root root  167696 2007-04-17 23:53 msh261.drv
-rw-r--r--   1 root root  424960 2007-04-17 23:53 msms001.vwp
-rw-r--r--   1 root root   76112 2007-04-17 23:53 msscds32.ax
-rw-r--r--   1 root root   49664 2007-04-17 23:53 nsrt2432.acm
-rw-r--r--   1 root root   34304 2007-04-17 23:53 qpeg32.dll
-rw-r--r--   1 root root  225280 2007-04-17 23:53 qtmlClient.dll
-rw-r--r--   1 root root  563200 2007-04-17 23:53 QuickTimeEssentials.qtx
-rw-r--r--   1 root root  904704 2007-04-17 23:53 QuickTimeInternetExtras.qtx
-rw-r--r--   1 root root 4544512 2007-04-17 23:53 QuickTime.qts
-rw-r--r--   1 root root     870 2007-04-17 23:53 README
-rw-r--r--   1 root root  299008 2007-04-17 23:53 rt32dcmp.dll
-rwxr-xr-x   1 root root   62896 2007-04-17 23:53 sipr.so.6.0
-rw-r--r--   1 root root  175616 2007-04-17 23:53 tm20dec.ax
-rwxr-xr-x   1 root root   22472 2007-04-17 23:53 tokf.so.6.0
-rwxr-xr-x   1 root root   59696 2007-04-17 23:53 tokr.so.6.0
-rw-r--r--   1 root root  573440 2007-04-17 23:53 tvqdec.dll
-rw-r--r--   1 root root   76800 2007-04-17 23:53 VDODEC32.dll
-rw-r--r--   1 root root   82432 2007-04-17 23:53 vdowave.drv
-rwxr-xr-x   1 root root  319480 2007-04-17 23:53 vid_3ivX.xa
-rw-r--r--   1 root root  211968 2007-04-17 23:53 ViVD2.dll
-rw-r--r--   1 root root  122880 2007-04-17 23:53 vivog723.acm
-rw-r--r--   1 root root  155648 2007-04-17 23:53 vmnc.dll
-rw-r--r--   1 root root   56320 2007-04-17 23:53 voxmsdec.ax
-rw-r--r--   1 root root  466944 2007-04-17 23:53 vp4vfw.dll
-rw-r--r--   1 root root  372736 2007-04-17 23:53 vp5vfw.dll
-rw-r--r--   1 root root  438272 2007-04-17 23:53 vp6vfw.dll
-rw-r--r--   1 root root   49152 2007-04-17 23:53 vssh264core.dll
-rw-r--r--   1 root root  421888 2007-04-17 23:53 vssh264dec.dll
-rw-r--r--   1 root root   98304 2007-04-17 23:53 vssh264.dll
-rw-r--r--   1 root root  454656 2007-04-17 23:53 vsshdsd.dll
-rw-r--r--   1 root root  706696 2007-04-17 23:53 vsslight.dll
-rw-r--r--   1 root root  167936 2007-04-17 23:53 vsswlt.dll
-rw-r--r--   1 root root  409720 2007-04-17 23:53 wma9dmod.dll
-rw-r--r--   1 root root  410216 2007-04-17 23:53 wmadmod.dll
-rw-r--r--   1 root root  773368 2007-04-17 23:53 wmsdmod.dll
-rw-r--r--   1 root root  486504 2007-04-17 23:53 wmspdmod.dll
-rw-r--r--   1 root root  807032 2007-04-17 23:53 wmv9dmod.dll
-rw-r--r--   1 root root 1181944 2007-04-17 23:53 wmvadvd.dll
-rw-r--r--   1 root root  807528 2007-04-17 23:53 wmvdmod.dll
-rw-r--r--   1 root root   93184 2007-04-17 23:53 wnvwinx.dll

```

The reason that error showed, was because the directory didnt have to be made, it most likely already existed.

---

### Post by NullHead on 2007-04-18
So how do I fix the problem? Did your script finish the procedure or did it stop halfway through? should I remove the directory then try your script again??

---

### Post by Kilz on 2007-04-18
> **NullHead said:**
> So how do I fix the problem? Did your script finish the procedure or did it stop halfway through? should I remove the directory then try your script again??

There is no problem. Since the error is about the script not being able to create a directory that already exists(it cant make it, its already there). The last thing the script does is places all the files that are already in that directory, as proved by the list you posted here. You are looking for a problem where none exists.

---

### Post by NullHead on 2007-04-18
I have the script installed and as you say working but I get no results. It installs software for the firefox 32bit correct? When I start it up I try a flash game website and it bothers me with there being no plugin for for flash. I also try youtube and no go there, a java site next and no go there either.

---

### Post by jlacroix on 2007-04-18
Here you go.

---

### Post by Kilz on 2007-04-18
> **NullHead said:**
> I have the script installed and as you say working but I get no results. It installs software for the firefox 32bit correct? When I start it up I try a flash game website and it bothers me with there being no plugin for for flash. I also try youtube and no go there, a java site next and no go there either.

Open Firefox, click Help, then click about Mozilla Firefox. Near the bottom is a section that starts with Mozilla, copy it and paste it into a reply here.

---

### Post by Kilz on 2007-04-18
> **jlacroix said:**
> Here you go.

Ok, open a terminal, type in firefox32, go to youtube and try and get it to freeze, perhaps we will get an error in the terminal with some info.

---

### Post by jlacroix on 2007-04-18
Sure thing. Here is the output:
```
jeremy@jeremy-desktop:~$ firefox32
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:17314): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** CLB *** Initializing Google Browser Sync...
*** CLB *** Instanciating core objects...
*** CLB *** Registering with XPCOM...
*** CLB *** Adding categories...
*** CLB *** Google Browser Sync initialized succesfully!
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
Killed


```

---

### Post by Kilz on 2007-04-19
> **jlacroix said:**
> Sure thing. Here is the output:
```

(firefox-bin:17314): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** CLB *** Initializing Google Browser Sync...
*** CLB *** Instanciating core objects...
*** CLB *** Registering with XPCOM...
*** CLB *** Adding categories...
*** CLB *** Google Browser Sync initialized succesfully!
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
Killed


```

Actualy the ```
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
```
Isnt what I was hoping we would see. Its an error that is there all the time, for everyone. It comes from not being able to preload the script. The application even ignores it. It has nothing to do with Flash.
Dose this freezing happen on every video? If not can you link me to one that does freez the browser?

---

### Post by NullHead on 2007-04-19
> **Kilz said:**
> Open Firefox, click Help, then click about Mozilla Firefox. Near the bottom is a section that starts with Mozilla, copy it and paste it into a reply here.

There it is.

```
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.3) Gecko/20061201 Firefox/2.0.0.3 (Ubuntu-feisty)
```

---

### Post by Kilz on 2007-04-19
> **NullHead said:**
> There it is.

```
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.3) Gecko/20061201 Firefox/2.0.0.3 (Ubuntu-feisty)
```

You are running the 64bit version of firefox, or have it open when you start the 32bit. Having the 64bit version open causes all other Firefox windows, regardeless of what lancher you click on to be 64bit.

---

### Post by NullHead on 2007-04-19
> **Kilz said:**
> You are running the 64bit version of firefox, or have it open when you start the 32bit. Having the 64bit version open causes all other Firefox windows, regardeless of what lancher you click on to be 64bit.

So I use Firefox one at a time with it being only 32bit? Should I uninstall 64bit Firefox?

---

### Post by Kilz on 2007-04-19
> **NullHead said:**
> So I use Firefox one at a time with it being only 32bit? Should I uninstall 64bit Firefox?

Yes, make sure all 64bit firefox windows are closed before opening up the 32bit version. No dont uninstall it, because the help button on most applications uses the 64bit firefox.

---

### Post by NullHead on 2007-04-19
> **Kilz said:**
> Yes, make sure all 64bit firefox windows are closed before opening up the 32bit version. No dont uninstall it, because the help button on most applications uses the 64bit firefox.

Well now everything works but not java ... it just crashes. My attachment is the terminal dump of firefox's crash and my "about plugins" page.

---

### Post by jlacroix on 2007-04-19
> **Kilz said:**
> Actualy the ```
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
```
Isnt what I was hoping we would see. Its an error that is there all the time, for everyone. It comes from not being able to preload the script. The application even ignores it. It has nothing to do with Flash.
Dose this freezing happen on every video? If not can you link me to one that does freez the browser?
Here is one:

[http://youtube.com/watch?v=OpTaBulIL_w](http://youtube.com/watch?v=OpTaBulIL_w)

Now, let me make sure that I'm explaining myself correctly. Regardless of what video it is in particular on Youtube, all of them have a 1 in 3 chance (typically) of freezing my browser. When it does freeze, it doesn't freeze while playing the video, it freezes when its over. For example, say I'm playing a video on Youtube and its working fine. I see a video linked there that I click on, sometimes it will load the next video, or it will freeze. Or, if I get tired of the video and stop it, it may freeze. It will always play when you click on it its just when its over (either you stop playing the video yourself or the video runs its course) it locks up the browser. 

For the video I posted above, I just let the video play for about 30 seconds, then I refreshed it. It played it again no problem. I refreshed it again, and then my browser locked up.

---

### Post by Kilz on 2007-04-19
> **jlacroix said:**
> Here is one:

[http://youtube.com/watch?v=OpTaBulIL_w](http://youtube.com/watch?v=OpTaBulIL_w)

Now, let me make sure that I'm explaining myself correctly. Regardless of what video it is in particular on Youtube, all of them have a 1 in 3 chance (typically) of freezing my browser. When it does freeze, it doesn't freeze while playing the video, it freezes when its over. For example, say I'm playing a video on Youtube and its working fine. I see a video linked there that I click on, sometimes it will load the next video, or it will freeze. Or, if I get tired of the video and stop it, it may freeze. It will always play when you click on it its just when its over (either you stop playing the video yourself or the video runs its course) it locks up the browser. 

For the video I posted above, I just let the video play for about 30 seconds, then I refreshed it. It played it again no problem. I refreshed it again, and then my browser locked up.

To be honest, this is the first time I have had someone with this problem. You have had this problem from before you installed my script. Perhaps something got messed up in the settings. Lets try removing the settings directory. Flash will automaticly recreate it when you open the next flash animation. Open a terminal and enter.

```
rm -rfd ~/.macromedia
```

---

### Post by jlacroix on 2007-04-20
Sorry for the late reply. Yesterday was the official release of Feisty so I decided to do a clean install.

After the clean install finished last night, I went to the restricted manager to get nvidia's driver loaded (the refresh rate was killing me) and then I immediately ran your script. I am having the same problem. Before I reinstalled Feisty, on my old install I ran automatix2 and loaded its 32-bit Swiftfox with the plugins. Same problem there as well.

I also have a theory this may be a java problem, I think youtube uses java and flash both, if I'm not mistaken. Many sites have flash, from animations to animated ads all over the place and I haven't yet had a freeze on those kinds of sites.

I hope what I wrote helps you help me. :(

---

### Post by NullHead on 2007-04-20
Well youtube works fine for me. Its just java stuff that doesn't.

---

### Post by jlacroix on 2007-04-20
Its not a matter of whether or not youtube works, its a matter of if it freezes every now and then after leaving a video for another site or another video.

---

### Post by Kilz on 2007-04-20
> **jlacroix said:**
> Its not a matter of whether or not youtube works, its a matter of if it freezes every now and then after leaving a video for another site or another video.

Youtube uses Flash, not java. Since other firefox installs that do not share files do the same thing. I have to wonder if its something else not related to firefox.

> **jlacroix said:**
> Sorry for the late reply. Yesterday was the official release of Feisty so I decided to do a clean install.

After the clean install finished last night, I went to the restricted manager to get nvidia's driver loaded (the refresh rate was killing me) and then I immediately ran your script. I am having the same problem. **Before I reinstalled Feisty**, on my old install I ran automatix2 and loaded its 32-bit Swiftfox with the plugins. Same problem there as well.

I also have a theory this may be a java problem, I think youtube uses java and flash both, if I'm not mistaken. Many sites have flash, from animations to animated ads all over the place and I haven't yet had a freeze on those kinds of sites.

I hope what I wrote helps you help me. :(

Have you been running Feisty all this time?

---

### Post by Kilz on 2007-04-20
> **NullHead said:**
> Well youtube works fine for me. Its just java stuff that doesn't.

Are you running Feisty?

---

### Post by jlacroix on 2007-04-20
Well I had this problem back when I was using Edgy, still had it when I installed Feisty Development, and I still have it now with Feisty final.

Youtube does use java, because on Windows when Youtube fails it will demand that you install java and flash. Unless it complains about java for no reason.

---

### Post by NullHead on 2007-04-20
> **jlacroix said:**
> Well I had this problem back when I was using Edgy, still had it when I installed Feisty Development, and I still have it now with Feisty final.

Youtube does use java, because on Windows when Youtube fails it will demand that you install java and flash. Unless it complains about java for no reason.

But when I try youtube it works great... and Java doesn't work at all for me.

---

### Post by jlacroix on 2007-04-20
I don't pretend to understand it. Why don't you try playing 30 seconds of a random video with firefox32, wait 30 seconds, click on a random video, and repeat no more than 15 times and tell me if it crashes for you? You may have just been lucky.

---

### Post by Kilz on 2007-04-21
> **NullHead said:**
> But when I try youtube it works great... and Java doesn't work at all for me.

Are you running Feisty?

---

### Post by CRIMPS on 2007-04-21
Kilz-

I used your "how-to install flash" and I believe it worked...  When I run about: plugins in firefox32, the screenshot is:
[http://ubuntuforums.org/attachment.php?attachmentid=30342&stc=1&d=1177164254](http://ubuntuforums.org/attachment.php?attachmentid=30342&stc=1&d=1177164254)
Unfortunately, since running dapper and now edgy, I have _never_ been able to play video through the internet.  It doesn't matter what site I go to, whether the media is video or audio.  Here is a screenshot of what I get when on youtube.  It looks like I can simply click the video to play.  When I do so mplayer flashes up and then disappears in about a half second.  So nothing happens, no errors, nothing.

[http://ubuntuforums.org/attachment.php?attachmentid=30343&stc=1&d=1177164254](http://ubuntuforums.org/attachment.php?attachmentid=30343&stc=1&d=1177164254)
I have searched through the forums and I can't seem to find anything on this.  Do I need to enable something?  I also tried using MediaPlayerConnectivity utility but to no avail.  What am I missing?
[http://ubuntuforums.org/attachment.php?attachmentid=30344&stc=1&d=1177164254](http://ubuntuforums.org/attachment.php?attachmentid=30344&stc=1&d=1177164254)


Thanks for helping us little people...

Z

athlon64 3200, 120+ 200GB HDD's, 1GB RAM, dual boot edgy + winXP(for now)

---

### Post by Kilz on 2007-04-21
> **CRIMPS said:**
> Kilz-

I used your "how-to install flash" and I believe it worked...  When I run about: plugins in firefox32, the screenshot is:
[http://ubuntuforums.org/attachment.php?attachmentid=30342&stc=1&d=1177164254](http://ubuntuforums.org/attachment.php?attachmentid=30342&stc=1&d=1177164254)
Unfortunately, since running dapper and now edgy, I have _never_ been able to play video through the internet.  It doesn't matter what site I go to, whether the media is video or audio.  Here is a screenshot of what I get when on youtube.  It looks like I can simply click the video to play.  When I do so mplayer flashes up and then disappears in about a half second.  So nothing happens, no errors, nothing.

[http://ubuntuforums.org/attachment.php?attachmentid=30343&stc=1&d=1177164254](http://ubuntuforums.org/attachment.php?attachmentid=30343&stc=1&d=1177164254)
I have searched through the forums and I can't seem to find anything on this.  Do I need to enable something?  I also tried using MediaPlayerConnectivity utility but to no avail.  What am I missing?
[http://ubuntuforums.org/attachment.php?attachmentid=30344&stc=1&d=1177164254](http://ubuntuforums.org/attachment.php?attachmentid=30344&stc=1&d=1177164254)


Thanks for helping us little people...

Z

athlon64 3200, 120+ 200GB HDD's, 1GB RAM, dual boot edgy + winXP(for now)

To me , it looks like you have something else installed. Im not sure what it is. Either a video downloader or another kind of flash, maybe? If Flash wasnt installed, or youtube wasnt seeing it, you would see something like the 2 attached graphics.
Being that I dont know what it is, I have no idea how to remove it off the top of my head. 
If you are planing on moving to Feisty you may want to do a fresh install. That or you may have to uninstall firefox, the plugins, and all their settings folders.

---

### Post by NullHead on 2007-04-21
> **Kilz said:**
> Are you running Feisty?

Yes

---

### Post by Kilz on 2007-04-21
> **NullHead said:**
> Yes
Untill yesterday evening there was no Feisty script. The Edgy script had problems on Feisty with the jre 1.4 blackdown that was installed. There was a note in the Feisty section to replace the java with a newer version using the manual howto.
As I said this was yesterday up untill the evening. I then released a Feisty script. So you have 2 options.
1. Follow the manual howto (not recommended as the java now is at 6 and it is buggy)
2. Install the new Feisty script and let it just overwrite everything.

---

### Post by CRIMPS on 2007-04-21
Kilz-

You are a genius.   I was planning on upgrading to Feisty.  But since I haven't been on Linux very long I decided to do a clean install.  Well, I ran your script for flash and I video magically appeared. :guitar:  Thanks so much for your help and your dedication.


Z

---

### Post by NullHead on 2007-04-21
> **Kilz said:**
> Untill yesterday evening there was no Feisty script. The Edgy script had problems on Feisty with the jre 1.4 blackdown that was installed. There was a note in the Feisty section to replace the java with a newer version using the manual howto.
As I said this was yesterday up untill the evening. I then released a Feisty script. So you have 2 options.
1. Follow the manual howto (not recommended as the java now is at 6 and it is buggy)
2. Install the new Feisty script and let it just overwrite everything.

Thanks for the new script but It gave me the 
```
mkdir: cannot create directory `/usr/lib/win32': File exists
``` 
output again. Is this the end of your script as far as the end of the install proses? It all works now (including java)... I'm just a noob trying to understand linux better :)

---

### Post by Kilz on 2007-04-21
> **NullHead said:**
> Thanks for the new script but It gave me the 
```
mkdir: cannot create directory `/usr/lib/win32': File exists
``` 
output again. Is this the end of your script as far as the end of the install proses? It all works now (including java)... I'm just a noob trying to understand linux better :)

The script has to try to create the directory, because it places files there. If the directory exists, it gives the error, but the error is nothing to worry about. Its near the end, the only thing after it , is removing the script directory to clean up. Some of the folders it makes and files it downloads are owned by root and are hard to remove. So I just delete the folder the script is in.

---

### Post by jlacroix on 2007-04-22
I reran the script and I'm having the same problems. I really wish I knew what was causing this. Its not a major one but its just that its so annoying.

I used your script to install iceweasel, how do I uninstall it? Also, is there a way for me to uninstall firefox32 so I can try again with a vanilla install?

---

### Post by Kilz on 2007-04-22
> **jlacroix said:**
> I reran the script and I'm having the same problems. I really wish I knew what was causing this. Its not a major one but its just that its so annoying.

I used your script to install iceweasel, how do I uninstall it? Also, is there a way for me to uninstall firefox32 so I can try again with a vanilla install?

Both are installed with .deb files. Do a search in synaptic for firefox32 and iceweasel32. But, I dont think it has anything to do with your browser. The reason is you told me that swiftfox did the same thing. Swiftfox uses completely different files. It shares 0 files with firefox32, not even the plugin files, they are in different places. 2 different programs that dont share files doing the exact same thing points to a problem else ware.

---

### Post by jlacroix on 2007-04-22
I was considering just wiping my hard disk clean and starting over again. Do you think that may help?

Edit: I remember once I tried your script I did not have this problem at all, then I used Automatix to download Swiftfox and the problem began happening for both. I've wiped my drive and reinstalled Fiesty Final since then though and I don't use Automatix anymore but I was telling you that in case it means something in particular.

---

### Post by Kilz on 2007-04-23
> **jlacroix said:**
> I was considering just wiping my hard disk clean and starting over again. Do you think that may help?

Edit: I remember once I tried your script I did not have this problem at all, then I used Automatix to download Swiftfox and the problem began happening for both. I've wiped my drive and reinstalled Fiesty Final since then though and I don't use Automatix anymore but I was telling you that in case it means something in particular.

Im not sure that will help as you have tried that.

---

### Post by jlacroix on 2007-04-23
Okay I'll just continue searching google. If  you find something please let me know. Thank you for everything so far.

---

