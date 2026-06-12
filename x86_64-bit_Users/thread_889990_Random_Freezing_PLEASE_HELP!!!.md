---
title: "Random Freezing PLEASE HELP!!!"
date: 2008-08-14
forum: x86 64-bit Users
---

### Post by JayRott on 2008-08-14
Ok, I have the old random freezing problem. I am running 64 bit 8.04 Hardy on an AMD Athlon 64 3000+. I have 1Gig of RAM, and I connect to the internet via a dial-up connection using Gnome ppp. I am using a conextant modem. I mostly experience this problem while using firefox. The only way I can always duplicate the problem is trying to log into myspace.com (Don't make fun.... the wife is addicted to it. I couldn't care less about myspace.) I get the total system lockout; Frozen mouse, screen, music etc.
I tried a fresh re-install.
I disabled Compiz Fusion
I didn't install the Proprietary Nvidia drivers this time around.
I removed powernowd.
I tried this method "sudo aptitude install linux-image-rt linux-restricted-modules-rt"
I even un-installed the Network Manager at someone's suggestion.

NOTHING IS WORKING! I am trying my best to avoid using windows (although I have to just to have the time to type this) Please someone help me figure this out.

---

### Post by Thelasko on 2008-08-14
Try to run an update.  If you see any kernel updates install them.  There may have been some kernel updates since you installed Ubuntu, and you missed them because you are on dialup and it takes a while for them to download.

---

### Post by Jouke74 on 2008-08-15
With random freezes the first thing you need to check is your memory. During boot hit "Esc" to get to the Grub menu if you have installed only Ubuntu. With dual boot the menu should be there already. 

Subsequently select Memtest86+ and let it run fully for about 6 to 7 times. During this test no errors should come up indicated by red, and the computer should not freeze as well! The last can be seen, because during the memtest a timer will be running. 

To quit the memtest hit "Ecs", the computer will reboot and you can select your OS again.

In case of any failure you need to exchange your memory, or take out the faulty hardware. If not Ubuntu itself is to blame.

---

### Post by JayRott on 2008-08-15
My kernel is fully up to date, but I will try the memory test.

---

### Post by JayRott on 2008-08-16
OK. I ran the memtest and through process of elimination I figured out what memory modules have been giving me errors. I removed them, and now I am down to 512mb of RAM. I still can reproduce the freezing by trying to log into myspace via the wife's account. I tried to make my own, just because I have no other ideas... no good. still freezes on me.:confused: I did some more research to figure out this problem, and all I have come up with is that this seems to be a semi-common problem and as of yet I am S.O.L. Any other possible workarounds or even information on this bug being addressed by ubuntu would ease my mind at this point.

---

### Post by elmoosecapitan on 2008-08-16
What version of flash are you running?
(If old, update and try again)

Does either your capslock or your scroll-lock lights flash? 
(If yes, possible hardware issue)
(If yes, search /var/log/*insert filename* for the word 'PANIC')

---

### Post by JayRott on 2008-08-17
I never installed flash unless it came standard, and I am not sure what those search instructions mean... I have only been using ubuntu for about a week now.

---

