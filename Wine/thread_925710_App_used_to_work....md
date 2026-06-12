---
title: "App used to work..."
date: 2008-09-20
forum: Wine
---

### Post by maphilli14 on 2008-09-20
I'm not sure where to start with this and I'm hoping someone can help get me in the right direction.  I use Hardy on 2 different Lenovo Laptops (T61 and T60p).  The application in question is an Astronomy processing program called "registax".  I used to be able to use all the functions like radio buttons, checkboxes, pop-up (overlay?) and dialog boxes.  Then something happened like a wine update or conflicting application or setting.  Now the wine window for Registax just freezes can cannot be closed or interacted with.  Running from cli doesn't offer any insight either.  One hardy install has the 1.0.0 wine, and the other now has 1.1.5.  Same results on both installs.  Please tell me what information would help diagnose and hopefully solve this issue.

TIA,

Mike

---

### Post by asdfoo on 2008-09-21
> **maphilli14 said:**
> I'm not sure where to start with this and I'm hoping someone can help get me in the right direction.  I use Hardy on 2 different Lenovo Laptops (T61 and T60p).  The application in question is an Astronomy processing program called "registax".  I used to be able to use all the functions like radio buttons, checkboxes, pop-up (overlay?) and dialog boxes.  Then something happened like a wine update or conflicting application or setting.  Now the wine window for Registax just freezes can cannot be closed or interacted with.  Running from cli doesn't offer any insight either.  One hardy install has the 1.0.0 wine, and the other now has 1.1.5.  Same results on both installs.  Please tell me what information would help diagnose and hopefully solve this issue.

TIA,

Mike

You can run a regression test [http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting) to find out which patch broke your application.  Then you file a bug report at [http://bugs.winehq.org](http://bugs.winehq.org) using that information.

---

### Post by maphilli14 on 2008-09-23
Great info!  I will try, but what if I'm not sure what verions to test?!

Mike

---

### Post by david_kt on 2008-09-24
> **maphilli14 said:**
>  I used to be able to use all the functions like radio buttons, checkboxes, pop-up (overlay?) and dialog boxes.  Then something happened like a wine update or conflicting application or setting. 

Open synaptic package manager, browse to wine and click it to focus, and then press <ctrl> <e>, it will open a dialog box. Click on the force version drop down box, choose the last one (the oldest wine available on the force version), and then click "force version" button below.

After the wine has been downgraded, run again your application. if it is ok, then lock wine:

Open synaptic package manager, browse to wine and click it to focus, and then click package menu on the synaptic, choose lock version. After that if you see wine in the synaptic, it shows a lock symbol there. It would not upgrade again while it is locked.

DK

---

### Post by asdfoo on 2008-09-24
> **maphilli14 said:**
> Great info!  I will try, but what if I'm not sure what verions to test?!

Mike


As per the instructions you would mark the version that doesn't work correctly as bad and the last version that worked correctly as good.

---

### Post by maphilli14 on 2008-09-25
> **asdfoo said:**
> As per the instructions you would mark the version that doesn't work correctly as bad and the last version that worked correctly as good.

I tried the lowest available version 0.9.59 and it doesn't seem to clear up my issue.  I do appreciate the handy tip!

Anyone have any ideas about non-version related issues,  Compiz?

TIA,

Mike

---

### Post by asdfoo on 2008-09-25
> **maphilli14 said:**
> I tried the lowest available version 0.9.59 and it doesn't seem to clear up my issue.  I do appreciate the handy tip!

Anyone have any ideas about non-version related issues,  Compiz?

TIA,

Mike

Is there a download available?  If there is I will take a look myself.

---

### Post by david_kt on 2008-09-25
> **asdfoo said:**
> Is there a download available?  If there is I will take a look myself.

Actually I already downloaded and try, but I do not know how to use it:

[http://www.astronomie.be/registax/installregistax4.exe](http://www.astronomie.be/registax/installregistax4.exe)

Looks no problem in my computer.

DK

---

### Post by maphilli14 on 2008-09-25
> **david_kt said:**
> Actually I already downloaded and try, but I do not know how to use it:

[http://www.astronomie.be/registax/installregistax4.exe](http://www.astronomie.be/registax/installregistax4.exe)

Looks no problem in my computer.

DK

Hey folks, thanks for helping out!  Much appreciated!

The application itself is somewhat complicated to the passer-by.  It is however fairly easy for me to lock up / freeze.

Simply click one of the checkboxes and then try to do anything else.  Uncheck, recheck, help.  Even closing the app is busted.

Let me know if there's additional info I can supply to shed more light.

TIA,

Mike

---

### Post by maphilli14 on 2008-10-10
One more update before I approach giving up on this niche app:

I've tried to run from cli in linux before and it won't print any lines of output for me. Except one time, I closed the window (via xkill) and the cli thought the process was still running. I then hit CTRL+C and found this output:

```
":~/.wine/drive_c/Program Files/RegiStax4$ wine ./RegiStax4.exe
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
after 377 requests (375 known processed) with 288 events remaining.
E: thread-posix.c: Assertion 'pthread_setspecific(t->key, userdata) == 0' failed at pulsecore/thread-posix.c:194, function pa_tls_set(). Aborting.
wine: Assertion failed at address 0xb7fab410 (thread 001b), starting debugger..."
```


could be a generic error about WM stuff??? not sure

Mike

---

### Post by david_kt on 2008-10-10
> **maphilli14 said:**
> 

```
":~/.wine/drive_c/Program Files/RegiStax4$ wine ./RegiStax4.exe
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
after 377 requests (375 known processed) with 288 events remaining.
E: thread-posix.c: Assertion 'pthread_setspecific(t->key, userdata) == 0' failed at pulsecore/thread-posix.c:194, function pa_tls_set(). Aborting.
wine: Assertion failed at address 0xb7fab410 (thread 001b), starting debugger..."
```



I have tried in my computer, this program work very well with wine 1.0, although I do not really how to use it. It never crash when I play around with it. May be you could try below:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then restart your computer.

After that, try to launch it again, hopefully it help.

DK

---

### Post by maphilli14 on 2008-10-10
I had a great suggestion from a nice fellow on cloudynights.com ([http://www.cloudynights.com/ubbthreads/showflat.php?Cat=0&Number=2691877&page=0&view=collapsed&sb=5&o=all&fpart=1&vc=&PHPSESSID=](http://www.cloudynights.com/ubbthreads/showflat.php?Cat=0&Number=2691877&page=0&view=collapsed&sb=5&o=all&fpart=1&vc=&PHPSESSID=)) and found a fix.

I went into winecfg to turn off all the audio/sound options.  I had ALSA turned on and even in wine 1.1.6 (recently released), it still 'crashed'.  Turning off audio fixed almost EVERYTHING!

Happily, I don't need audio for much anything in wine, but if I understand correctly, each app can have a separate 'bottle' setup with different audio and other settings.  So best of luck to everyone and thanks to you for the suggestion!

Mike

---

