---
title: "Cannot install x64 or run it Live"
date: 2009-08-27
forum: x86 64-bit Users
---

### Post by Paradoxx611 on 2009-08-27
[COLOR=Red]_This problem was resolved!  See post #9 for the resolution_[/COLOR]

Hello all,
  I am having a bit of a debacle here.  I recently just upgraded my memory from 2g to 4g of corsair ddr2 800mhz memory.  I orriginally had 32 bit Vista Ult on my machine, but couldnt utilize my memory fully, so I decided to wipe my system clean and install a fresh new Win 7 x64.  It failed.  I end up downloading the newest release of Ubuntu x64 desktop.  Tried installing it which ended up failing as well.  I am perplexed here.   
 
**Here is what my system is:**
 
Mobo - Intel DG965WH socket LGA 775
Proc - Core2 Quad Q6600
Memory - 4g DDR2 Corsair 800mhz
Gfx card - Nvidia Gforce 9600GT
HD - 250g SATA drive wiped using DBAN 
 
My system should most definitly be x64 compatible. 
 
 
**Here is what I have tried so far:**
 
-Ran hardware diagnostics on all hardware using my Hirens disk which includes Memtest86 for memory, PCcheck for mobo and proc functionality, and a HD surface scan utility.  All came back perfectly functional and no errors!
 
-Updated my Bios
 
-Tried installing both OS' using different opticle drives
 
-Disconnected my HD from my system and ran Ubuntu Live but froze in the same spot as it did when I was trying to install it.
 
-Used the Ubuntu Install Disc check,  the installer disc had no errors.
 
 
 
Both OS' kept failing in the same place when trying to install or run it Live.
**Here is the kicker, Both 32 bit windows and 32 bit ubuntu install perfectly fine on my system still.**
 
 
I honestly dont know where to turn from here, any insight?

---

### Post by Paradoxx611 on 2009-08-27
scratch that, I am now not able to install or run ubuntu live 32 bit.
 
Getting:
 
init: rc-default main process (2983) terminated with status 127
 
and it stops

---

### Post by fatbotgw on 2009-08-28
Try taking out the new RAM sticks and try the install.  If it installs then great and then add the new RAM.

---

### Post by Paradoxx611 on 2009-08-28
Replaced it the corsair memory with my original memory.  Still having the same issue =(

---

### Post by fatbotgw on 2009-08-28
What version (9.04?) are you trying?  Have you tried another version?

From what I've found, your error message means it can't find something it's looking for.

---

### Post by Thelasko on 2009-08-29
> **Paradoxx611 said:**
> Replaced it the corsair memory with my original memory.  Still having the same issue =(

Did you burn your Ubuntu disk with the old RAM installed?

---

### Post by katon on 2009-08-30
> **Paradoxx611 said:**
> Hello all,
  I am having a bit of a debacle here.  I recently just upgraded my memory from 2g to 4g of corsair ddr2 800mhz memory.  I orriginally had 32 bit Vista Ult on my machine, but couldnt utilize my memory fully, so I decided to wipe my system clean and install a fresh new Win 7 x64.  It failed.  I end up downloading the newest release of Ubuntu x64 desktop.  Tried installing it which ended up failing as well.  I am perplexed here.   
 
**Here is what my system is:**
 
Mobo - Intel DG965WH socket LGA 775
Proc - Core2 Quad Q6600
Memory - 4g DDR2 Corsair 800mhz
Gfx card - Nvidia Gforce 9600GT
HD - 250g SATA drive wiped using DBAN 
 
My system should most definitly be x64 compatible. 
 
 
**Here is what I have tried so far:**
 
-Ran hardware diagnostics on all hardware using my Hirens disk which includes Memtest86 for memory, PCcheck for mobo and proc functionality, and a HD surface scan utility.  All came back perfectly functional and no errors!
 
-Updated my Bios
 
-Tried installing both OS' using different opticle drives
 
-Disconnected my HD from my system and ran Ubuntu Live but froze in the same spot as it did when I was trying to install it.
 
-Used the Ubuntu Install Disc check,  the installer disc had no errors.
 
 
 
Both OS' kept failing in the same place when trying to install or run it Live.
**Here is the kicker, Both 32 bit windows and 32 bit ubuntu install perfectly fine on my system still.**
 
 
I honestly dont know where to turn from here, any insight?

ICANT BELIEVE IT i have the same same same problem . ALMOST the same configuration like you.
My intel Board is dp43tf and the memories are regular memories.
WHat can we do???
i made the same things you said.

---

### Post by tgeer43 on 2009-08-30
Well, this error:
```
init: rc-default main process (XXXX) terminated with status 127
```is usually corrected by copying the file 'telinit' from /sbin on a live CD to that same folder on your new installation.
But if you can't even run from the Live CD then I don't know what to tell you.

tgeer

---

### Post by Paradoxx611 on 2009-08-31
Well I fixed the issue.  It turns out my system board was going bad even though it had passed all of the diagnostics I had ran.


**How I found my system board was going bad:**

-When running my Hirens boot cd, I noticed not all of the components were being loaded correctly.  And would fail to be loaded even when i attempted to manually load them.  I know it was not the memory, because I was running it with some "Known to work" memory.  

-This limited it to the processor or mobo.

-Lukily I had a spare socket lga775 proc and mobo lying around, so I threw those into my system.  Hirens loaded everything like it should.

_**I would not encourage anyone to do the below unless you are willing to risk damaging your equipment.**_

-What I did next was swap the processors to find which(if not both) was bad.

-It turned out my core2Quad functioned properly with the spare mobo, but the spare processor  was having the same issue when i put it on my original board.

[B]Process of elimination dictates it was my Mobo.

  Bought a new board, swapped it out, 9.04 64bit runs nicely now =)[/B]

Katon,  
  I hope this helps you out as well.

---

### Post by Paradoxx611 on 2009-08-31
> **Thelasko said:**
> Did you burn your Ubuntu disk with the old RAM installed?

I had burned the disk with a completely different computer =/

---

