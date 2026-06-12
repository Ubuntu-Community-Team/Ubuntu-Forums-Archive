---
title: "Stuck at loading screen"
date: 2006-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by daz_138 on 2006-11-01
Hi 

I am a relative new user of Ubuntu, and have installed the 64bit version on a dual boot system with 2 hard drives.

I have had this problem for about 2 weeks, I can load ubuntu onto the second drive without any problems and the system restarts after install.  However from this point on when I shut down the system it will not load up again.  The grub loads and i can select XP or Ubuntu with no problem, if i select Ubuntu it decompresses and the kernel boots- the loading screen appears but the loading bar just sits there and nothing else happens no matter how many times I try.

I have already re-downloaded the iso in case there was a problem with the burned CD and have installed around 30 times but the same thing keeps happening.  Does anyone have any thoughts or suggestions on this?

If i keep rebooting after about 25 times it actually sometimes loads................

My system:
AMD FX60
Asus A8N32-SLI Deluxe Motherboard
2 x Nvidia 7900 GTX 512 mb

thanks

---

### Post by mbeierl on 2006-11-01
Have you tried the "single-user mode" boot to see if it spits out any more meaningful messages?

---

### Post by kuja on 2006-11-01
Did you install with the alternate or live cd? Does the live cd boot ok? If not, it could possibly be an issue with something like ACPI or APIC. It could also possibly be a problem with the graphics card drivers. Can you boot into rescue mode?

If you can boot into rescue mode, try this:
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

The open source nv driver may not like your SLId video cards, so what the above does is install the drivers from NVidia's website, which support SLI.

Nice system btw.

---

### Post by olieviya on 2006-11-15
Oh, I have the same problem, any ideas? I get it about 1 out of 3 times i try to turn on my pc. Ubuntu just freezes while loading and I am forced to restart... :confused:

I am on an Alienware m5550, specs:
CPU: Intel Core 2 Duo Processors (2MB Cache, 667MHz FSB)
Graphics: 128MB ATI Mobility Radeon X1400
HDD: 100GB SATA with NCQ
Monitor: 15.4&#8221; Wide Screen WXGA 1280 x 800
:-?

---

### Post by RFScheer on 2006-11-15
This was happening to me after I upgraded from dapper 32 to edgy 64.  I was able to improve things but eventually concluded that a clean install (using a downloaded iso) was the way to go.  Luckily, my home directory is on a separate partition, so reinstalling is not so bad.  No problems like that remained after a clean install, although it's been a bit of a road to get all 32 bit apps to have sound.

---

### Post by olieviya on 2006-11-16
> **RFScheer said:**
> This was happening to me after I upgraded from dapper 32 to edgy 64.  I was able to improve things but eventually concluded that a clean install (using a downloaded iso) was the way to go.  Luckily, my home directory is on a separate partition, so reinstalling is not so bad.  No problems like that remained after a clean install, although it's been a bit of a road to get all 32 bit apps to have sound.

Mine is a clean install as well, don't know how re-installing for a 5th time will actually help. .iso is good.

---

### Post by ubbi_nub on 2006-11-16
I am having this exact same problem.

I am using 

[B]Opteron 165
Asus A8N32SLI - Deluxe
Radeon X1900[/B]

**Hard drives: **
**1 Sata1 120gb hdd** on primary sata 1 channel. Master (Shows up as "sda") This is where grub is installed and where my windows xp installation is.

**1 Sata1 120gb hdd **on secondary sata 1 channel. Master (Shows up as "sdb") This is where I installed 6.10 on using the gparted guided install/partition and used the whole disk for Ubuntu. 

[B]Nvraid "fakeraid" setup: 
2 Sata1 300gb[/B] hdd on channels 3 and 4 in raid 1 configuration.

When I boot my machine, it boots up to grub, and if I select windows xp, windows boots without any problems. If I select Ubuntu, it returns an error 17. I found it had mapped the partition wrong and when I redirected it to boot from hd(1,0) it would _boot into the ubuntu splash screen and then hang after increasing the loading bar by only a few pixels. _

When booting into recovery mode, I find it hangs at usb HID core driver 2.6 loading. If I go back and disable ACPI in the bios, it continues to boot up past the USB issue, but then hangs at "initramfs" then says something about alert dropping to shell. 

I can boot and install from both the amd 64bit and pc 32bit 6.10 live cds. 

Any help for this super linux nub would be wonderful. Thanks!

---

### Post by plcdfa on 2006-11-17
First you should try deleting the "quit" option from the the kernel line in the boot menu and boot that way. (Press e on ubuntu in the grub menu.) This way the actual booting steps are printed on the loading screen and you could identify which is the problematic one. Switching to the first console (ctrl+alt+f1) might even give usable error messages.

---

### Post by jonccnoj on 2006-11-20
I am too having the same problem, having installed Edgy yesterday.

I am also using the Asus A8N32SLI - Deluxe.

One curiosity is that if I only have one HD plugged in (the nVidia SATA port), then everything boots fine. As soon as I plug in the other drive (the one with windows on), I get the problem as described. This is using the same GRUB config both times...

From a bit of searching, I am going to try adding acpi=force lapic to the   "/kernel/" GRUB entry. I think there are several ACPI= values that you can try, including ACPI=off.

I'll let you know how I get on.


edit:

I found this list [here]("http://web.bii.a-star.edu.sg/~tanyh/jotterbook.html"):


AFAIK the kernel options for APIC and ACPI are,

ACPI is commonly used when you need to acquire info about system's AC Power, 
Thermal, Battery, etc. Additional manipulations available like "ht", not sure
what it does.
acpi=off    } - disable ACPI
acpi=on     } - enable ACPI
acpi=ht     } - use ACPI for CPU enum only (hyperthread, interrupts routing)
acpi=force  } - to override the blacklist


APIC is still new to me, i'm still reading more about it.
apic        } - enable APIC
noapic      } - disable APIC
lapic       } - enable local APIC
nolapic     } - disable local APIC

---

### Post by AbEx on 2006-11-20
Had that issue with any 64 bit cds on my asus m2npv-vm. Booting with nolapic and noapic during the install worked for me. I didn't need to do this after I installed the system though. Booting with acpi=off meant no usb... All my keyboards and mice are usb. I believe it has to do with the bois and there is a bios update that will correct this problem, I haven't applied it.

---

### Post by jonccnoj on 2006-11-21
I thought I'd add an update. I re-installed edgy, but this time with both of my HDs connected (before I only had my non-windows one connected, to prevent accidental deletion/overwriting).

It all installed and is now booting up fine. So there must be some more configuration going on behind the scenes over and above what is seen to be happening (in grub etc).

A bit strange....

---

### Post by canisyursus on 2006-11-21
I have had a similar problem, but this is only when i try to boot with something plugged into my USB ports, it still did not work after i unplugged them, I had to clear out ram for it to boot correctly ... so i guess i have a problem with mounting my usb bus any suggestions. I am running a pesario r3000 64 laptop...

---

