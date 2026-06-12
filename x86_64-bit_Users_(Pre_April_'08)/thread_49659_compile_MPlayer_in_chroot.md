---
title: "compile MPlayer in chroot"
date: 2005-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by negatory on 2005-07-17
Has anyone tried to compile mplayer in a chroot enviroment?
At the end it gives me:"/usr/bin/ld: warning: i386:x86-64 architecture of input file `Gui/libgui.a(app.o)' is incompatible with i386 output"
and lots of other erros like that but for different libs...
If you can help me with this I would appreciate.
Thanks
Pedro Carrico

---

### Post by Jet2k5 on 2005-07-17
Well I haven't tried, but are you sure you set up a clean 32-bit chroot environment?  You can follow this guide [here](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64) 
 
Hope that helps ...

---

### Post by negatory on 2005-07-17
Yes, I've followed that instructions.
And everything seems to work just fine, firefox,acrobat...
I've apt-get'ed mplayer and it works too,I'll stick to that instead of compiling the new version (version in the repositories is 1.0pre6-3.3.5 and the one I was trying to compile was 1.0pre7).
Thanks
Pedro Carrico

---

### Post by Flac on 2005-07-17
but why use chroot for mplayer? mplayer compiles under 64-bit.

 I dont have chroot set up and im clueless an many things, just curious :) *trying to learn*

---

### Post by Tamir on 2005-07-17
[QUOTE=Flac]but why use chroot for mplayer? mplayer compiles under 64-bit.

 I dont have chroot set up and im clueless an many things, just curious :) *trying to learn*[/QUOTE]

But the codecs doesn't  :-|

---

### Post by Flac on 2005-07-17
ah, *understands* i havnt done much with mplayer, so i didnt really notice :P I know it ran the few videos i have attempted well enough. Anyway, thank you for enlightening me :)

---

### Post by negatory on 2005-07-17
Yes the w32codecs were the reason why I wanted to compile the latest version on mplayer in a chroot enviroment...
I've compiled the mplayer-plugin with success in the chroot using [this howto](http://www.ubuntuforums.org/showthread.php?postid=229950#poststop).The only thing that I can't really compile is the latest version of mplayer...argh!!!  :-x  
Maybe if I find a .deb with the latest version I can run it.
Thanks
Pedro Carrico

---

