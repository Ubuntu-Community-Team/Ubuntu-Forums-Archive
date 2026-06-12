---
title: "Avidemux 2.3 install help"
date: 2007-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by flammenwurfer on 2007-02-13
Has anybody installed avidemux 2.3?  There's a .deb in the [www.debian-multimedia.org](www.debian-multimedia.org) repos but it needs higher versions of a bunch of the dependencies and won't install.

---

### Post by heracles on 2007-02-13
I have installed it but as of yet have not used it. The interface dialogue box comes up however. I installed it under Automatix2

---

### Post by flammenwurfer on 2007-02-13
I installed it using Automatix2 also, but it's version 2.1.2, not 2.3.  I want version 2.3 because it has mp4 encoding for my psp.

---

### Post by SadaraX on 2007-02-19
If you want to give version 2.3, you can download it from [www.getdeb.net](www.getdeb.net) or you can try my custom Edgy version:
[http://students.washington.edu/cdobrich/avidemux_2.3.0_i386.deb](http://students.washington.edu/cdobrich/avidemux_2.3.0_i386.deb)

I keep updates about my build in the thread called 'Avidemux in Edgy' ([http://www.ubuntuforums.org/showthread.php?t=287902](http://www.ubuntuforums.org/showthread.php?t=287902))

Version 2.1.2 in the repositories is very old and it does not contain PSP support. The latest stable version of Avidemux is 2.3.0, but PSP support is still broken in version 2.3. PSP seems to be fixed in development version 2.4. 

In the Avidemux Wiki, there is a LONG article about compiling Avidemux for yourself. The development branch is 2.4.
[http://www.avidemux.org/admWiki/index.php?title=Compiling_Avidemux#Ubuntu.2FKubuntu_.28Dapper_6.06.2C_Breezy_5.10_.26_Hoary_5.04.29](http://www.avidemux.org/admWiki/index.php?title=Compiling_Avidemux#Ubuntu.2FKubuntu_.28Dapper_6.06.2C_Breezy_5.10_.26_Hoary_5.04.29)

SVN:
svn://svn.berlios.de/avidemux/branches/avidemux_2.4_branch/

It is pretty hard to compile Avidemux in Edgy because the Spidermonkey libs are not in the official Ubuntu repositories. You can follow their steps, they have some work arounds. There is one other work around, but it is big a dirty kludge. If you feel like trying to compile yourself, post to thread and I can give you steps if you cannot follow the wiki article.

---

### Post by SadaraX on 2007-02-19
Heck, why should you have to compile it? Here, I just made a fresh working version of 2.4.0 from the unstable development. 

[http://students.washington.edu/cdobrich/avidemux_2.4.0_unstable_i386.deb](http://students.washington.edu/cdobrich/avidemux_2.4.0_unstable_i386.deb)

That is current version of the SVN with the GTK interface. The PSP works now. The official statement by the developers concerning non-stable versions is "Do not use if you want to save what you make" basically meaning no there is no guarantee (though I have been running with the development for years and never had problems). You can fool around with it and the PSP has been tested pretty thoroughly recently. We think it is fixed.

---

### Post by flammenwurfer on 2007-04-18
awesome!  thanks for the deb

---

### Post by SadaraX on 2007-04-18
You are welcome. If you experience problem, post them and I will see if I can help

---

### Post by arashiko28 on 2007-07-20
Following the wiki instructions. Can't install spidermonkey, how do I find it? I'm rather new and its the first time I try to compile alone. Please help!!!
UPDATE: I REALLY MESSED UP THIS TIME!!!

I accidentally deleted the libnspr4 and it removed a ton of other programs including firefox, nautilus, gnome... How do i recover them? I'm even affraid of turning off the laptop.

Haven't restarted, installed back gnome and firefox and nautilus, don't remember anything else :S
 After I install all the dependencies, when I try to do the make -f Makefile.dist I keep getting an error:
" *** Creating aclocal.m4
aclocal:configure.in:121: warning: macro `AM_GNU_GETTEXT' not found in library
*** Creating configure
configure.in:121: error: possibly undefined macro: AM_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
make[1]: *** [cvs] Error 1
make: *** [all] Error 2 "

Help, please :confused:

---

### Post by SadaraX on 2007-07-21
> **arashiko28 said:**
> Following the wiki instructions. Can't install spidermonkey, how do I find it? I'm rather new and its the first time I try to compile alone. Please help!!!
UPDATE: I REALLY MESSED UP THIS TIME!!!

I accidentally deleted the libnspr4 and it removed a ton of other programs including firefox, nautilus, gnome... How do i recover them? I'm even affraid of turning off the laptop.

Haven't restarted, installed back gnome and firefox and nautilus, don't remember anything else :S
 After I install all the dependencies, when I try to do the make -f Makefile.dist I keep getting an error:
" *** Creating aclocal.m4
aclocal:configure.in:121: warning: macro `AM_GNU_GETTEXT' not found in library
*** Creating configure
configure.in:121: error: possibly undefined macro: AM_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
make[1]: *** [cvs] Error 1
make: *** [all] Error 2 "

Help, please :confused:

This might help. In /var/log there is a file called dpkg.log. This has logs of all the package installation and removal activity on the system for the last several days. You can look at what we removed when you ran the commend to get rid of libnspr4. Once you know what you are missing, you can run:

sudo apt-get install everything_I_am_missing

As for your compilation problem, the developer of Avidemux got really tired of all the Spidermonkey troubles (he runs Kubuntu64 himself). So in Avidemux version 2.4, he has included built in Spidermonkey engine code. This means that people do not need to install Spidermonkey development files to compile Avidemux 2.4.

Unfortunately, Avidemux 2.4 is not officially released yet. There are some very stable previews available though:

[http://fixounet.free.fr/avidemux/download.html](http://fixounet.free.fr/avidemux/download.html)

I suggest that anyone who has trouble compiliing Avidemux try grabbing the preview 2 source and compile that. The instructions for compiling are exactly the same except for no Spidermonkey. (I should update the wiki docs).

I have been using the latest SVN development version of Avidemux for years and it isi usually quite stable.

---

### Post by arashiko28 on 2007-07-21
Are you sure it's that stable, because according to what i´ve read, it should not be used for really important things, I'm going to process some old (really old) family videos (from one of the 1st color 8mm video cameras on my country, passed to vcr 40 years later, and now intend to pass it to DVD to give a copy to the whole family). :popcorn: Of course that i have a bacup, but i'll just shoot myself after spending 16 h processing a video, that it fails.

---

### Post by SadaraX on 2007-07-21
> **arashiko28 said:**
> Are you sure it's that stable, because according to what i´ve read, it should not be used for really important things, I'm going to process some old (really old) family videos (from one of the 1st color 8mm video cameras on my country, passed to vcr 40 years later, and now intend to pass it to DVD to give a copy to the whole family). :popcorn: Of course that i have a bacup, but i'll just shoot myself after spending 16 h processing a video, that it fails.

Well, it is not stable in that we have released it and are relatively sure there are no major bugs. Usage may vary from person to person. If you are really worried, use the stable version 2.3. 

All I will say is that I have been using the 'unstable' version of the program for years now. By and large most errors are very obvious and you see them within seconds. But these errors are few and far between. The preview version are usually low on the errors, if there are any.

---

### Post by arashiko28 on 2007-07-21
SOLVED!!! EVERYTHING, ABSOLUTELY EVERYTHING NEEDED TO INSTALL AVIDEMUX IS ALREADY ON SYNAPTIC, INCLUDING AVIDEMUX ITSELF!!!!:lolflag: so why compiling, its a click away!

---

### Post by arashiko28 on 2007-07-22
Sadarax, since you've been using it for a long time, could you tell me of a place to find some sort of manual, i'm pretty confused, even after i load the subtitles, it process the video within seconds but no subtitles. i don't know what i'm missing. My only interest is to encode the video and add hardsub. On Virtualdub was very easy, but here i'm kinda lost...:confused:

---

