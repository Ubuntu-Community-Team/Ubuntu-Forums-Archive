---
title: "64bit Firefox 3 + Flash"
date: 2008-06-30
forum: x86 64-bit Users
---

### Post by ingvildr on 2008-06-30
Does anybody have problems with flash just not seeming to load some flash content, i know they work on 32bit fedora and opensuse, so its really annoying when it wont on hardy 64.

Here is an example, this on my pc will just sit at loading....

[http://www.comedycentral.com/shows/the_colbert_report/index.jhtml]("http://www.comedycentral.com/shows/the_colbert_report/index.jhtml")

---

### Post by stchman on 2008-06-30
> **ingvildr said:**
> Does anybody have problems with flash just not seeming to load some flash content, i know they work on 32bit fedora and opensuse, so its really annoying when it wont on hardy 64.

Here is an example, this on my pc will just sit at loading....

[http://www.comedycentral.com/shows/the_colbert_report/index.jhtml]("http://www.comedycentral.com/shows/the_colbert_report/index.jhtml")

Works fine on all three of my machines.  Did you install the flashplugin-nonfree package?

---

### Post by ingvildr on 2008-06-30
> **stchman said:**
> Works fine on all three of my machines.  Did you install the flashplugin-nonfree package?

Yup

---

### Post by onering on 2008-06-30
I've had the same problem.  Most of the time it works fine however sometimes I only get a gray box where the Flash object should be and no sound.  Other times I get a gray box with sound.  One working theory is that there could be a memory leak in the Flash application but that has not been confirmed for sure.

---

### Post by Plasma_NZ on 2008-07-01
i have a similar problem... but that site loads fine, takes a while, but works..

all flash sites work, but evilchillie videos dont load for me..

---

### Post by stchman on 2008-07-01
Every once in a while I have to restart Firefox when Flash content won't load.  It is every once in a while.

I am used to Flash being buggy for Linux as Adobe will not fix it.

---

### Post by bradtem on 2008-07-01
I have also been getting this problem ever since moving to firefox 3 during the beta period.   Now flash works for anywhere from a few hours to a day or two.  After that all flash programs fail (gray box).    I have flashblock but this even happens if you tell it to allow flash for a site all the time.

In the past, I actually had to do more than restart FF to get it to work -- I had to quit firefox, do a reinstall of flashplugin-nonfree and restart firefox.  However, this is no longer the case.

Sometimes the flash plugin will keep running (making audio) after I close firefox, but this is rare.  

It's pretty annoying, though.

---

### Post by Yellow Pasque on 2008-07-01
I believe that comedycentral.com was mentioned before as having mpeg4(?) format. Make sure you have a media player plugin with that codec. I use VLC myself, but a lot of people use xine.

```
sudo apt-get install libxine1-plugins libxine1-misc-plugins xine-plugin lib32nss-mdns
```

When you enter about:plugins in the URL bar, it should have a xine plugin entry with a large list of audio/video formats.

For VLC:
```
sudo apt-get install vlc libvlc0 vlc-plugin-pulse mozilla-plugin-vlc lib32nss-mdns
```

---

### Post by bradtem on 2008-07-02
Well, VLC may be all well and good for comedy central, but it doesn't solve the flash problem which many of us are finding frustrating.  It is, unfortunately, hard to duplicate.

---

### Post by incubii on 2008-07-03
Yes i also have this issue with flash. Most of the time the flash content will play but sometimes i just get the grey box problem.

Refreshing the page does not work as it affects all instances of flash in that firefox instance so only a restart of firefox will fix the issue.

Its more an annoyance then anything. Especially when you open many tabs of youtube content etc...

---

### Post by Plasma_NZ on 2008-07-03
Ok i had flash problems in 64bit - sometimes video's would crap-out halfway through, meaning i'd have to goto terminal and find the proccess id for npviewer.bin - and kill it, then i got sick of that and make a short script and put it as a icon... i used this..

```

#!/bin/bash

killall npviewer.bin
exit

```

so when-ever i have flash problems, i click it once, then reload the page and the problems solved.. hope this helps..

---

### Post by promodus on 2008-07-03
I had Gutsy and upgraded to Hardy.
I had the same problem where all flash suddenly just appeared as a gray box.
```

dpkg --purge nspluginwrapper flashplugin-nonfree
apt-get --reinstall install flashplugin-nonfree
```

Seemed to fix the problem on my end.

---

### Post by erkanea on 2008-07-03
i also have the same issue. flash is working normally but rarely i just see grey box. after a restart of firefox worked all the time. (without a firefox restart problem keeps going)

flashplugin-nonfree installed and hardy is fully updated.

---

### Post by ilcontegis on 2008-07-03
Hi....
I have a similar problem.
FF3 installed but flash doesn't wanna work!
I explain. If for example i try to watch a video on youtube or if i try to play a online flash game, when i just click it start to work but after 2-3 seconds it blocks. Moreover I have no audio.
I tried to:
- install the package nonfree
- install flash through nspluginwrapper
- install flash 9
- install flash 10 beta 1
- install flash 10 beta 2
The result is always the same.
Do you have some suggestions?
thx:)

---

### Post by Yellow Pasque on 2008-07-03
> **ilcontegis said:**
> Hi....
I have a similar problem.
FF3 installed but flash doesn't wanna work!
I explain. If for example i try to watch a video on youtube or if i try to play a online flash game, when i just click it start to work but after 2-3 seconds it blocks. Moreover I have no audio.
I tried to:
- install the package nonfree
- install flash through nspluginwrapper
- install flash 9
- install flash 10 beta 1
- install flash 10 beta 2
The result is always the same.
Do you have some suggestions?
thx:)
Do you have libflashsupport installed?
```
sudo apt-get install libflashsupport
```

---

### Post by ilcontegis on 2008-07-04
> **Temüjin said:**
> Do you have libflashsupport installed?
```
sudo apt-get install libflashsupport
```

Yes. The problem doesn't change.

Any other suggestions?

Thank you.

---

### Post by wallsensus on 2008-07-04
Hello Everyone,

I'm currently using Hardy AMD64 with the flash installed. I have a problem with flash for when I am viewing a site with flash on it and then I close the site npviewer.bin dies.

To illustrate this example go to [www.youtube.com](www.youtube.com) in one tab, and [www.futureshop.ca](www.futureshop.ca) in another.  (Futureshop is Canada's bestbuy.  And actually bestbuy bought futureshop, incase anyone was wondering)

The future shop site seems to be the killer in this case because when I close that tab I get this error from npviwer.bin

```
(npviewer.bin:19293): Gdk-WARNING **: GdkWindow 0x40001bc unexpectedly destroyed

(npviewer.bin:19293): Gdk-WARNING **: GdkWindow 0x40001b9 unexpectedly destroyed

(npviewer.bin:19293): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 4124 error_code 3 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I've installed everything as per instructions in threads here on ubuntu forums

If other people can reproduce this then it will prove that at least I'm not taking crazy pills :)

---

### Post by iamnotthemessiah on 2008-07-04
theres a new nspluginwrapper available [http://gwenole.beauchesne.info//en/projects/nspluginwrapper#news](http://gwenole.beauchesne.info//en/projects/nspluginwrapper#news)

---

### Post by Yellow Pasque on 2008-07-04
> **iamnotthemessiah said:**
> theres a new nspluginwrapper available [http://gwenole.beauchesne.info//en/projects/nspluginwrapper#news](http://gwenole.beauchesne.info//en/projects/nspluginwrapper#news)
> Fix crashes with Flash Player 9 Update 3 (9.0.115)

Hopefully, the fixes also work for Update 4 (9.0.124), because that's what's in the Ubuntu repo.

---

### Post by bradtem on 2008-07-04
> **iamnotthemessiah said:**
> theres a new nspluginwrapper available [http://gwenole.beauchesne.info//en/projects/nspluginwrapper#news](http://gwenole.beauchesne.info//en/projects/nspluginwrapper#news)

Anybody made a .deb for hardy amd64?

---

### Post by jespdj on 2008-07-06
Flash works normally on my 64-bit Ubuntu 8.04 system.

> **wallsensus said:**
> To illustrate this example go to [www.youtube.com](www.youtube.com) in one tab, and [www.futureshop.ca](www.futureshop.ca) in another.  (Futureshop is Canada's bestbuy.  And actually bestbuy bought futureshop, incase anyone was wondering)

The future shop site seems to be the killer in this case because when I close that tab I get this error from npviwer.bin

...

If other people can reproduce this then it will prove that at least I'm not taking crazy pills :)
I've just tried that and it works normally, no crashes or error messages.

I do have flashplugin-nonfree installed.
I do not have libflashsupport installed.

---

### Post by dcstar on 2008-07-06
> **ingvildr said:**
> Does anybody have problems with flash just not seeming to load some flash content, i know they work on 32bit fedora and opensuse, so its really annoying when it wont on hardy 64.

Here is an example, this on my pc will just sit at loading....

[http://www.comedycentral.com/shows/the_colbert_report/index.jhtml]("http://www.comedycentral.com/shows/the_colbert_report/index.jhtml")

Same problem on my 64 bit Hardy install - but the site works fine on my 32 bit Hardy VM!

Other Flash sites seem to work ok on my 64 bit.

---

### Post by ilcontegis on 2008-07-06
> **ilcontegis said:**
> Yes. The problem doesn't change.

Any other suggestions?

Thank you.

i did a complete format....and reinstall all ok now

---

### Post by bradtem on 2008-07-06
> **jespdj said:**
> Flash works normally on my 64-bit Ubuntu 8.04 system.


I've just tried that and it works normally, no crashes or error messages.

I do have flashplugin-nonfree installed.
I do not have libflashsupport installed.

I'm sure it does.  The problem is not easy to reproduce.  It always happens after a day or so of use, however.  There are probably people for whom it never happens, but there are many for whom it is annoyingly regular.   So what's interesting is any reports of how to make the problem go away.    Alas, doing a complete reinstall is not a suitable work-around.

---

### Post by chrono13 on 2008-07-06
> **Plasma_NZ said:**
> Ok i had flash problems in 64bit - sometimes video's would crap-out halfway through, meaning i'd have to goto terminal and find the proccess id for npviewer.bin - and kill it, then i got sick of that and make a short script and put it as a icon... i used this..

```

#!/bin/bash

killall npviewer.bin
exit

```

so when-ever i have flash problems, i click it once, then reload the page and the problems solved.. hope this helps..

I dropped that script into my script folder and created a launcher on my panel. This is a great and convenient workaround - much much better than having to close all Firefox windows. Thank you!

---

### Post by promodus on 2008-07-07
> **iamnotthemessiah said:**
> theres a new nspluginwrapper available [http://gwenole.beauchesne.info//en/projects/nspluginwrapper#news](http://gwenole.beauchesne.info//en/projects/nspluginwrapper#news)

I needed to install the following
```
 apt-get install libxt-dev libgtk2.0-dev libglib2.0-dev
 wget http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-1.0.0.tar.bz2
 tar xvjf nspluginwrapper-1.0.0.tar.bz2
 cd nspluginwrapper-1.0.0
 ./configure --disable-biarch
 make
```

From there I only replaced npwrapper.so and npconfig.

My previous post of purging and reinstalling did not fix the issue. Hopefully this does...

---

### Post by dcstar on 2008-07-12
> **dcstar said:**
> Same problem on my 64 bit Hardy install - but the site works fine on my 32 bit Hardy VM!

Other Flash sites seem to work ok on my 64 bit.

The Flash 10 update now allows me to load this site ok in 64 bit!   :)

---

