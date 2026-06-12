---
title: "Slow Encoding (I think)"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by JJ122 on 2008-04-28
OK so to start my system specs are.
AMD64 4000+ (San Deigo core)
DFI Lanparty NF4 ultra dual MOBO
3 GB of ram DDR400
Nvidia 8500GT
Kubuntu 8.04 (from 7.10)

I think it is using the x86-64 arch.  I used an AMD64 live CD so I assume it is using the x86-64 arch.

When I use programs like DVD::rip or Acidrip I get really slow encoding speeds, i.e. 20-25 FPS or about 4 hours for a 1.5 hour movie, Does this sound reasonable? When I use something like DVDShrink in Vista it seems to go much more quickly, i.e. 50-120 FPS depending on the ammount of compression.  So about 2 hours including the time to rip to the drive for it to complete.  Plus when I was using Gentoo on a computer with less memory but a better processor(1 gig and a Core duo) it would complete in 20-30 minutes.

I have KDE 3.4, KDE4, and Xfce installed but it doesn't make a difference on how fast it goes by changing the environment, which leads me to think it is something with either Kubuntu or my hardware is just slow.


So do you guys have any ideas on what might be wrong?  Or do these numbers sound ok?
If these numbers are correct I'm kinda dissapointed in Linux and 64 Bit, faster encoding was one of my main reasons for dual booting Kubuntu and Vista.  

Also is there anyway I can install programs from source(gentoo style) through adept or apptitude?

Thanks,
JJ122

---

### Post by stmiller on 2008-04-28
Programs are not going to be instantly faster unless the programming code in the application is specifically written to take advantage of 64bit.

Some programs are even a tad slower. Like LAME 3.97. It has some code (nasm) which is 32bit only, and does not work in a 64bit system. So encoding with LAME is a tad bit slower in 64bit vs. 32bit.

But some programs (like a 64bit Handbrake) are much faster in 64bit.

So the answer is: it depends.

I'd say the advantages of 64bit outweight the disadvantages at this point. Read the sticky at the top of this forum section, and wikipedia has a good article on 64bit computing.

---

