---
title: "no Linux 1386 will unstall on my x86 64 machine."
date: 2008-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by morganpatrick on 2008-04-02
Hello,

I'm running an HP PC with dual amd64 processor.

I can install ubuntu 64. I can install ubuntu studio 64. I can install ubuntu studio i386.

I can't install any other distro that's i386. Open SUSE live cd, Jacklab, 64 Studio i386.

In Open SUSE and Jacklab, I can't get past installation because my keyboard and mouse don't work. In 64 studio I can install the os but when I boot the keyboard and mouse don't work. In the live CDs they don't work.

I've tried noapic, nolapic, acpi=off, acpi=oldboot, none of these flags help.

I guess this isn't really an Ubuntu question other than, why do my PS/2 keyboard and mouse only work on ubuntu 32-bit installations and nothing else?

Thanks in advance.

---

### Post by morganpatrick on 2008-04-03
Actually, now I can't install my 1386 Ubuntu Studio disc either. I have no idea what special blend of parameters I set before but now it's the same problem: I get to the beginning of the installation when I'm supposed to select a language, and my keyboard won't work.

---

### Post by jespdj on 2008-04-03
> **morganpatrick said:**
> ...I can't get past installation because my keyboard and mouse don't work.
Do you have an USB keyboard and mouse? Have a look at the BIOS settings of your computer and see if there is a setting called something like "Legacy USB keyboard / mouse support". Set it to enabled and try again.

But why would you want to install the i386 version if the x86_64 version works well on your computer?

---

### Post by morganpatrick on 2008-04-03
Nope, regular ps/2 mouse and keyboard.

I specifically want to run i386 because I'm trying to use my computer for audio production and most VST instruments are only 32 bit, and will only run in a 32 bit environment.

I also want to see if Jacklab can solve my myriad audio production woes and that only comes as an i386 distro. In general I've had a hell of a time getting anything audio to compile and install on my 64 bit OS.

---

### Post by jespdj on 2008-04-03
32-bit software also runs on 64-bit Linux. If you have software that for some reason checks the architecture and doesn't want to run unless it's i386, you can try running it using linux32, for example:
```
linux32 uname -a
```
You'll see that this reports i386 (or i686) even if you run it on an x86_64 system. So try running your program like this:
```
linux32 programname
```

---

### Post by morganpatrick on 2008-04-03
Thank you so much for the help. I have spent months trying to get my system the way I need it.

So you're saying I should add this to the boot parameters? Like where I would add acpi=off, noapic et cetera, this is where I should type this?

I'll try this in a moment. If there are any other options I'd like to hear them so I can write these down before I try to boot into the disc.

FYI: I'm getting this error:

```
Can't read CTR while initializing i8042
```

Which I'm investigating now. It appears this is directly linked to keyboard problems so if I can solve this I'll post the results.

---

### Post by morganpatrick on 2008-04-03
Apparently this is a known issue. I found a patch that is supposed to fix this bug in the kernel:

[http://marc.info/?l=linux-kernel&m=109508824931419&w=2](http://marc.info/?l=linux-kernel&m=109508824931419&w=2)

But I don't see how that really helps on an installation cd.

---

### Post by jespdj on 2008-04-04
> **morganpatrick said:**
> So you're saying I should add this to the boot parameters?
No, you just type "linux32" on the command line (in a terminal window) in front of the name of the program you want to run. It is not a boot time kernel parameter.

Try this: Open a terminal window, type "uname -a". It will display something like this:

Linux hostname 2.6.24-12-generic #1 SMP Wed Mar 12 22:31:43 UTC 2008 **x86_64** GNU/Linux

Now type "linux32 uname -a", and it will display:

Linux hostname 2.6.24-12-generic #1 SMP Wed Mar 12 22:31:43 UTC 2008 **i686** GNU/Linux

Note that the program "uname" now thinks it is running on 32-bit Linux (which you can see because it prints "i686" instead of "x86_64").

---

### Post by morganpatrick on 2008-04-04
Interesting... well somehow. by the grace of God, I was able to install 32 bit ubuntu studio, finally. my problems seemed to be related to acpi but I managed to get this installed with acpi=off, even though I swear I did that before to no avail.

Anyway thanks.

---

