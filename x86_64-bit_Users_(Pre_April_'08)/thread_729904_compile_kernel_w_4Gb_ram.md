---
title: "compile kernel w/ 4Gb ram"
date: 2008-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Virtual_Ron on 2008-03-20
I've pulled all but 3 of my hairs out!

I had 2GB of ram on my machine, and decided to install 2GB more.

It hung on boot, until I added the "mem=4096M" to the grub kernel paramaters.   Then it booted fine.
But, only reported 3.48GB.    

**kernel: [   17.760413] Memory: 3442944k/3537792k available (2333k kernel code, 94460k reserved, 1242k data, 312k init)**

I read every post I could about this problem... then ended up downloading and compiling the latest kernel 2.6.24.3.

After compiling and installing the new kernel, the machine booted up fine, and showed 3.88Gb. WITHOUT using the "mem=4096M" parameter.    Much better.
[B]
kernel: [   16.795009] Memory: 3885540k/4718592k available (2333k kernel code, 176152k reserved, 1242k data, 312k init)
[/B]
Then, I had to re-install my ATI drivers.    When I rebooted after installing them, my machine hung again.  I re-added the "mem" parameter in grub, and the machine booted fine.....   but, was back to the 3.4Gb of ram again.

**kernel: [   17.760413] Memory: 3442944k/3537792k available (2333k kernel code, 94460k reserved, 1242k data, 312k init)**

What the hell?  All I did was reinstall my ATI drivers.

AND, now when I do a restart or shutdown, the machine hangs at a black/blank screen.    It shuts down the desktop, and just before I see the normal Kubuntu shutdown spash screen, it hangs.   I believe its when it shutting down X...

Anybody have any clues or ideas for me?   You'll be my hero, and I'll tell everyone I meet on the street that your Mojo is the best!

Thanks,
Ron

_Various Specs:_
AMD64 X2 Dual 6000+
Ubuntu "Gutsy" x86_64
ATI Radeon X1200
ATI 8.3 video drivers
KDE 3.5.8
4G of ram

---

### Post by Triggerhapp on 2008-03-20
> 3885540k/4718592k available Looks to me like its using some? Im no where even close to professional, but i've seen things happen like this, took me a while to realise my graphics card steals some of my normal memory for its own XD

---

### Post by Virtual_Ron on 2008-03-20
> **Triggerhapp said:**
> Looks to me like its using some? Im no where even close to professional, but i've seen things happen like this, took me a while to realise my graphics card steals some of my normal memory for its own XD

Oh, I'd be happy with the 3.8Gb, but after my ATI driver updates, it went back to 3.4Gb.

---

### Post by Triggerhapp on 2008-03-20
I meant the fact that its reporting 3.8g as available, and 4.5gb as maximum ram XD

---

### Post by ian dobson on 2008-03-20
Hi,

Go into your bios and enable memory remapping.

Some (Read Graphic Cards) sit in memory just below 4Gb (Are you old enough to remember 640kb?) so this range cannot be used my Linux. Enabling memory remapping moves this block of memory above the 4Gb range so linux can use it.

Regards
Ian Dobson

---

### Post by Virtual_Ron on 2008-03-21
> **ian dobson said:**
> Hi,

Go into your bios and enable memory remapping.

Some (Read Graphic Cards) sit in memory just below 4Gb (Are you old enough to remember 640kb?) so this range cannot be used my Linux. Enabling memory remapping moves this block of memory above the 4Gb range so linux can use it.

Regards
Ian Dobson

Thanks Dude.   I looked, but didn't have any of these settings in my BIOS.   So, i checked out Asus's website and it seems my jesus..err  Asus board had an old buggy bios on it.   So I upgraded it, and VIOLA, I had all my memory when booting up.   nice.   Thanks for the tip.

Unfortunatly, now my machine doesn't have any audio.    Don't know what update broke that... i'm sure it was the new kernel...

I have an ASUS M2A-VM HDMI motherboard, with onboard audio.   was working fine until...

Anybody have any tips to correcting that?  I can't see anything related in the syslogs...     When I start armok, or kaffiene, I get an error "all audio drivers failed to initialize"

:confused:

---

### Post by soxs on 2008-03-21
maybe the biosupdate reseted all biossettings and disabled the onboard audio?

---

### Post by Virtual_Ron on 2008-03-21
> **soxs said:**
> maybe the biosupdate reseted all biossettings and disabled the onboard audio?

Thanks.   I just checked my bios settings, and the onboard audio IS turned on. 

Also, when I run 'lspci" it shows up:
**01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller**

 I guess I could load the old bios and see if the audio comes back...

---

### Post by Virtual_Ron on 2008-03-21
Well, I downloaded the ALSA hda-intel drivers, compiled and installed the kernel modules, and VIOLA, my sound is back.

I guess I crushed them when compiling the new kernel.

Thanks all.

---

