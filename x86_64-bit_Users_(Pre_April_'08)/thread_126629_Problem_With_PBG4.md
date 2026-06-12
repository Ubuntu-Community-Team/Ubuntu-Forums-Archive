---
title: "Problem With PBG4"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by xQuick on 2006-02-07
I am new to linux so pardon any faux pas... 

I am trying to install off a disk that I burned with Toast as an ISO first and it just wouldn't boot from that so I'm just using my original .dmg burn using Tiger. I make it to the part where I get to input install and what not (far... I know) I've tried a few combitnations of everything. What I think I might be doing incorrectly is not putting it on the right partition and I don't know how to go about doing that. Anywho, my problem is that the screen goes white after after the ramdisk the next thing after loading the kernel (even when trying to use video=ofonly) and goes back to a black screen where it runs down a list of things i've found to be similar to things already on the internet however mine ends at arch_setup: Enter. Sometimes there are red little artifacts on my screen and sometimes it just says 'e'. I have 768 ram, don't know if that's important. and the partition i wish to put ubuntu on it well uh, "Ubuntu" =)

(update)
What my screen stays at after the white screen flash

Welcome to Linux, Kernel 2.6.12-9powerpc

Linked at : 0xc0000000
frame buffer at : 0xa0000000 (phys), 0xd0000000 (log)
klimit : 0xc0324004
MSR  : 0xc00003030
HIDO : 0x841c0bc

pmac_init(): exit
id mach(): done
mmu:enter
mmu:hw init
hash: enter
hash: fine peice
hash: patch
hash: done
mmu:mmpir
mmu:setio
mmu:exit

setup_arch: enter

///////

sometimes "enter" reads as "Enter" "E" or "e" and I tend to get different artifacts everytime but only a varioation of 3. red lines under enter and to the left,, one small blue/green mess to the right or one blue/green mess under enter...

---

### Post by koni2005 on 2006-02-07
The problem definetly is not the partition, as the installer will later ask you to partition the disk...

Check out these threads:

[http://ubuntuforums.org/showthread.php?t=126115](http://ubuntuforums.org/showthread.php?t=126115)
[http://ubuntuforums.org/showthread.php?t=110226](http://ubuntuforums.org/showthread.php?t=110226)
[http://ubuntuforums.org/showthread.php?t=122516](http://ubuntuforums.org/showthread.php?t=122516)

---

### Post by xQuick on 2006-02-07
Thanks koni but as much as I have very similar problems with those people linked I can't resolve me issue. I can't use ctrl-op-f1 (even when trying to use function) and if i try to run dpkg ect... in terminal it says that is an invalid command. :cry:

---

