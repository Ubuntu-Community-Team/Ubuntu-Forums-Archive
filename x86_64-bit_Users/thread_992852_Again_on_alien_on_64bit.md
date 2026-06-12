---
title: "Again on alien on 64bit"
date: 2008-11-25
forum: x86 64-bit Users
---

### Post by egalua on 2008-11-25
Hi all,

I need to install a program which comes in rpm 32 bit; trying to convert it with alien, I get the usual error message as in 
[http://ubuntuforums.org/showthread.php?t=483757&highlight=32bit+alien]("http://ubuntuforums.org/showthread.php?t=483757&highlight=32bit+alien")

I then tried a trick: I first used "alien --to-tgz" and this gives me a tgz, then I tried alien on this tgz and... I get a deb!!
So, why am I not able to produce a deb directly?:confused:

The deb obtained this way gets installed without errors with dpkg and 
it seems to work properly...

Someone can explain me what did happen? Can I rely on the program installed this way?

In any case, on many posts on the web I have seen that to solve the error message

dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)

there are two ways: recompile the program, or use alien in a
chrooted 32bit environment.

What if I need just a single program which is in rpm? Create a chrooted 32bit env only for one program is too much work... Is there a shorter way?

Thanks a lot

Fabio

---

### Post by Kilz on 2008-11-25
A Chroot is one way, but not the only way. It was way back with Breezy (Ubuntu 5.10). 64bit Ubuntu since Dapper can run 32bit applications if all the libraries are in place. You could just as easily force architecture the deb file you end up with and use [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790") to install any missing libraries.

---

### Post by egalua on 2008-11-25
> **Kilz said:**
> A Chroot is one way, but not the only way. It was way back with Breezy (Ubuntu 5.10). 64bit Ubuntu since Dapper can run 32bit applications if all the libraries are in place. You could just as easily force architecture the deb file you end up with and use [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790") to install any missing libraries.

I see that things are better now. In fact, the deb I obtained via the tgz step installs and runs smoothly (apparently...:) ).

In any way, thanks for the interesting link.

Fabio

What I would like to know is why I couldn't obtain directly a deb and how produce directly a deb from a 32bit rpm without to much hassle.

---

### Post by Thelasko on 2008-11-25
> **egalua said:**
> What I would like to know is why I couldn't obtain directly a deb and how produce directly a deb from a 32bit rpm without to much hassle.

Alien has protections in place to prevent you from creating a deb out of a 32-bit rpm because it isn't reliable.  You are fortunate your program worked.

---

