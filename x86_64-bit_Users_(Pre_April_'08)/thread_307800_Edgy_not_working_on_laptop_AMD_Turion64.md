---
title: "Edgy not working on laptop AMD Turion64"
date: 2006-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by finite9 on 2006-11-27
One very irritated and annoyed Ubuntu user:

I have used Dapper (Gnome) 64-bit for a year and it has worked perfectly.  I decided that 1 month after Edgy release was enough to 'let the dust settle' and hopefully any major bugs would be fixed in the repositories, so on Friday I upgraded using gksu "update-manager -c".

Upgrade went perfectly...took 10 minutes to download the tarball.  No errors whatsoever apart from asking if I wanted to overwrite GDM conf file.  Reboot borked my system.

1. Black and white splash.  It's cool, it's cool...no biggie, will fix itself in time and not an issue for me with nosplash.

2. No amd64 kernel.  Sort of cool...what happened to optimised kernels?

3. System hangs at different stages whilst doing different things.  Not cool at all.  I get errors on boot about BUG: soft crash on CPU#0!  I was using 2.6.15-27-amd64-k8 in Dapper and notice that it's the generic 2.6.17-10 in Edgy.  This kernel does not work with my system (AMD Turion64 ML28).

I downloaded the Edgy desktop ISO, and did a clean install (/home on separate part. so no biggie).  Same issue with clean install after having formatted / and swap.  What gives?  For a start, it seems a bit dubious with the amd64-k8 kernels being 'obsoleted'  Maybe this is right?  Does anyone have solid info on this from the devs where they state that the generic kernel includes all optimisations for all architectures out of the box?  Otherwise, to me it seems like they just don't have resources to support all kernels.

I heard about -noapic etc, but why would I want to cripple my system (no usb for example) but using -noapic??  This is not a solution in my opinion, only a very short term workaround to be able to boot and troubleshoot.  I have not tried this...I found out about it today after already having reinstalled Dapper.

So now, I had to do another clean install of Dapper and go back to what I had.  Big disappointment for me, as many issues that I have with Dapper are fixed in the software in Edgy.

Why the buggy kernel in Edgy?  Why has the black and white splash not been fixed after 1 month?  Do all amd64 users see this?  It cannot be video card specific as it hasn't even loaded the gfx modules for X at that point and I can see on other threads that many nvidia users have this issue and I have ATI Mobility X700 PCI-E!?  I have an i386 install of Edgy at wotk on a Pentium4 HT and the splash is fine there and no crashes with the kernel.  Is the splash problem amd64 specific?

---

### Post by stormy315 on 2006-11-28
I have the same problem... except it hangs at that splash screen. The loading bar goes outside of the area that it should be in... and it isn't filled in at all... I can only see the hash marks of the bar.

I've left the install there (i'm doing a clean install) for quite a while and it gets no further.

my computer specs are (only the important ones)
AMD64 3400+
nVidia 6800XT
SATA HDD

I am very disapointed in not being able to take advantage of my x64 CPU... :(
Guess it's 32 bit for me until they fix this... :/

This guy had a similar or the same problem:

[https://launchpad.net/distros/ubuntu/+ticket/2169](https://launchpad.net/distros/ubuntu/+ticket/2169)
(look at his post near the middle of the page or so... it talks about the problem I have)

---

### Post by RAOF on 2006-11-28
The optimised kernels were removed for a couple of reasons:
1) New optimisations in the kernel code itself meant that the -k8, -xeon, etc kernels weren't actually appreciably faster than the -generic kernel.
2) It's quicker to build, and simpler to support, 1 -generic kernel than multiple CPU specific kernels.

Black and white splash is a work-around for stupid nVidia drivers on AMD64.  You get a black and white splash instead of no splash at all, and a 5 minute boot time.  I'm not sure, but I don't think it's likely to be fixed in Edgy anytime soon.  Maybe they'll backport Feisty's bootsplash, if they can fix it there (it's not fixed yet).

The kernel is buggy for you presumably because no-one with your hardware submitted bug reports early enough during Edgy testing.  Checking out [launchpad.net](launchpad.net) says you probably have [this](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418) problem.  Looks like they're aware of it, it's an upstream bug, and that a work around is to have your wireless turned on at boot :).

---

### Post by finite9 on 2006-11-29
Thanks for the solid info RAOF!  I do not have an nvidia card...does the black and white splash issue apply to ATI as well? (I suppose it must as I have the problem).

It would be interesting to see if there is any performance difference when ripping music CDs or transcoding video between a 2.6.15-27-amd64-k8 kernel and a 2.6.17-10.33-generic kernel.  Is it at all possible, after upgrading to Edgy, to boot with the older 2.6.15-27 kernel?  Would this work at all or would Edgy complain loudly?

If it really is the case that I have the bug you refer to in launchpad, then I am truly screwed, as I have an Acer Aspire 5021WLMi laptop with a broadcom bcm43xx chip, and I need to load  an acer_acpi module to be able to turn on the adapter through software as it is not possible to turn it on through hardware/bios.  I load acer_acpi in /etc/modules, but I suppose it depends on when /etc/modules gets called...I experience the crashes quite soon after boot, so maybe that's before modules even gets called?

---

### Post by RAOF on 2006-11-29
> **finite9 said:**
> Thanks for the solid info RAOF!  I do not have an nvidia card...does the black and white splash issue apply to ATI as well? (I suppose it must as I have the problem).

It would be interesting to see if there is any performance difference when ripping music CDs or transcoding video between a 2.6.15-27-amd64-k8 kernel and a 2.6.17-10.33-generic kernel.  Is it at all possible, after upgrading to Edgy, to boot with the older 2.6.15-27 kernel?  Would this work at all or would Edgy complain loudly?
...

1) AMD64 usplash runs in black and white, always.

2) You may well be able to boot with the .15 kernel.  The newer kernel will support more hardware and may be a bit faster (but not increadibly so), but if the .15 one boots reliably and the .17 one doesn't... :).

---

