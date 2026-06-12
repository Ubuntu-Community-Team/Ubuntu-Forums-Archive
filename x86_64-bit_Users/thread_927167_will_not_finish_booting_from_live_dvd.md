---
title: "will not finish booting from live dvd"
date: 2008-09-22
forum: x86 64-bit Users
---

### Post by papaw on 2008-09-22
i downloaded ultimate edition v-1.9-x64. i am running a x64 bit system.the kerenel is 2.6.24-21-generic. i have also edited the kernel and changed it to. did the no quiet splash several ways. also edited my cards in nano, shows they are loaded and working.i have vista ultimate and Linux Mint Elyssa 5 on a dual boot(with a swap file). when i boot from my dvd, it loads the screen and i can click on run or install and it starts to load. when the loading bar gets full it disappears and my screen stays on but stays where it is.i have left it like this for about 45 minutes, still nothing. i have also tried to load in safe mode and text. same thing happens. i had this same problem with PCLinux OS and Linux Mint,but i was able to load them in safe mode and they worked.i had a friend bring his dvd that he downloaded and the same thing happens.i burned the DVD with K3B and it checks the MD5 sum, the numbers matched.I also burned it at x4 speed, like to burn things slow. i burned the os to a memorex DVD-+R disk.ive tried the ultimate forums bot nothng there has helped. looks like a nice system would love to try it.any help will be appreciated. below will be the system i am running hope it helps.be nice to have a log but there is not one for this i think.system is about six weeks old,built it myself.

thank you,
pawpaw

Motherboard: Asus M2N-SLI
Processor: AMD Phenom X4 9500 Quad 2.21GHz
Memory: 4x 1GB Samsung DDR2 800 MGh
Drive: WD 1600 JS Caviar SE 160 GB 7200rpm- SATA connection
DVD Burners: Sony DRU-840A- set as master-IDE connection
Lite-On- SATA connection
Grapic Cards: 2x PNY Verto GeForce 8500 GT (SLI configured)
Cooling Fan: Kingwin Gladiator Hybrid Liquid Cooling(the liquid is anti-freeze lol)

reason the live dvd wouldnt finish loading was it wasnt picking up my sli configured video cards. i got a friend to load ultimate x64 on one of his ide hard drive and bring it over. we booted the dvd and went into recovery mode loaded my nvidia drivers by running envyng -t in text mode.it loaded my video drives and i was able to boot into ultimate.he then took my sata hard drive home and loaded it with ultimate, brought it back. we booted it in safe mode ran envyng -t again and it loaded my video cards.then it booted into ultimate.it was not picking my video cards up.bford16 thanks for the help,if you come across this again you can tell them what i did. pain in the but unless you have an extra computer laying around. i had just given my old one to my friend.

---

### Post by bford16 on 2008-09-23
There is a known issue with Ubuntu (kernel 2.6.24-) and SATA devices.  Try booting the DVD with the "pci=nomsi" option.

---

### Post by papaw on 2008-09-26
hope you see this bford16

---

