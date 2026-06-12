---
title: "64 bit compatability"
date: 2004-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rink on 2004-12-01
It is noticeable that quite a few packages don't support the 64 bit kernel and are missing from the 64 bit installation.

Would it be possible to post a list of applications which can be used on this installation? Plus any work arounds for those applications which can be got to work with a little tweaking, including chroot.

I would expect that there will start to be more and more applications which will be optimised for 64 bits; could we possibly get a list of these applications as they appear?

Many thanks,

Dave

---

### Post by daniels on 2004-12-02
Which applications do you see that are missing?

---

### Post by dmatrix on 2004-12-02
gkrellm, cdrdao, acidrip, tvtime and a working openoffice.org with gtk-theme are a few packages that come to mind. As well as packages like xcompmgr, transet, etc needed for extra things on X.org.

---

### Post by daniels on 2004-12-02
xcompmgr and transset, for one, are in the archive, and amd64's OOo is no more outdated than the one for i386.  Every architecture builds packages from the same source package, so there are no huge variations; many of the packages you named simply do not work on amd64.

---

### Post by JayBee on 2004-12-02
[QUOTE=daniels]Which applications do you see that are missing?[/QUOTE]
 How about gnucash & the madwifi driver?

---

### Post by daniels on 2004-12-02
[QUOTE=JayBee]How about gnucash & the madwifi driver?[/QUOTE]Er, gnucash is there, at least in Hoary.  And I have packages prepared which do madwifi on i386, amd64 and powerpc, even, that just need a bit of work to go with 2.6.9.

---

### Post by Schumi4ever on 2004-12-02
The w32codecs also dont work in 64 bits :(

edit: the whole marillat repo doesnt support 64 bit if Im correct.

---

### Post by Rink on 2004-12-02
[QUOTE=daniels]Which applications do you see that are missing?[/QUOTE]

Any web development programs such as Screem, Bluefish and Quanta.

Most Perl modules, including Tk and various Net modules.

Any Gui, such as wxpython.

I could go on, but internet access is restricted here and it costs an arm and a leg....

Dave

---

### Post by dmatrix on 2004-12-02
bluefish is in amd64 and works quite well. Not sure about the others.

---

### Post by dmatrix on 2004-12-02
[QUOTE=daniels]xcompmgr and transset, for one, are in the archive, and amd64's OOo is no more outdated than the one for i386.  Every architecture builds packages from the same source package, so there are no huge variations; many of the packages you named simply do not work on amd64.[/QUOTE]


gkrellm, cdrdao, acidrip and tvtime packages from Debian Sarge AMD64 work fine on Ubuntu. I am just curious why they are not built in Ubuntu. I think with acidrip the source was in Ubuntu archives and I built it from there. The other 3 I am pretty sure I got Debian Sarge AMD64 debs and they work fine.

---

### Post by jdong on 2004-12-02
[QUOTE=Schumi4ever]The w32codecs also dont work in 64 bits :(

edit: the whole marillat repo doesnt support 64 bit if Im correct.[/QUOTE]

32-bit Windows .dll's will not work under a 64-bit Linux kernel.... imagine that

---

### Post by BoyOfDestiny on 2004-12-02
tvtime 0.9.15 compiles on warty 64. Even made .deb with checkinstall

---

### Post by daniels on 2004-12-03
[QUOTE=Rink]Any web development programs such as Screem, Bluefish and Quanta.

Most Perl modules, including Tk and various Net modules.

Any Gui, such as wxpython.

I could go on, but internet access is restricted here and it costs an arm and a leg....[/QUOTE]Er, those are all there in 'universe', you just need to enable it.  See the FAQ on the website.

---

### Post by jdong on 2004-12-03
daniel, out of curiousity, have you guys included a 32-bit WINE yet? That was one of the only reasons I'm not currently running 64-bit Ubuntu.

---

### Post by daniels on 2004-12-04
Dunno, sorry.  Probably not -- I imagine you'd need a chroot.  But I should be getting an amd64 system for home sometime after I get back.

---

### Post by jdong on 2004-12-04
[QUOTE=daniels]Dunno, sorry.  Probably not -- I imagine you'd need a chroot.  But I should be getting an amd64 system for home sometime after I get back.[/QUOTE]

That's fine. Using dpkg --force to install 32-bit Wine debs actually works, but I don't WANT to know what kind of dpkg problems that could cause in the future....


I still remember what happened when I tainted AMD64 Gentoo with -m32 binaries! LOL, boy did I learn a lot about Portage in that incident!

---

### Post by Rink on 2004-12-07
[QUOTE=daniels]Er, those are all there in 'universe', you just need to enable it.  See the FAQ on the website.[/QUOTE]


Is there a list of available software in 'universe'?

---

### Post by leech on 2004-12-08
[QUOTE=jdong]That's fine. Using dpkg --force to install 32-bit Wine debs actually works, but I don't WANT to know what kind of dpkg problems that could cause in the future....


I still remember what happened when I tainted AMD64 Gentoo with -m32 binaries! LOL, boy did I learn a lot about Portage in that incident![/QUOTE]

Any idea if that would work with Cedega/WineX?  

Leech

---

### Post by firfin on 2004-12-08
[QUOTE=dmatrix]bluefish is in amd64 and works quite well. Not sure about the others.[/QUOTE]

I got the bluefish using synaptic. It is the amd64 version? How can you tell?
It's version 0.12-1 (3613 kB size)

---

### Post by leech on 2004-12-10
all of the packages in Synaptic will be amd64 versions, since it looks in the repository for the amd64 architecture.

Just tried Cedega with dpkg -i --force-architecture and it installed, but won't load anything.  Would always give me;

XRender could not be loaded
        This is not necessarily a fatal error, however some
        applications require XRender to be installed and
        may not function or display text correctly otherwise.
        Please consult the WineX Font FAQ for more details
        about this problem/usr/lib/transgaming_cedega//winex/bin/wine: can't exec '/mnt/windows/WINDOWS/NOTEPAD.EXE': error=21


Oh well, there are always Emulators and Neverwinter Nights...

Leech

---

