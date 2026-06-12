---
title: "Beige G3 won't go live"
date: 2005-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by ristosu on 2005-11-07
I managed to boot the live-CD using BootX (the hard disk contains just OS 9). It seems to get up to Detect hardware correctly, but stops in Configure timezone, in Ubuntu installer main menu. There is no option for getting further.

So, I wonder, is this correct behaviour, to get into the installer in the first place? And why is this timezone setting so vital, that it can't go on without it?

---

### Post by jessecurry on 2005-11-08
have you placed a kernel argument in BootX? I believe that from the liveCD you need to add 

"casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop --"

Not sure if this is the same for the new string, but you should be able to look at yaboot.conf and find what is appended.

---

### Post by ristosu on 2005-11-08
That did it. Thank you!

---

### Post by spencer on 2005-11-30
Hi, I have an old Power Mac G3 tower with B/W 350 Mhz processor in it, overclocked at 375 Mhz 85 Mhz Bus. I'm having the same trouble here with getting the live ubuntu CD running. I have os 9 and BootX installed, when I reboot the BootX panel displays and I choose linux. Nothing happens, it just stays frozen with the mac os smiley face displayed. I put in the recommended kernel arguement too. Anything else I missed? Thanks!

-spencer

---

### Post by spencer on 2005-12-03
Hi, Nothing I've tried has worked to get the live Ubuntu cd to boot. The closest I've come to booting it was using the following options:

1.  vmlinux is in the kernels folder
2.  bootx is in the control panels
3.  I used the kernel argument "casper/enable=true              casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop --" that jessecurry recommended. 
4.  /dev/hda11 is the root device.

I get this far before computer hangs with the following message:

"version  :5
compatible version :s10
architecture :0x00000001
Wating a little bit so you can read all that stuff...
Entering PPC Supervisor..."

What does that mean? What else can I try? And, has anyone else been able to run the Ubuntu live cd? Thanks!

-spencer

---

### Post by spencer on 2005-12-06
Hi, Well, I've finally came to the conclusion that Ubuntu on Beige G3 is not the best option. It is just too difficult, I tried all methods recommended on who know how many websites. And even if I did figure out how to do it, I wouldn't be happy with it running on the beige G3. It's just not enough oomph! So I'm typing this running from the live cd using a G4 and know will install and work properly using it. I will install Ubuntu on it  soon. I'll have some questions I'm sure, until then thanks Ubuntu team for the Great work!

-spencer

---

### Post by cilynx on 2005-12-06
If the G3 is yours to play with, you might want to go ahead and do a real install.  The live CD has much higher system requirements (mostly RAM) than does a real install.  I have installed a perfectly usable setup of Ubuntu on a first-generation tray-load iMac.  Said iMac won't even consider running the live CD.  It tells me right off the bat that it doesn't have the system resources to do it.

---

### Post by ristosu on 2005-12-09
Can you see that BootX has found your kernel? Did you copy the initrd.gz to MacOS and select it in BootX Options? Probably not, because then you can't set the root device (which is not needed). The third thing is the kernel argument for casper. That should be all. For me BootX has never failed :)

I ran the live cd in my beige G3/233 with 192 MB of RAM. It was slow, but usable. Now I have installed Warty on hard disk, runs quite smoothly, but no sound yet...

---

### Post by spencer on 2005-12-09
I just finished installing Ubuntu Breezy on a Mac G4 last night and haven't gotten around to the G3 yet. I'm still playing with breezy on the mac. I'll get back to the G3 in a few days and report the details. Thanks!

-spencer

---

### Post by spencer on 2006-02-17
Hi,

Well, after sometime I finally had some time to try again. This time I was successful at booting Ubuntu 5.04 Hoary live disk. It worked; a little slow to boot but eventually made it to desktop. Now If I could just install Ubuntu to disk..., but the directions to boot live disk don't work for installing onto disk. Thanks!

-spencer

---

