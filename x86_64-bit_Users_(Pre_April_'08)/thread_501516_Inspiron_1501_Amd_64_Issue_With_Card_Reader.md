---
title: "Inspiron 1501 Amd 64 Issue With Card Reader"
date: 2007-07-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by amaurynieto on 2007-07-15
Hello All, I'm hoping you can assist me. - I have the 64 bit version of Ubuntu installed, and unfortunately the Ricoh Card Reader included in my machine isn't working. I'm told through the ubuntu1501 blogspot that this was fixed with the kernel update to .17 - I have this update, however no cigar......

I'm wondering if it's to do with the fact that I'm running a 64 bit system.

Please help, I'd really love to have it resolved.

That, and the fact that DIVX videos play HORRIBLY on my 1280*800 display. I'm guessing it's the ATI driver (fglrx) for an Xpress 1150 (x200 chipset). It's all pixelated and looks like dog food (mind you, it's watchable, but nowhere near Nvidia's output).

Anyone have any feedback which might help me resolve the problem?

Thanks! A.

---

### Post by Kilz on 2007-07-15
> **amaurynieto said:**
> Hello All, I'm hoping you can assist me. - I have the 64 bit version of Ubuntu installed, and unfortunately the Ricoh Card Reader included in my machine isn't working. I'm told through the ubuntu1501 blogspot that this was fixed with the kernel update to .17 - I have this update, however no cigar......

I'm wondering if it's to do with the fact that I'm running a 64 bit system.

Please help, I'd really love to have it resolved.

That, and the fact that DIVX videos play HORRIBLY on my 1280*800 display. I'm guessing it's the ATI driver (fglrx) for an Xpress 1150 (x200 chipset). It's all pixelated and looks like dog food (mind you, it's watchable, but nowhere near Nvidia's output).

Anyone have any feedback which might help me resolve the problem?

Thanks! A.

Just one question, are you playing the video at the size it was encoded to? I'm still running Dapper and divx and dvd's play nice.

---

### Post by Mr_bleu on 2007-07-15
Have you tried System>Preferences>Removable Drives and Media>?
Just curious.  My e1505 has no problems with the Ricoh Driver.  
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: Dell Unknown device 01bd
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at ef9fd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Dell Unknown device 01bd
        Flags: medium devsel, IRQ 11
        Memory at ef9fd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Dell Unknown device 01bd
        Flags: medium devsel, IRQ 11
        Memory at ef9fd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
Run lspci -v  and post the results here.

---

### Post by amaurynieto on 2007-07-15
> **Kilz said:**
> Just one question, are you playing the video at the size it was encoded to? I'm still running Dapper and divx and dvd's play nice.

Thanks very much for your reply.

The resolution is automatic, that is to say, it plays at what it was encoded and looks okay, (encoded at 640 by 480 roughly), (these are the aXXo Div-x files one gets from bittorrent and the like. however of course, when I press fullscreen to sit back and enjoy the movie it extends to 1280 by 800. That's when it looks bad. Although this was not an issue in (dare I say it) Vista, they looked okay. 

Are you suggesting possibly I should lower the screen resolution to 640 by 480 so I could watch them properly?.... Even if I do, it extends the desktop to the full size of the screen (no black bars on each side of the screen).

---

### Post by amaurynieto on 2007-07-15
> **Mr_bleu said:**
> Have you tried System>Preferences>Removable Drives and Media>?
Just curious.  My e1505 has no problems with the Ricoh Driver.  

Run lspci -v  and post the results here.

Here's what I get. It seems it doesn't mount anything

08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Dell Unknown device 01f5
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at c0302800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:01.1 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: Dell Unknown device 01f5
        Flags: bus master, medium devsel, latency 0, IRQ 9
        Memory at c0302c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by Kilz on 2007-07-15
> **amaurynieto said:**
> Thanks very much for your reply.

The resolution is automatic, that is to say, it plays at what it was encoded and looks okay, (encoded at 640 by 480 roughly), (these are the aXXo Div-x files one gets from bittorrent and the like. however of course, when I press fullscreen to sit back and enjoy the movie it extends to 1280 by 800. That's when it looks bad. Although this was not an issue in (dare I say it) Vista, they looked okay. 

Are you suggesting possibly I should lower the screen resolution to 640 by 480 so I could watch them properly?.... Even if I do, it extends the desktop to the full size of the screen (no black bars on each side of the screen).

Im not 100% sure what would be better, lowering the screen res to watch it full size would work (I suspect Vista dose this automatically for you) because when you view a low resolution video at high res it stretches it. Thats going to make it look bad..

---

### Post by redDEADresolve on 2007-07-16
use the 32 bit version of feisty. if your only reason to run the 64 bit version is because you have a 64 bit processor you're only hurting yourself. the 32 bit version works flawlessly with the ricoh card reader. i just used it 4 minutes ago

redDEADresolve
[www.ubuntu1501.blogspot.com](www.ubuntu1501.blogspot.com)

---

### Post by dmfield on 2007-07-16
Nothing wrong with the card reader on My dell 1501 running x86_64 Ubuntu 7.04, infact, its the only 64bit distro i CAN get it working with..

Please don't uninstall the 64bit version of any distro.. for the 32bit because its "Easier" numbers count, and if more people are using the 64bit versions, then the bugs will iron out, and the software will start to be produced..

Why did you buy a PC with 64bit architecture, if not to run 64bit apps? When i get home, i'll post some more info on what versions of everything i'm running, but it does work, as i ported over a lot of MP3 to listen to on this morings tube run.

Maybe its the size of the Card? I seem to remember over a GB used to faulter..

---

### Post by amaurynieto on 2007-07-22
It works now, for some ODD reason, only with SD cards (not MMC). I have a 128 MMC which won't be read (but will read in Windows), and the SD cards I have are recognized without a hitch.

Anyone have any hints?

---

### Post by cobalaminco on 2007-10-22
> **amaurynieto said:**
> 
That, and the fact that DIVX videos play HORRIBLY on my 1280*800 display. I'm guessing it's the ATI driver (fglrx) for an Xpress 1150 (x200 chipset). It's all pixelated and looks like dog food (mind you, it's watchable, but nowhere near Nvidia's output).

Anyone have any feedback which might help me resolve the problem?

Thanks! A.

hey!

did you get a way to watch the divx well? i'm having the same problem as you, if you get the solution let me know please! :)

thanks!

---

