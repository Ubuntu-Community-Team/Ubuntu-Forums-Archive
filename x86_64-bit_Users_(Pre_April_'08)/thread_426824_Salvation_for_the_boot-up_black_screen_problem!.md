---
title: "Salvation for the boot-up black screen problem!"
date: 2007-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by firebird84 on 2007-04-28
I have been trying to solve this problem all day, going back and forth to the forums here, and since I didn't  see any solutions, I thought I'd post.

What was happening, was that during the non-alternative feisty install, there is a black screen upon Ubuntu starting to boot.  You can see the system doing things to your hard drive in the background, but you can't do anything else.  Also, once I installed using the alternative (text-based) installer for Ubuntu, when I booted into my system w/o recovery mode, I would get the same behavior (a black screen after the kernel is unpacked).  Turns out that the problem is the bootsplash which is enabled by default in Feisty.  At least, it's a problem for my hardware.  Here's my specs:

Intel QX6700 Core 2 Extreme Quad core
4 GB PC800 DDR2
eVGA nVidia 8800GTX (only x1 right now)
eVGA nForce 680i SLI mobo


Anyway, to install, download the alternative ISO from ubunto.com.  You have to click the checkbox at the bottom of the page.  This will give you a text-based installer, and will not bother with a bootsplash or any crazy eye-candy.

Once you have Feisty running, boot into recovery mode, and edit your grub config.  (/boot/grub/menu.lst).  Make sure to back up the file first!!!

Under the automagic kernel text near the bottom, you'll see some mumbo jumbo that looks kinda like this:

```
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet
boot
```

Change that to this:

```
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro
initrd /boot/initrd.img-2.6.17-10-generic
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet
boot
```

This keeps ubuntu from booting up with the bootsplash.  You lose some eyecandy, but at least it will boot properly until someone figures this out better than I can.

If you have the same hardware I do, you might want to also use the new envy 0.92 beta that alberto milone has up.  It was the only way I got X working right (it downloads the new 9755 drivers).

---

### Post by firebird84 on 2007-04-28
By the way, this was Feisty 7.04 AMD64, not i386

---

### Post by Synthetik on 2007-05-05
Thanks so much! That's been driving me nuts, I was sick of pressing esc every time grub started then selecting safemode.

I have:

AMD Athlon 64 3500+
1GB Ram
ATI X850XT
MSI K8N mobo

---

### Post by Tanker Bob on 2007-05-05
Thanks!  Works great here on my Feisty x86-64 setup.

---

### Post by roony1974 on 2007-05-07
Looks like the problem is really the monitor refresh rate since setting the resolution higher resolved the problem on my computer.

Now it boots flawlessly from the live kubuntu cd. 

I am writing this from live-cd on a EVGA 680i MB with 8800gtx gfx card and a Xeon3060 2,4Ghz CPU.

---

### Post by firebird84 on 2007-06-14
My LCD monitor's native resolution was 1280x1024 and could do 32 bit color so I did in /boot/grub/menu.lst:
```
# defoptions=quiet splash vga=0x31B
```

Leave it commented!! It works that way for some reason

then I did 

```
sudo update-grub
sudo reboot
```

And bam! I had a splash screen.  Now to find the vga codes for 1680x1050 ;)

---

