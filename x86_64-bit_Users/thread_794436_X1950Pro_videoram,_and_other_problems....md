---
title: "X1950Pro videoram, and other problems..."
date: 2008-05-14
forum: x86 64-bit Users
---

### Post by RubberSoul on 2008-05-14
I have a Sapphire X1950pro and a SB X-Fi Fatal1ty Platinum Champion Series, my system is running ok, but i got some problems:

Sound in flash... Too many people with this one...
Java wont work properly... Too many people with this too...

And

My video card only show 128MB ram... It has 512MB... I dont find any information about that... Please, if anybody can help... Theres a good hadrware manager for 8.04 (64bits) that can show hardware information? Sysinfo? Any other better? (yes, i'm noob in linux too)

Thanks for the help.

---

### Post by Yellow Pasque on 2008-05-15
> Java wont work properly... Too many people with this too...
Read the sticky'd threads in this forum...

> Sound in flash... Too many people with this one...
Read the sticky'd threads in this forum...

> My video card only show 128MB ram...
Try this command to see how much X is finding:
```
dan@harvest:~$ **cat /var/log/Xorg.0.log | grep RAM**
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR2
```

---

### Post by RubberSoul on 2008-05-15
Hummm, thanks for ur reply, i found that:

(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR3
(II) Initializing built-in extension XINERAMA

So i was wrong, theres not 128mb, but 256mb... What should i do now?! The right value is 512mb...

---

### Post by RubberSoul on 2008-05-23
Still need help on VideoRam problem... Got a 512 card, but only 256 working...

---

### Post by soxs on 2008-05-23
Wow, I aswell only get 256 out of 512..
Though I use VideoRam option with my ramsize in kb

Catalyst Control Center shows 512.. odd -.-

---

### Post by RubberSoul on 2008-05-23
My Catalist Control Center shows only 128... =/
HELPPPP =]]

---

### Post by soxs on 2008-05-23
has anyone tried Fedora with the (mor or less) _latest_ xserver?

---

### Post by RubberSoul on 2008-05-25
Well... Ubuntu (Hardy 8.04 64Bits) is the first distro i ever use... Its very good, i'm liking it. But i got some problems, X-fi issues, and the ones related in this post..

I think that videoram problem is easy to solve, so keep asking for help... =]

---

### Post by soxs on 2008-05-25
Ok, I just installed fedora, but 8.5 is still noct cpable of the latest Xorg fedora 9 sulphur uses -.- so I can't test it, as fglrx refuses to build (downgrading wouldn't help anyways, the result would be much like ubuntu 8.04) -.-

---

