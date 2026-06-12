---
title: "build 64-bit apps under i386 Kubuntu on an AMD64 machine"
date: 2008-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by David J Bush on 2008-04-09
[FONT=Century Gothic][SIZE=3]I'm generally satisfied with i386 Kubuntu running on my dual core 64-bit Athlon box. The graphics look fine to me. But there are **some **apps I would like to be able to use the full power of my machine. These apps do a lot of intensive calculation. For example, chess engines, fractal zoom image generators, and povray would all benefit. But if I follow the standard sequence of ./configure, make, and sudo make install, the configure script would just read the target architecture as 32-bit, and would compile accordingly. Is that right? Or did I miss something? Is there any way I could tweak some initialization file or something to build these apps the way I want? Would there be any issues involved with getting them to behave under the 32-bit OS?

Thanks![/SIZE] 
[/FONT]

---

### Post by Mr. Swiveller on 2008-04-09
I know you can run 32-bit apps on 64-bit Kubuntu if you force-install them. I have never heard of this being possible the other way around, though. 

In any case, I think that moving to 64-bit Ubuntu would ultimately be the best solution in your case, assuming that you are prepared, and have the time necessary, to migrate your files to a new OS. 

I run 64-bit Kubuntu on my PC, and have yet to come across any disadvantages - all of the applications I use are available, and the system runs smoothly.

Oh well, I hope this is some help.

* Swiveller *

---

### Post by Yellow Pasque on 2008-04-09
If you just had a few apps in mind for 64-bit goodness, you could look into making a chroot environment. 

Really though, it's time to bite the little bullet and install the amd64 version when Hardy/8.04 is released.

---

### Post by David J Bush on 2008-04-09
Okay, looking up "chroot environment" in the Ubuntu help pages I find this warning:

"Make sure to install at least the version of                 **debootstrap** that is from the                 Ubuntu release for which you are trying to create the chroot.                 You may have to download it from [packages.ubuntu.com]("http://packages.ubuntu.com/")                 and manually install it with **dpkg                     -i**."

debootstrap depends on binutils and wget, which in turn have dependencies and so on. Would the 32-bit packages that make up this dependency tree satisfy a 64-bit debootstrap?

Also, they warn me that "creating a chroot environment will take some time." Ah, how much time on a dialup modem? A ballpark estimate would be helpful. Ironically, I do have an install DVD for 64-bit Gutsy, but when I try to add it to the sources list, my 32 bit OS can't read the disc.

This is an interesting exercise if nothing else. Thanks for any help.

---

### Post by Kilz on 2008-04-09
> **David J Bush said:**
> Okay, looking up "chroot environment" in the Ubuntu help pages I find this warning:

"Make sure to install at least the version of                 **debootstrap** that is from the                 Ubuntu release for which you are trying to create the chroot.                 You may have to download it from [packages.ubuntu.com]("http://packages.ubuntu.com/")                 and manually install it with **dpkg                     -i**."

debootstrap depends on binutils and wget, which in turn have dependencies and so on. Would the 32-bit packages that make up this dependency tree satisfy a 64-bit debootstrap?

Also, they warn me that "creating a chroot environment will take some time." Ah, how much time on a dialup modem? A ballpark estimate would be helpful. Ironically, I do have an install DVD for 64-bit Gutsy, but when I try to add it to the sources list, my 32 bit OS can't read the disc.

This is an interesting exercise if nothing else. Thanks for any help.

I think the idea of a chroot was meant to show you that a 64bit install would be a better idea. A chroot will be an install, inside an install. It will take as long as downloading a complete 64bit install would. Along with the huge amount of hard drive space, they are hard to setup and configure. This is a reason not many people use them anymore. It is easy to get 32bit applications running on a 64bit install without a chroot (not that any are required).

---

### Post by gsmanners on 2008-04-09
Another thing to try would be KVM or some other virtual environment for your 64-bit programs. You'd have to install a complete 64-bit OS, but you'd have that ability then.

---

### Post by David J Bush on 2008-04-09
What about a source file package which is not listed in any repository. It doesn't depend on any other packages, and no packages depend on it. I want it to compile for the AMD 64 architecture. Would I need a chroot environment for that? I just want to change the .config.ini file, or use some command line option when I call configure, or hopefully something similar so the compiled package will run in 64 bit glory.

Thanks for your time.

EDIT: On second thought, the package does require kde headers.

---

### Post by Kilz on 2008-04-10
> **David J Bush said:**
> What about a source file package which is not listed in any repository. It doesn't depend on any other packages, and no packages depend on it. I want it to compile for the AMD 64 architecture. Would I need a chroot environment for that? I just want to change the .config.ini file, or use some command line option when I call configure, or hopefully something similar so the compiled package will run in 64 bit glory.

Thanks for your time.

EDIT: On second thought, the package does require kde headers.

It is not possible to run a 64bit application on a 32bit install. But it is possible to install a 32bit application on a 64bit install. A chroot is a complete 64bit install inside a 32bit install, thats why it works. But there are other issues. If you have the room why not do a duel boot 32/64bit system to see if there are any issues that would keep you from running a 64bit system.

---

### Post by Half-Left on 2008-04-10
When you compile something in x86_64 then it takes the compiler flags from the compiler, which would be x86_64, you shouldn't need to change anything.

Only mame do you have to set the compile flags in it's own file.

---

### Post by Yellow Pasque on 2008-04-10
> I think the idea of a chroot was meant to show you that a 64bit install would be a better idea. A chroot will be an install, inside an install.

Exactly. DJB, it seems you're looking for a painless (in terms of time/effort) solution here and there isn't one. Embrace the suck, backup your data, repartition for a dual-boot (or better yet, commit to 64-bit and just keep your /home folder). Let us know when you're ready and we'll help you through it.

---

