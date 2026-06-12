---
title: "Hoary ia32-libs"
date: 2005-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by callahan on 2005-03-12
Minor thing in Hoary, ia32-libs doesn't upgrade properly:

E: /var/cache/apt/archives/ia32-libs_0.5ubuntu3_amd64.deb:  error creating symbolic link `./usr/lib32/libGL.so.1': No such file or directory

  Michael

---

### Post by Kareema on 2005-03-12
[QUOTE=callahan]Minor thing in Hoary, ia32-libs doesn't upgrade properly:

E: /var/cache/apt/archives/ia32-libs_0.5ubuntu3_amd64.deb:  error creating symbolic link `./usr/lib32/libGL.so.1': No such file or directory

  Michael[/QUOTE]

Seems that there's been a problem while packaging. If you look at the package with "dpkg --contents" you can see the paths beginning with "./"!
I think it won't take long till a new package will show up in the repositories...

---

### Post by Kareema on 2005-03-14
Hmm, no update of ia32-libs till today and I couldn't find a way to force an install of the package ignoring the errors (and still having a usable system).
I would have emailed the package maintainer to inform him about the problem but I don't know if Daniel Jacobowitz <dan@debian.org> is the right person. Is he only the package maintainer of the Debian package or is he the maintainer of the Ubuntu package, too?

---

### Post by AndersAA on 2005-03-14
bugzilla.ubuntu.com/ :)

---

### Post by Kareema on 2005-03-14
[QUOTE=AndersAA]bugzilla.ubuntu.com/ :)[/QUOTE]
Right, but I thought a packaging problem like that isn't worth opening a bug in bugzilla (it's no real bug) and a direct email to the maintainer would be more appropriate in this case.

Thank's anyway...

---

### Post by jdong on 2005-03-14
Yeah, a packaging problem is a pretty serious bug, especially since it doesn't properly  install a file that it's supposed to!

---

### Post by Kareema on 2005-03-14
[QUOTE=jdong]Yeah, a packaging problem is a pretty serious bug, especially since it doesn't properly  install a file that it's supposed to![/QUOTE]

Already in bugzilla as bug 7542 now (reported by somebody else). It was no general packaging failure as I first thought. As you can read in the bug report it seems to occur only if you've installed xorg-driver-fglrx (or the nvidia drivers, too?). Workaround: Remove xorg-driver-fglrx, update ia32-libs and reinstall xorg-driver-fglrx.

---

### Post by callahan on 2005-03-14
That worked for me.

  Michael

---

### Post by Dromio on 2005-03-14
[QUOTE=callahan]That worked for me.

  Michael[/QUOTE]
 Still doesn't seem to have done it for me.  GDM works, I login and hear the pretty sound, but no desktop.  :(

I haven't install nvidia-glx yet, it's straight off the CD.  It also occurs with Hoary-i386 too.

I can't even figure out what log file to look at for clues.  Any suggestions?

---

