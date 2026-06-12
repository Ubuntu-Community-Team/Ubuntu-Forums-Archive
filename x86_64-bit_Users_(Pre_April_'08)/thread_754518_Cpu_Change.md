---
title: "Cpu Change"
date: 2008-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chriis on 2008-04-13
Some advise about that,

Can i change a P4 3.2 (640) by a Core2duo (E8400) and just reboot ubuntu?
ps : i do not change the MB, juste cpu upgrade.

Some of you have did it yet?


Thanks a lot

Chriis:popcorn:

---

### Post by damvcoool on 2008-04-13
It should be just that easy. i don't see why you would have to re-install. Let us know the outcome.

---

### Post by Jouke74 on 2008-04-14
Are the mobo sockets the same?

You might need a new Kernel which supports SMP. This can be installed through synaptic though.

---

### Post by Half-Left on 2008-04-14
Nope, the generic one is smp now, you dont need to install different kernels like before.

---

### Post by Chriis on 2008-04-14
Thanks, it will be done in few hours,..i'm waiting for the cpu.

I will keep you informed

Thanks again. :)

---

### Post by jfinger on 2008-04-14
Ubuntu shouldn't care, but your BIOS might.  What I would do:  First check you motherboard manufacturer's web site to see if there's a new bios for adding support for your new CPU.  If there is, I would download that BIOS and get everything necessary to install the BIOS, like the DOS-mode installers.

Then I would swap the CPUs, without putting in the new BIOS.  If everything works, then you're done.

If it doesn't work, then flash the new BIOS into the board.

Good luck.  Let us know how it goes.

---

### Post by Chriis on 2008-04-14
It is done whitout any glitch,..

I put the new cpu on board, cooler on top, power up and after a complain from bios that the cpu was changed, I enter the bios and load default, reboot, re-enter it and set my memory timing back, save, and voila

ubuntu doesn't even ask me cd,..lol Ubuntu is wiser than the bios of my board! :-)

Thanks to all of you again.

Chriis
:guitar:

---

### Post by Half-Left on 2008-04-14
Thats the great thing about Linux, it detects all hardware on boot, you can change your motherboard and it still be ok, no need to format and worry about chipset drivers screwing it up, safe mode blah, blah.

---

### Post by Chriis on 2008-04-14
I would say "one of the several greats things about Linux ,..^^

I love linux since one year, since Ubuntu Feisty, Good Job 

Release party in few days Yeah!!! will be my second one:popcorn:

---

### Post by tgm4883 on 2008-04-14
Keep in mind that by doing what you did you didn't actually change anything on the operating system.  You are still running a 32-bit OS, just now on 64-bit hardware.

---

### Post by stchman on 2008-04-14
> **Chriis said:**
> Some advise about that,

Can i change a P4 3.2 (640) by a Core2duo (E8400) and just reboot ubuntu?
ps : i do not change the MB, juste cpu upgrade.

Some of you have did it yet?


Thanks a lot

Chriis:popcorn:

As long as the CPU fits in the socket and the mobo supports the C2D then no problem.  The C2D is an LGA775 processor, but there were many P4s that were socket 478.  Make sure your mobo is an LGA775 that supports C2D.

Make sure you use the -generic kernel (it is the default) as the -i386 kernel does not support SMP or multi cores.

---

### Post by Flying caveman on 2008-04-14
I took my hard drive out of AM2 amd64x2 6000+ system and but it in an socket 754 AMD64 3000+ system. the only thing that was the same was the hard drive and both 64bit cpu's 

It would have just booted right up but the graphics card was different too, and I had to reconfigure x.         Everything worked after that except I couldn't run the folding@home SMP client with only a single core, which I knew would happen.  Anyway,it saved me hours or days of backing-up transferring off all my pictures/movies/music.  

I love that I can do that.

---

### Post by Chriis on 2008-04-14
> **tgm4883 said:**
> Keep in mind that by doing what you did you didn't actually change anything on the operating system.  You are still running a 32-bit OS, just now on 64-bit hardware.

At all, it is a 64bits forum here.:)
 i was on 64os with my old cpu and now im still on a 64bits Os with my new one. 

P4 EM64 HT --> old
Core2duo e8400 --> new

both are 64bits cpu's

:popcorn:

Chriis

---

### Post by stchman on 2008-04-14
Beauty of Linux is that you can transfer your hdd to another mobo without reinstalling.  The drivers are in the kernel unlike Windows.

---

### Post by tgm4883 on 2008-04-14
> **Chriis said:**
> At all, it is a 64bits forum here.:)
 i was on 64os with my old cpu and now im still on a 64bits Os with my new one. 

P4 EM64 HT --> old
Core2duo e8400 --> new

both are 64bits cpu's

:popcorn:

Chriis

Ah, i stand corrected

---

