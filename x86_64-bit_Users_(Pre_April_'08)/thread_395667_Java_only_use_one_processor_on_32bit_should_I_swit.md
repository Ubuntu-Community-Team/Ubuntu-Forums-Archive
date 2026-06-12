---
title: "Java only use one processor on 32bit should I switch?"
date: 2007-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Biochem on 2007-03-28
Hello all,
I'm using a Java software for my image analysis and just discovered that it only use one of my CPU. Since I need heavy calculation I was wondering if switching to Ubuntu x64 will enable me to increase the speed. Also note that there is no dedicated x64 bit version of ImageJ and I have no clue if that will affect the performance.

I know there is problem with unavailable plugin and driver for x64 so I'm considering dual booting (XP, Ubuntu32 and Ubuntu64). That way I can forget flash only when I'm doing weird heavy stuff (I'm still new to this linux stuff so I want keep it as simple as possible). Can I easily do that or should I expect GRUB conflict?

Thank You

---

### Post by maxamillion on 2007-03-28
the Java virtual machine (to the best of my knowledge) still performs all calculations in 32-bit mode within the VM no matter what platform you are on (if I am wrong, someone please correct me because I would hate to give false information) 

also, java isn't using the second processor probably because the application wasn't written with processing threads geared for a multi-cpu or multi-core machine.... otherwise the jvm might not be taking advantage of the other cpu like it should and there might just be an issue somewhere

.... this might not have really helped now that i re-read it, but i hope it atleast gives you a little insight on a couple reasons its not using that other cpu and about moving to 64-bit linux

---

### Post by Kilz on 2007-03-28
> **Biochem said:**
> I know there is problem with unavailable plugin and driver for x64 so I'm considering dual booting (XP, Ubuntu32 and Ubuntu64). That way I can forget flash only when I'm doing weird heavy stuff (I'm still new to this linux stuff so I want keep it as simple as possible). Can I easily do that or should I expect GRUB conflict?

Thank You

You can install multiple versions of Ubuntu without problems. As for the unavailable plugin, you are incorrect. Flash is available, but it takes a little setup. You can run a 32bit firefox with flash/java on the 64bit version. There is also nspluginwrapper, but it is difficult to install/make work . Also nspluginwrapper does not work with java.

---

### Post by Biochem on 2007-03-29
Thanks guys,
@ maxamillion
So if I understand you well Java will still be 32bit and therfore if it doesn't take advantage of the second CPU now it will probably no do it on X64.

@ Kilz
I know that there are work around for almost anything (from what I read you still can't print from the 32bit firefox on x64). Its just that I still on a 12 step program  of MA (Micro$oft anonymous):lolflag:  So I still have much to learn about linux and adding layers of complexity is not for now if I don't have immediate benefit from it. Might get back to it in a few month though.:)

---

### Post by Kilz on 2007-03-29
> **Biochem said:**
> 

@ Kilz
I know that there are work around for almost anything (from what I read you still can't print from the 32bit firefox on x64). Its just that I still on a 12 step program  of MA (Micro$oft anonymous):lolflag:  So I still have much to learn about linux and adding layers of complexity is not for now if I don't have immediate benefit from it. Might get back to it in a few month though.:)

This work around has a script that will install 32bit Firefox with flash, java , and mplayer plugins. I think even my mother could install it.

---

