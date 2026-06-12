---
title: "Running zsnes without chroot?"
date: 2005-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by BoyOfDestiny on 2005-11-10
Ok, so compiling the zsnes cvs fails... 1.42 compiles but running it returns illegal instruction...

Here is a 32-bit deb I've built myself with checkinstall.

[http://www.safaribans.com/gpl/zsnes-cvs_cvs-20050927-1_i386.deb](http://www.safaribans.com/gpl/zsnes-cvs_cvs-20050927-1_i386.deb)

**Backstory:**
(I don't use the ubuntu one since 1.36 and doesn't run a lot of games and can't see files in jma (same for snes9x in the repo regarding jma)

I tried forcing the install of my deb made no difference (removed it since it made me uncomfortable ;)

**The meat and potatoes:**
Running the binary from the deb I get this at console:

./zsnes: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

Is there an easy way to just drop this in some folder? Where is the best place to find this file (I have ubuntu 32 on my laptop)

Anyway, I don't know if it would require anything else also (to compile it I have gathered all the usual stuff: nasm, libpng [optional], the sdl-dev stuff, automake, autoconf, think that's all of it...)

Thanks for your time! :KS

---

### Post by Mednafen on 2005-11-10
I created a directory, "/la", and ran debootstrap on it.  I then updated /la/etc/sources.list, chroot'd into /la, ran apt-get update, and then installed the necessary packages, including ZSNES.

I can then run ZSNES without using chroot, like 
"env LD_LIBRARY_PATH=/la/usr/lib/ /la/usr/bin/zsnes GameName.smc".

For some reason, it locks up in the GUI when I try to use the GUI, so be cautious.

---

### Post by RAOF on 2005-11-10
You could actually download the SDL .debs from the 32bit repository, extract them using file-roller (which will open them as an archive), and copy all the SDL*.so.whatever files into the /usr/lib32 directory and run "sudo ldconfig".

This is not really a clean way of doing it, and there's no guarantee that the SDL libraries won't bomb out trying to access some other 32bit lib, but it could work.

---

### Post by BoyOfDestiny on 2005-11-11
Ok nevermind! Setting up a chroot was really easy! I like the way it can see my home folder too...
Fantastic! 

Now I don't miss 32-bit since I can enjoy my 16-bit... :KS

---

