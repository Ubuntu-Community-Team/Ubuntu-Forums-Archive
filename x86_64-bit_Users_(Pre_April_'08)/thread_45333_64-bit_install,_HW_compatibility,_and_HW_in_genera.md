---
title: "64-bit install, HW compatibility, and HW in general"
date: 2005-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by edisav on 2005-06-29
Hi folks,

I am planning on installing Kubuntu in a brand new box using an AMD 64-bit processor. Before I buy all parts, I would like to know:

- Are there any issues in general with this type of processor?

- Is there anywhere a hardware-compatibility list?

- Are there any other issues with any other hardware such as video, sound, nic card, etc? Is there anything that I need to stay away from?

- Is this an overkill? Should I stay 32?

- Kubuntu or Ubuntu?

Any feedback will be appreciated.

---

### Post by dewey on 2005-06-29
As far as compatibility, I'm running a DFI Lanparty 250gb NF3 board, with an AMD64 3000+(socket 754) and compatibility is great.  The one thing you might want to avoid if you're a big gamer, is ATI cards, their linux drivers are pretty sketchy (Atleast for me), and Nvidia has much better linux support, but ATI is getting better with their linux support.  It's completely possible to get ATI cards working great, and many people have,  I personally however, have not.

64 bit being overkill?  If you're talking about the CPU itself, definitely not.  If you bought a 32bit cpu now, in a year, you'd be regretting it.  Everything is shifting over to 64bit now, and support is getting better and better.

Incompatibilities limited to 64bit can be pretty nasty,  Flash and many proprietary codecs have been noted not to work, but running a 32bit CHRoot solves that problem right up (Great tutorial on the forum, just run a search for it).

Kubuntu or Ubuntu?  It depends on whether you like [Gnome](http://www.gnome.org)  or [KDE](http://www.kde.org) as your interface.  And if you install one, and decide you prefer the other, a simple apt-get line can retrieve the other desktop for you.
To get Kubuntu while running Ubuntu
```
$sudo apt-get install kubuntu-base kubuntu-desktop
```
To get Ubuntu while running Kubuntu
```
$sudo apt-get install ubuntu-base ubuntu-desktop
```
They are nearly identical, it's just that one uses Gnome, and the other KDE.

There's a nice Hardware compatibility list [here](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by Terracotta on 2005-06-29
There's no need to install the base, when you're gonna install de desktop after it. kubuntu-desktop en ubuntu-desktop will also install kubuntu-base and ubuntu-base.
I'm running an asus A8V mainboard with a Sata harddisk and all the stuff, everything just works.

---

### Post by negatory on 2005-06-30
I'm running an AMD64 3500+ with an Asus A8N-SLI,1GB ram,a sata disk and a Nvidia 6600 256 megs and have no problems with hardware compatibility.I have also a bluetooth dongle working that I couldn't put to work with the windows drivers in my laptop...go figure!

Pedro Carrico

---

