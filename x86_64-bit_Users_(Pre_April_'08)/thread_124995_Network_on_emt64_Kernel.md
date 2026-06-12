---
title: "Network on emt64 Kernel"
date: 2006-02-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by gucampos on 2006-02-02
well, some search in the forums and at google and got nothin, so...

...here's the problem:

I was always an user of Debian. Recently I've bought a new 64 PC, powered by a Intel Pentium 630 processor (3.0 HT 64bit).

So I installed Debian amd64, and downloaded the intel emt64-smp kernel

After that, my network card stopped to function, and I was not able to connect to the Internet through my cable modem.

Then, I switched to Ubuntu. Installed the amd64 bit version, downloaded the emt64-smp kernel and guess?

NO INTERNET xD

The emt64 kernel simply will not detect my network adapter, and I have no idea of why would it do this so bad thing to me =/

Anyone got the same problem? Any tips to solve it?

I thank you in advance =)

P.S. - If I boot on the generic amd64 kernel, my network adapter works pretty fine ^^

---

### Post by RAOF on 2006-02-02
Well, it seems that there are two possibilities here.  Either SMP is messing up your network drivers, or the EMT64 specific compile for the kernel is.  If the generic amd64 kernel works, use that for the moment.  Unless someone can think of some way you could fix this on your own, I think you'd be best off hitting [www.launchpad.net](www.launchpad.net) and filing a bug against the EMT64 kernel.  Maybe they (accidentally) just haven't built support for your card into that kernel?

---

