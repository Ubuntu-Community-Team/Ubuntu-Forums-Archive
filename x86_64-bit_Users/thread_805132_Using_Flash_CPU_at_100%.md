---
title: "Using Flash CPU at 100%"
date: 2008-05-23
forum: x86 64-bit Users
---

### Post by peakshysteria on 2008-05-23
Youtube and similar sites give me a CPU at 100%. And no option for playing it in totem-plugin-viewer via Firefox. This sites makes this possible: [http://www1.nrk.no/nett-tv/klipp/277798](http://www1.nrk.no/nett-tv/klipp/277798) and the CPU is steady at 28%.

Possible related plugins: about: plugins:

Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r100

Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.


Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233




```
ls -al /usr/lib/mozilla//plugins/
```
total 8
drwxr-xr-x 2 root root 4096 2008-05-06 14:34 .
drwxr-xr-x 4 root root 4096 2008-04-22 23:59 ..
lrwxrwxrwx 1 root root   37 2008-04-28 20:54 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

```
ls -al /usr/lib/firefox/plugins/
```
total 8
drwxr-xr-x 2 root root 4096 2008-05-06 14:34 .
drwxr-xr-x 4 root root 4096 2008-04-28 20:54 ..
lrwxrwxrwx 1 root root   37 2008-04-28 20:54 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
```
uname -a
```
Linux ninja-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
ninja@ninja-desktop:~$ 

Does anyone have a fix for this?

---

### Post by Vadi on 2008-05-23
This is a Flash problem, it's like this for everybody and I'm pretty sure they know.

---

### Post by peakshysteria on 2008-05-23
So what about the link? Isn't that flash too?

---

### Post by Vadi on 2008-05-23
Flash is like a programming language. Not all flash programs do the same thing. Most often though, the ones that display video, tend to make flash use 100%. At any rate this is a known flash problem.

---

### Post by peakshysteria on 2008-05-24
This sites makes this possible: [http://www1.nrk.no/nett-tv/klipp/277798](http://www1.nrk.no/nett-tv/klipp/277798) and the CPU is steady at 28%. And i can play it in Movie Player., which is pretty awesome I think. So what your saying is that we'll just have to wait it out :(  Kinda frustrating....

---

### Post by Yellow Pasque on 2008-05-24
You can wait it out or you can do something about it:

I submitted a feature request this morning for a 64-bit version. I suggest everyone reading this do the same. 
[http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform](http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform)

> *******Enhancement / FMR*********
 If you cannot open the code for Flash9, please make an x86_64 port. Ease of installation,  CPU usage (and subsequently, heat and fan noise) would all be greatly improved. Yes, I am aware of the open source efforts and the recent release of specs, but it is not enough.  Ubuntu 8.04 and Fedora 9 (amongst other major distributions) were released within the last month and thousands of people are trying Linux for the first time without genuine Flash support. It is enough to drive them to 32-bit Linux or worse yet, back to Microsoft slavery.

Thank you.

---

### Post by peakshysteria on 2008-05-24
Done. Thanks for the link :)

---

### Post by francesco1964 on 2008-08-25
I have the same problem with Ubuntu 8.04 32 bit.
I've submitted this to Adobe hoping ...

******BUG******
Concise problem statement:
cpu 100% usage when display page with flash ads
Steps to reproduce bug:
 1. visit some pages with flash ads
 2.
 3.
 Results: the cpu goes to 100% usage
 Expected results: the CPU does not go to 100% usage

I don't like to put all of my cpu just to look that unuseful ads. Please correct this bug very annoying or I'll should correct my browser abandoning flash use. I can't believe that your are promoting Microsoft and SilverLight this way!!! Wake Up boys.
***********

Is there anyway to stop automatic flash playing? A way so that I can manually start a play?

---

### Post by peakshysteria on 2008-09-03
If you are using Firefox [COLOR="Red"][Flasblock]("https://addons.mozilla.org/en-US/firefox/addon/433")[/COLOR] will do this for you. The latest version should be working fine on 32 bit as far as I know. It's got some issues in 64 bit making FF crash when loading several pages with lots of flash content at once. The addon replaces flash with a nice play icon and replacing the add (or the likes) with the sites/pages background colour. Very nice. One of the most usefull addons out there if you ask me. Wish it was working smooth on 64 bit as well......

---

### Post by tuxxy on 2008-09-03
> **peakshysteria said:**
> Youtube and similar sites give me a CPU at 100%. And no option for playing it in totem-plugin-viewer via Firefox. This sites makes this possible: [http://www1.nrk.no/nett-tv/klipp/277798](http://www1.nrk.no/nett-tv/klipp/277798) and the CPU is steady at 28%.

Possible related plugins: about: plugins:

Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r100

Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.


Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233




```
ls -al /usr/lib/mozilla//plugins/
```
total 8
drwxr-xr-x 2 root root 4096 2008-05-06 14:34 .
drwxr-xr-x 4 root root 4096 2008-04-22 23:59 ..
lrwxrwxrwx 1 root root   37 2008-04-28 20:54 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

```
ls -al /usr/lib/firefox/plugins/
```
total 8
drwxr-xr-x 2 root root 4096 2008-05-06 14:34 .
drwxr-xr-x 4 root root 4096 2008-04-28 20:54 ..
lrwxrwxrwx 1 root root   37 2008-04-28 20:54 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
```
uname -a
```
Linux ninja-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
ninja@ninja-desktop:~$ 

Does anyone have a fix for this?

Is the problem always there or is it an on/off issue, will youtube run fine sometimes?

---

