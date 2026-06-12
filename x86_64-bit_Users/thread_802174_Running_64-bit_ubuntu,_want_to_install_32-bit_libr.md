---
title: "Running 64-bit ubuntu, want to install 32-bit libraries."
date: 2008-05-21
forum: x86 64-bit Users
---

### Post by softest bullet ever shot on 2008-05-21
Hi all,
I'm running 64-bit ubuntu.  However, my company hasn't gotten kept up with technology so we compile our software in 32-bit mode.  I need certain libraries (mostly related to Motif/X11) in 32-bit mode.  Does anyone have any helpful tips on searching for 32-bit versions of development libraries?  I tried searching for things like "libXm 32" but had no luck.  

Thanks in advance for the help.

---

### Post by Kilz on 2008-05-21
> **softest bullet ever shot said:**
> Hi all,
I'm running 64-bit ubuntu.  However, my company hasn't gotten kept up with technology so we compile our software in 32-bit mode.  I need certain libraries (mostly related to Motif/X11) in 32-bit mode.  Does anyone have any helpful tips on searching for 32-bit versions of development libraries?  I tried searching for things like "libXm 32" but had no luck.  

Thanks in advance for the help.

If it isnt included in a ia32 package like ia32-libs, you may have to use [getlibs ]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")to install it. You can search packages for contents[ here]("http://packages.ubuntu.com/").

---

### Post by softest bullet ever shot on 2008-05-21
> **Kilz said:**
> If it isnt included in a ia32 package like ia32-libs, you may have to use [getlibs ]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")to install it. You can search packages for contents[ here]("http://packages.ubuntu.com/").

Thanks, that seems to be the trick.  I haven't found all the stuff I need yet, but it's just a matter of finding it.

---

