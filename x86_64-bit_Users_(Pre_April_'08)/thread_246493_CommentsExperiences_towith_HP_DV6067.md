---
title: "Comments/Experiences to/with HP DV6067"
date: 2006-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by martinrandau on 2006-08-29
Hi,
I've bought a HP DV6067 laptop and I'm going to dualboot windows and ubuntu. I wonder if anyone here has any experience with this computer or similar models. Are there any serious problems that would prevent me from installing ubuntu 6.06 on it? I have good experience with both ubuntu and gentoo linux for 32 bit intel processors and ndiswrapper etc is no problem.

Here are the specs: 
```
AMD Turion 64 X2 mobile technique TL-52
2 GB RAM - DDR II SDRAM - 667 MHz ( 2 x 1 GB )
NVIDIA GeForce Go 7200 TurboCache 
Ethernet, Fast Ethernet, Bluetooth, IEEE 802.11b, IEEE 802.11a, IEEE 802.11g
```

Any help is appreciated!

Take care,
Martin

---

### Post by lmerte on 2006-08-30
I've got the dv6040, same processor, memory, video.  I just tried to start Ubuntu from the liveCD, but it froze (completely) during the boot-up process.. usually after configuring network interfaces..
No idea what's wrong, but I'm brand new to this.  Trying some other distros.

---

### Post by martinrandau on 2006-08-30
No, wait! Don't switch distro, I have the solution to your problem. :-D 

You have to pass acpi=off as a kernel parameter before boot. You do this by pressing F6 (I think)at the boot menu and then adding acpi=off to the other kernel parameters,

For me this works and both the videocard, soundcard and broadcom wlan card are detected, ie everything works!

---

### Post by shadowhywind on 2006-08-31
martinrandau You are a life saver *gives hug*. I have been useing Kubuntu for the last year and love it. Just recently i bought a dv6040 and decided to install kubuntu 64-bit (even the normal 32-bit version was giving me the same problem), After searching for an hour or two and finding nothing i found your post. AND IT WORKED! THANK YOU SO MUCH! I am going to make sure i write this down for future use. 

 I do have a few problems, it did not detect my wireless card, *still fighting with it*, My sound options are very limited. and my video settings i am not sure yet. Any ideas? I am thinking about doing a fresh install with giving the acpi=no at installation and see if that helps. 

THANKS AGAIN

---

### Post by martinrandau on 2006-09-01
Sadly enough, it's the acpi=off that disables both the sound card and wlan device. I struggled with this alot and then tried with suse 10.1. It had the same problems (no boot without acpi=off) but then I tried passing noapic to the kernel and now have both the wlan and the sound working. You might wanna try this. Good luck!

---

