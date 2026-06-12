---
title: "Latest VMWARE server version with amd64"
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by gearshifter on 2006-06-10
I am having problems detecting the audio device in windows xp emulation.  I have installed the correct drivers from the manufacturers website and it doesnt even look like it's installing the software.  

I have the nforce4 chipset with realtek sound.  It's dapper 64 wtih windows xp 32 emulation.

Anyone got any ideas?


Thanks
Jason

---

### Post by Elyas on 2006-06-11
That's why i've changed my Dapper from 64 bit to 32. Cause i had to many problems with vmware, wine etc.

---

### Post by gearshifter on 2006-06-11
no worries.. i got it all figured out :)

---

### Post by Kilz on 2006-06-11
[QUOTE=Elyas]That's why i've changed my Dapper from 64 bit to 32. Cause i had to many problems with vmware, wine etc.[/QUOTE]

All it takes to get answers sometimes is asking a question. Im sure some nice person here would have helped you out without haveing to use a 32 bit os on your 64 bit box. :D

---

### Post by HellSpawn on 2006-06-14
[QUOTE=gearshifter]no worries.. i got it all figured out :)[/QUOTE]


Share you're knowledge!! :confused: 

Please!!

---

### Post by gearshifter on 2006-06-15
you ahve to add the device to vmware itself.  Where your cpu, keyboard, etc are added, you have to add the sound device to that list.

---

### Post by Hendrik van den Boogaard on 2006-06-16
So basically what you mean is: the CPU is 'taken over' by vmware, so Windows XP does recognize the Atlhon64x2 where the soundcard actually is 'emulated' by some soundblaster compatible device so you *don't* need your *own* soundcards' drivers.

I actually upgraded from dapper32 to dapper64 and after reinstalling vmware, my old Windows XP (32) configuration still works like a charm (for what's worth it, running Windows ;)). It detects some more RAM (increased memory pool, because I upgraded an Ahtlon XP2800+ 1 GB Ram to a Athlon64x2 4200+ with 2 GB RAM) and the new processor.

Or do you mean that you actually have to tell the VMWARE config that you are going to use a soundcard in your guest OS?

Anyway, just to tell other readers; on my system an upgrade from Dapper32 to Dapper64 worked out without troubles so far.

---

### Post by nmsa on 2006-06-17
[QUOTE=gearshifter]you ahve to add the device to vmware itself.  Where your cpu, keyboard, etc are added, you have to add the sound device to that list.[/QUOTE]
is your printer (parallel) port working?
I can't have it working in vmplayer.
I'll try and use the USB for my Samsung MFP, but I wonder if you have it working.

these are my entries in the vmx file:
```
parallel0.present = "TRUE"
parallel0.fileName = "LPT1"
parallel0.bidirectional = "TRUE"
```

and this is the error message I have when I start the player:
```
Cannot open LTP1: No such file or directory
Virtual device parallel0 will start disconnected.
```

---

### Post by AVonGauss on 2006-06-17
The product "VMware Server" does not support sound other than the system beep if you are using the VMware Server Console to view the guest OS - you have to use RDP (Remote Desktop) or other similar remote software that allows for sound to hear any sound coming from a guest OS other than a system beep.  VMware player or the console in VMware Workstation do support sound coming from the guest OS as they do not use VNC as the primary protocol.

---

### Post by AVonGauss on 2006-06-17
[QUOTE=nmsa]is your printer (parallel) port working?
I can't have it working in vmplayer.
I'll try and use the USB for my Samsung MFP, but I wonder if you have it working.

these are my entries in the vmx file:
```
parallel0.present = "TRUE"
parallel0.fileName = "LPT1"
parallel0.bidirectional = "TRUE"
```

and this is the error message I have when I start the player:
```
Cannot open LTP1: No such file or directory
Virtual device parallel0 will start disconnected.
```[/QUOTE]

If you're using Ubuntu as the host OS, should the printer be something like "/dev/lp0" or "/dev/usb/lp0"?

---

### Post by Hendrik van den Boogaard on 2006-06-17
Perhaps I should read the title first ;). I actually use VMWare Workstation, and that does make a difference :).

For the parallel port; do you have the module for a 'raw connection to the printerport' installed? I thought this was called parport. So you might try: *modprobe parport* and then start Vmware again.

---

### Post by eaglefly21 on 2006-06-21
To reply to the post from AVonGauss: 
>>The product "VMware Server" does not support sound other
>>than the system beep if you are using the VMware Server 
>>Console to view the guest OS - you have to use RDP (Remote 
>>Desktop) or other similar remote software that allows for 
>>sound to hear any sound coming from a guest OS other than 
>>a system beep. VMware player or the console in VMware >>Workstation do support sound coming from the guest OS as 
>>they do not use VNC as the primary protocol.

On what information do you base this "fact" that you have posted? I have been using all versions of vmware (up to and including the newest server v1.x), and know for a fact that sound works as expected, provided that you have set up the virtual soundcard in vmware, and that you actually have a real sound card in the machine that vmware is running on top of. If you do not have a sound card installed, no sound.

---

