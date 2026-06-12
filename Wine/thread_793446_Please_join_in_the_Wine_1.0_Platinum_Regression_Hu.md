---
title: "Please join in the Wine 1.0 Platinum Regression Hunt"
date: 2008-05-13
forum: Wine
---

### Post by YokoZar on 2008-05-13
One of the release goals for Wine 1.0 is for it to be, unequivocally, better than every previous Wine release for all applications.  This means that any application that worked perfectly out of the box in an old Wine version must continue to do so.

We've set up a wiki page for anyone who wants to test their favorite platinum application to make sure it works the best it ever has in Wine 1.0:  [http://wiki.winehq.org/PlatinumRegressionHunt](http://wiki.winehq.org/PlatinumRegressionHunt)

If you find a legitimate regression, you can post it in the Wine forum or, alternatively, here in this thread.  I'll forward bug reports and messages for you.

Thank you.

---

### Post by happyhamster on 2008-05-13
Is it ok to join the hunt when using self-compiled versions of wine? (I'm still on gutsy.)

---

### Post by cogadh on 2008-05-13
How about a Gutsy RC1 package? I'd like to help with the Platinum regression tests, but for some reason every time I've tried compiling RC1 on my Gutsy machine, I end up with Wine that works right up until the app tries to produce a sound, then it just locks up. I'm not sure if it is an issue with Wine itself or my compile process (I still use steps that worked back when I was running Feisty).

EDIT - Or, if a package is not an option, how about foolproof Ubuntu/Gutsy-specific compile instructions? That way we Gutsy users can continue to participate in the bug hunt as new RCs come out.

---

### Post by schtufbox on 2008-05-14
Joined in by testing..well okay, using the apps I usually use under rc1. They work just as well as ever :)

---

### Post by MemoryDump on 2008-05-14
so far [World of Warcraft]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922") doesn't work as well as it had in the past. Choppiness being reported. (you can see ppl talking about it in the [Wine forums]("http://ubuntuforums.org/forumdisplay.php?f=313"))

---

### Post by Dark Aspect on 2008-05-14
The Halo update is broke with wine 1.0-rc1,it use to work perfect on wine 0.9.42.

```
-----------@---------:~$ env WINEPREFIX="/home/-----------/.halo" wine /home/-----------/.halo/drive_c/halopc107.exe
Warning: could not find DOS drive for current working directory '/home/-----------', starting in the Windows directory.
-----------@---------:~$ fixme:wintrust:SoftpubAuthenticode unimplemented for UI choice 1
_halopat.tmp: Failed
```

---

### Post by YokoZar on 2008-05-15
> **cogadh said:**
> How about a Gutsy RC1 package? I'd like to help with the Platinum regression tests, but for some reason every time I've tried compiling RC1 on my Gutsy machine, I end up with Wine that works right up until the app tries to produce a sound, then it just locks up. I'm not sure if it is an issue with Wine itself or my compile process (I still use steps that worked back when I was running Feisty).

EDIT - Or, if a package is not an option, how about foolproof Ubuntu/Gutsy-specific compile instructions? That way we Gutsy users can continue to participate in the bug hunt as new RCs come out.
Did you already do this (on i386):
```

sudo apt-get build-dep wine
make distclean
CC="gcc-4.2" ./configure
make

```

64 bit can try here: [http://wiki.winehq.org/WineOn64bit#head-7703cf4cc6b63630523cf66e77d621e4f81bc873](http://wiki.winehq.org/WineOn64bit#head-7703cf4cc6b63630523cf66e77d621e4f81bc873)

---

### Post by oninjao on 2008-05-15
im cosidering doing this wine is a brill prog

---

### Post by cogadh on 2008-05-15
> **YokoZar said:**
> Did you already do this (on i386):
```

sudo apt-get build-dep wine
make distclean
CC="gcc-4.2" ./configure
make

```

64 bit can try here: [http://wiki.winehq.org/WineOn64bit#head-7703cf4cc6b63630523cf66e77d621e4f81bc873](http://wiki.winehq.org/WineOn64bit#head-7703cf4cc6b63630523cf66e77d621e4f81bc873)

The only thing I didn't do was specifying the compiler. However, even with doing that, I get the same exact results; Wine works, but if an app tries to produce sound (including the Test Sound function in winecfg), it locks up.

EDIT - Just for giggles I tried this on a different Gutsy machine and still got the same results. I also tried changing the sound driver to OSS instead of ALSA, but it made no difference. Has anyone else still running on Gutsy managed to compile a functional RC1? If so, how did you do it? I'm sure I'm just missing something annoyingly basic (that's usually what happens), but I'm out of ideas now.

---

### Post by cogadh on 2008-05-24
Aha! Looks like the problem was not me or the process I was using, but was Wine 1.0-rc1 itself! I just compiled rc2 using the same exact process as I used multiple times for rc1 and it works perfectly! No sound lockups or anything and the very first app I tried actually works better than it did before on 0.9.59!

I'm off to bug hunt now...

---

