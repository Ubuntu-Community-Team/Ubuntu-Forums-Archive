---
title: "LAN and Audio Card Not Detected"
date: 2007-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by jmznorton on 2007-01-26
I just installed Ubuntu 6.10 64-bit onto a newly built system.  By default all of the hardware and ports seem to have been detected just fine except for the built in LAN and built in Audio Card, both components are manufactured by Realtek.

I have been to both the website of the Motherboard and the Realtek website and see only Windows versions of their drivers.  This is my first time attempting to install Linux on any machine and so I am somewhat new at this.  Does anyone have any suggestions on how to get the OS to recognize these?  Here are the specifics:

Mainboard: MSI K9N6SGM-V Socket AM2 NVIDIA GeForce 6100 Micro ATX AMD
Built in LAN: Realtek 8201CL
Built in Audio: RealTek ALC883
Processor:  AMD Athlon 64 X2 3800+ Windsor 2.0GHz 2 x 512KB L2 Cache Socket AM2
RAM:  pqi 1GB 240-Pin DDR2 SDRAM DDR2 667 (PC2 5400)

thanks for whatever suggestions or help you can offer.

James

---

### Post by sizzlor on 2007-01-27
oh yeah..  that sounds real familiar.  
i have a very similar setup (GeForce 6100 chipset), and i had the exact same problem. 

there is a solution, however: **upgrade to a 2.6.20 kernel**. 
since i'm no kernel wizard, i simply decided to **[upgrade my system to Feisty]("http://ubuntuforums.org/showthread.php?t=305870")** (Ubuntu 7.04), which comes with Linux kernel 2.6.20-5.   

i know it *sounds* 'risky', but now everything works -- no fuss, no muss.   and Feisty will become the official release in a few months anyway, so you get to experience the bleeding edge while enjoying full 5.1 sound..  ;)

---

### Post by FloSynergy on 2007-06-19
hey, folks,

sounds like your issue is very similar to mine. I have posted more detail [here]("http://ubuntuforums.org/showthread.php?t=478163").

Any suggestions on how to upgrade the kernel - in south africa, it's a mission to download the entire 7.04 distro.

thanks,

flo

---

### Post by dannyboy79 on 2007-06-19
> **FloSynergy said:**
> hey, folks,

sounds like your issue is very similar to mine. I have posted more detail [here]("http://ubuntuforums.org/showthread.php?t=478163").

Any suggestions on how to upgrade the kernel - in south africa, it's a mission to download the entire 7.04 distro.

thanks,

flo
i beleive if you enable the backport repository in synaptic package manager, then reload, you should see the new kernel. the backport repo is basically packages that are for a later release than what you have but they have been built for the previous package, the backport repo is not guranteed to work however just a warning. do a google search on ubuntu backport repository and read about it.

---

### Post by FloSynergy on 2007-06-19
hey dannyboy,

thanks for your suggestion, i'll read up about it and give it a try asap.

be well,

flo

---

### Post by FloSynergy on 2007-06-20
hey again,

just checked out synaptic - the backports are not available off the install cd - i can only get hold of these on the net via synaptic, as far as i can tell...so this seems like a catch-22: can't get online cause the kernel doesn't recognise the chips, can't get a new kernel cause i can't get online?

:(

so what now...?

thanks for the suggestions, and i'll keep sleuthing.

be well,

flo

---

### Post by FloSynergy on 2007-06-20
ok folks,

bingo!!!

it seems that the only solution was to download a fresh iso-image and run the install cd of 7.04. the newer kernel recognised everything first-time around, and seems to be running smoothly and speedily.

yippee!

be well,

flo

---

