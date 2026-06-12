---
title: "Does Ubuntu make full use of the 64bit instructions?"
date: 2005-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by TmP on 2005-11-26
Hi!

I'm considering rebuilding my desktop. I've been aiming at 939 Venice 3000+. I'm an Ubuntu user. I heard some of the new Linux distros make full use of the 64 bit platform. I was told that it gives a BIG boost to some applications, like DVD rippers or vodeo encoders.

My question is: 
Does Ubuntu do that or should I use some other distro which does it better?

ThanX!

---

### Post by akiro.yamamoto on 2005-11-26
Sure does....
What is really important is that the software you want to use is also built to take advantage of the 64bit extensions....
Regards
:smile:

---

### Post by RAOF on 2005-11-26
[QUOTE=akiro.yamamoto]Sure does....
What is really important is that the software you want to use is also built to take advantage of the 64bit extensions....
Regards
:smile:[/QUOTE]
Actually, due to the magic of compiling(tm), all the Breezy64 packages take advantage of the 64bit extensions :)  Except, I think, OpenOffice.

---

### Post by jars_u on 2005-11-27
[QUOTE=akiro.yamamoto]Sure does....
What is really important is that the software you want to use is also built to take advantage of the 64bit extensions....
Regards
:smile:[/QUOTE]

Hello, question - been testing out several different live distro's of Linux Ubuntu, Kubuntu, Mepis, Mandriva, Puppy - dual booted to Kubuntu i386 but after testing Live CD of Ubuntu 64 5.04 think I am going to install again.  Took the time to download the ISO but anyway my real question is...

since I am new to Linux wan't as few "issues" as possible am I more likely to have them if I am running software not designed to take advantage of 64bit?

specifically from [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) "Currently, we only have i386 binary packages available. If you do not use an i386 architecture" does this = problems or does it just mean it won't run as well as it might be able to if there was a 64 bit version?

---

### Post by RAOF on 2005-11-27
[QUOTE=jars_u]Hello, question - been testing out several different live distro's of Linux Ubuntu, Kubuntu, Mepis, Mandriva, Puppy - dual booted to Kubuntu i386 but after testing Live CD of Ubuntu 64 5.04 think I am going to install again.  Took the time to download the ISO but anyway my real question is...

since I am new to Linux wan't as few "issues" as possible am I more likely to have them if I am running software not designed to take advantage of 64bit?

specifically from [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) "Currently, we only have i386 binary packages available. If you do not use an i386 architecture" does this = problems or does it just mean it won't run as well as it might be able to if there was a 64 bit version?[/QUOTE]
This means that it will not be quite as easy to get wine to work as with an i386 install.  You still can get it to work (I have) by manually downloading the i386 .deb and installing it using "dpkg --force-architecture".  Whether or not anything that you want to actually **run** in wine works or not is another matter... :)

---

### Post by Septor on 2005-11-28
Wine is an exception to the rule.  If you build (and it is possible) a 64bit wine system, it will only be able to run 64bit Windows applications... not very useful.  So you have to either get a 32bit wine or build it yourself.  I imagine getting a 32bit package from [http://winehq.com/site/download-deb](http://winehq.com/site/download-deb) would work just fine.  Of course then you would then need the 32bit compat libraries in the ia32-libs package, but you should be able to find a HOWTO for that somewhere.

---

### Post by AndersAA on 2005-11-29
we're actually missing a few libraries from getting wine working without chroot.

although I have multiple installs here anyway so getting them wasn't too hard.


and note, some software, like encoders might run slower on amd64, simply because the assembly optimizations for i386 wont compile, BUT, if they've been optimized in asm for amd64 aswell you'll see a very nice performance boost.

//edit, extra libs I needed : libXxf86dga.so.1  libXxf86vm.so.1
oh, and since your a dev, proper multilib headers so we could compile it ourselfes with -m32 would be nice ;)

---

### Post by Septor on 2005-11-29
[QUOTE=AndersAA]
//edit, extra libs I needed : libXxf86dga.so.1  libXxf86vm.so.1
oh, and since your a dev, proper multilib headers so we could compile it ourselfes with -m32 would be nice ;)[/QUOTE]
Yup I ran into this myself with another 32bit binary app (fireglcontrol in the ATI binary drivers).  These libraries should definitely be in the ia32-libs.  Probably filing a bug ([http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/)) would be in order.  I just found this [bug](http://bugzilla.ubuntu.com/show_bug.cgi?id=17389) which is similar, so perhaps you could just add to that.  Your multilib header issue should definitely be a new bug if none exists already though.  I don't have control of the X stuff directly as I only work on the ATI driver packages, so there is not much I can do for you :)

---

