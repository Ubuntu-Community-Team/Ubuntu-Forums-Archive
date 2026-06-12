---
title: "Trying to DualBoot 32bit XP on AMD64 Machine"
date: 2007-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by theROKR on 2007-06-29
Can anyone help me out with this one?
I have an old copy of XP, 32bit, and I need it on my AMD64 machine. Im trying to boot from the CD since Ubuntu wont recognize it. When I reboot it says:

```
Press Any Key To Boot From CD......
```

I press Enter.

```
Setup Is Detecting Your Computers Hardware Configuration...
```

It says that for about 3 or 4 seconds and then the screen goes blank and i have to pull the plug.
Is there any simple solution to my problem?

I have Ubuntu 6.06LTS running The Ubuntu[GNOME], Kubuntu[KDE], Xubuntu[Xfce], and Fluxbox[?] Desktops.
I am on a [Compaq SR1950NX]("http://www.dealtime.com/xPF-Compaq-Compaq-Presario-Sr1950nx-Media-Center-PC").

---

### Post by eddieb on 2007-06-30
Just a suggestion. Put the xp cd in the drive and reboot. I find my cd burner isn't recognised until I do that!!
Not trying to tell you how to suck eggs, but you do have the first partition of the first hard drive free? Xp requires it to be so! And you know you will lose the Grub menu. Good luck!

---

### Post by praxis22 on 2007-06-30
Sounds to me like it is booting from the XP CD, that's what I'd expect to see if you were re-installing.

But yes, XP needs to be located within the first 1024 cylinders of your boot disk I think. Easiest way to do this it to install another drive, and install windows onto that, just make sure you unplug the ubuntu drive when you do.

---

### Post by eddieb on 2007-07-01
I just noticed you have a Compaq. Years ago they used to be known as a Propriatory machine, meaning Compaq had a way of setting up their machines so only their version of Windows would work. If you tried to install another version of Windows the machine would refuse.

---

