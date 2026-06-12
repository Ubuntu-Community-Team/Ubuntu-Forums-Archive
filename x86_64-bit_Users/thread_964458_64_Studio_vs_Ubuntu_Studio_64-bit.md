---
title: "64 Studio vs Ubuntu Studio 64-bit"
date: 2008-10-30
forum: x86 64-bit Users
---

### Post by Th3Professor on 2008-10-30
[CENTER][SIZE=1][COLOR=White]..........[/COLOR][/SIZE][IMG]http://farm4.static.flickr.com/3191/2988493232_7f5bd3d9d2_o.jpg[/IMG][IMG]http://farm4.static.flickr.com/3290/2988493242_75bbdd745a_o.jpg[/IMG]*[SIZE=1](64-bit)[/SIZE]*

\\:D/



How are they similar?

How are they different?
[/CENTER]




[SIZE=1][COLOR=White]...[/COLOR][/SIZE]

---

### Post by Th3Professor on 2008-11-18
<bump>

---

### Post by John Jason Jordan on 2008-11-18
> **Th3Professor said:**
> How are they similar?
How are they different?

Studio 64 is a separate distro:

[http://64studio.com/]("http://64studio.com/")

Ubuntu Studio is an Ubuntu distro. In some respects it does a lot of the same things as Studio 64.

Both come in either 32-bit or 64-bit versions.

---

### Post by Th3Professor on 2008-11-18
> **John Jason Jordan said:**
> Studio 64 is a separate distro:

[http://64studio.com/](http://64studio.com/)

Ubuntu Studio is an Ubuntu distro. In some respects it does a lot of the same things as Studio 64.

Both come in either 32-bit or 64-bit versions.

Both are actually Debian-based... same distro derivative. ;) I believe they even share the same repos or at least the same studio ports.

I'm curious how well both operate in 64-bit, the differences specifically, though similarities as well. So far I've seen very little difference other than cosmetics. I'd like to know if someone has extensive first-hand experience with both, what could be said about the similarities and differences between 64 Studio and Ubuntu Studio 64-bit. :)

---

### Post by xigen on 2008-11-18
hey hey hey

It depends on what you want to do.

If you want to compose music, or remix, or use Ubuntu with an instrument -- Try Ubuntu studio.  The real-time aspects of the kernel are super cool.

If you want to edit/create video - again, Ubuntu Studio is super.

If you are doing primarily browsing/email/ play some music - I think it is better to stick with the main distribution.  Ubuntu Studio will do this fine, however, it seems like it would be a little off for your use case. 

rock on,

MW

---

### Post by Th3Professor on 2008-11-18
> **xigen said:**
> hey hey hey

It depends on what you want to do.

If you want to compose music, or remix, or use Ubuntu with an instrument -- Try Ubuntu studio.  The real-time aspects of the kernel are super cool.

If you want to edit/create video - again, Ubuntu Studio is super.

If you are doing primarily browsing/email/ play some music - I think it is better to stick with the main distribution.  Ubuntu Studio will do this fine, however, it seems like it would be a little off for your use case. 

rock on,

MW

howdy howdy howdy. :)

...I mean, comparing "Ubuntu Studio" (64-bit) to "64 Studio" (another Linux)... I didn't mean comparing Ubuntu Studio to Ubuntu. ;)

---

### Post by Jouke74 on 2008-11-19
When I compared Ubuntu Edgy with Studio 64 at that time, Ubuntu was the better choice strangely enough. After serious tweaking in both distro's the sound lag was much smaller in Ubuntu as compared to Studio 64. I don't know how this is currently.

Edit: Furthermore the larger userbase of Ubuntu might help solving issues. Also for non-free codecs Ubuntu might be a bit more user friendly. However, with all distro choices everything depends on yourself and how you deal with your hardware & software (issues).

---

### Post by danzvash on 2008-11-19
General differences: Ubuntu Studio is basically a set of packages on top of the Ubuntu distro, which is very polished and up-to-date.
64studio is a specialist distro based upon Debian "etch" - in general, Debian are not as quick to package new software as Ubuntu. So the recent upstream releases of all the cool apps (rosegarden, ardour, synths, everything!) will appear much sooner in Ubuntu repos than in Debian/64studio ones. 

You will probably have to tweak either distro for good audio performance - you won't find it all working out-of-the-box after install. (ALSA and JACK, real-time configuration etc)
Once tweaked, either distro will give you the same performance - but your app versions might be older in 64studio (unless you build apps from source, but if you do much of that you might aswell run Gentoo, or LFS ....)
Remember - this is Linux - because the source code is out there, ultimately you can always have exactly the same software running on WHATEVER distro - it's just a case of how technical you want to get!
But using packages makes a lot of sense - and Ubuntu package repos are incredibly complete and up-to-date. 

Ubuntu Studio would be my recommendation: for ease of install/configuration/recent app versions/active community etc.
Especially if you're relatively new to Linux - but also if you're not! (I've used Linux exclusively for 8 years - including from scratch, Gentoo, Sorcerer, Redhat/Fedora/ other RPM-based - and I have to say that nothing else can beat Ubuntu - it's got leading-edge apps, fully customisable, and you can have a working install done in 15 minutes! Better than 2 days with Gentoo ;))

I believe Ubuntu Studio has a much newer kernel (2.6.27-7) compared to 64studio (linux-image-2.6.21-1-multimedia-amd64) , which means better hardware support.
(Although my snd-hda-intel card is still giving me bad performance under 2.6.27.... :( ... JACK will _not_ run without xruns! ) 

Current (Intrepid) Ubuntu studio real-time (linux-rt) kernel does not support SMP, which means only 1 processor seen on your new Intel Core 2s or your AMD dual-cores ....

Although the standard Ubuntu kernel (linux-image-2.6.27-7-generic) seems to support realtime, and is also SMP-aware. But the resolution timer is at 250Hz rather than something higher like 1000Hz, so some audio apps will complain about low resolution (e.g. Rosegarden) ....

I'm currently dual-booting both Ubuntu Studio and 64Studio on my HP tx2500z (dual-Turion X2) tablet notebook. If you do the same, be careful with GRUB during the 64studio installer: it looks like it's preparing multi-boot fine, but the GRUB version used causes it to fail on booting other Linux distros you might have (like my Ubuntu). Leave the grub bit out when you install 64studio, and just boot back into Ubuntu (or whatever) to prepare GRUB and run it there.
I'm not sure I'm gonna keep the 64studio partition - after having had a peek, it looks like I'll have a lot less to tweak in Ubuntu Studio in order to get it working nice ;-)
(now i just have to fix snd-hda-intel soundcard latency, random caps-lock-flashing hard freezes, suspend/hibernate, fglrx/radeonhd issues, wacom, lirc, webcam ..... aaahhh linux, linux ....:) )

---

### Post by Th3Professor on 2008-11-19
Speaking of Rosegarden, it doesn't come default with Ubuntu Studio now. Weird! (Had to install it separately.)

---

