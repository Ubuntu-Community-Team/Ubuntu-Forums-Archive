---
title: "Boot from Live CD"
date: 2007-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by DragonzBreath on 2007-12-11
Hi Guys,

This is the first time I have tried to use Linux in years. The last time I tried was SUSE at least... 4 years ago and I was given a terminal session, that was enough to scare me off.

Anyhow... I was sent the GG CD's (32bit and AMD64) and I've tried to boot to the Live OS and after the splash screen, I get nothing.

I read another thread that mentioned removing 'splash' from the boot command because the monitor was going into sleep immediately after the splash screen completes the progress bar. It appears that is not the problem I'm facing.

I'd really appreciate some help.

---

### Post by azbarcea on 2007-12-11
Do you know what processor type your computer has?

The Live OS should boot flawlessly (for an x86 processor):
 * if u have a 32 bit type processor you should use the Live CD for 32 bit
 * If u have a 64 bit type processor you may use any of it. We recommend the 64 bit Live OS.

Now ... do you have any specific questions?

---

### Post by DragonzBreath on 2007-12-11
> **azbarcea said:**
> Do you know what processor type your computer has?

The Live OS should boot flawlessly (for an x86 processor):
 * if u have a 32 bit type processor you should use the Live CD for 32 bit
 * If u have a 64 bit type processor you may use any of it. We recommend the 64 bit Live OS.

Now ... do you have any specific questions?

Yes... I have an AMD 6000+. And I've tried both 32bit and 64bit versions of the Live CD. And I've now tried the alternative CD also... I get the same issue with all three...

After the splash screen I don't get anything else displayed on my PC.

Specific? Like, how do I get this ******* thing to work?

---

### Post by wespad on 2007-12-11
Where did you get your CD? Did you burn it? I had some problems running the live CD on my new system, with a disc I burned on my old system. It was the disc that was the problem.

---

### Post by Existentialist on 2007-12-11
I have the same issues at boot with and without the live cd.  I believe it was something to do with the nvidia graphics card I am running, sometimes I do not get a splash screen at all and sometimes the login GUI doesn't appear.  For me, it works to just switch shells (ctrl+alt+F5) or any of the other shells, and then switch back to the x windows one (ctrl+alt+F7).  Do this when the screen goes blank after booting.

I disabled the splash at boot since I couldn't see it anyways and then set it to show the standard dmesg output just scrolls at boot.  To do this change your grub entry at boot, or from the /boot/grub/menu.lst from looking something like this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4a757c22-ff81-458f-99dc-cef00037290a ro **quiet splash**
initrd		/boot/initrd.img-2.6.22-14-generic
**quiet**

remove the stuff in bold to get:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4a757c22-ff81-458f-99dc-cef00037290a ro
initrd		/boot/initrd.img-2.6.22-14-generic

Not sure if this is the same type of problem you are having, but hopefully it is of some help to you.

---

### Post by DragonzBreath on 2007-12-11
> **Existentialist said:**
> I have the same issues at boot with and without the live cd.  I believe it was something to do with the nvidia graphics card I am running, sometimes I do not get a splash screen at all and sometimes the login GUI doesn't appear.  For me, it works to just switch shells (ctrl+alt+F5) or any of the other shells, and then switch back to the x windows one (ctrl+alt+F7).  Do this when the screen goes blank after booting.

I disabled the splash at boot since I couldn't see it anyways and then set it to show the standard dmesg output just scrolls at boot.  To do this change your grub entry at boot, or from the /boot/grub/menu.lst from looking something like this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4a757c22-ff81-458f-99dc-cef00037290a ro **quiet splash**
initrd		/boot/initrd.img-2.6.22-14-generic
**quiet**

remove the stuff in bold to get:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4a757c22-ff81-458f-99dc-cef00037290a ro
initrd		/boot/initrd.img-2.6.22-14-generic

Not sure if this is the same type of problem you are having, but hopefully it is of some help to you.

Awesome, I'll look into this later! Thanks...

I had someone mention that they think it could be to do with the resolution of the monitor. Native res is 1680x1050. Is it possibble???

---

### Post by azbarcea on 2007-12-18
very possible ... how did it go?

---

### Post by tensai_999 on 2007-12-18
if your problem is that after selecting the "install ubuntu" in live cd menu option your monitor turns into blank(led turns to orange from green). used the alternate cd but the same scenario would appear upon every time you  boot after you have installed it but it would only last 20 sec then after that it would go to your logon screen, so to avoid it every time you boot edit the /boot/grub/menu.lst and add the line vga=*** wherein *** is the colors of your screen resolutuion supported by your monitor see the table at [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)).

another way is by adding the option vga=*** in the boot option of the live cd aside from the quiet splash option

---

