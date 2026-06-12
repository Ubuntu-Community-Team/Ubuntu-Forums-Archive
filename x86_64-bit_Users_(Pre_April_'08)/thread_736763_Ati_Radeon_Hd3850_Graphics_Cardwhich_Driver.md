---
title: "Ati Radeon Hd3850 Graphics Card/which Driver"
date: 2008-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by MeTylerDurden on 2008-03-26
My new Graphics caard uses the Vesa Generic one that must have been the default one that installed with Ubuntu 7.10    I would like to get better one so my tv out will work   and improve overall..    

Man, I see in fight club the strongest and smartest men who've ever lived. I see all this potential, and I see squandering. God dxxn it, an entire generation pumping gas, waiting tables; slaves with white collars. Advertising has us chasing cars and clothes, working jobs we hate so we can buy shxx we don't need. We're the middle children of history, man. No purpose or place. We have no Great War. No Great Depression. Our Great War's a spiritual war... our Great Depression is our lives. We've all been raised on television to believe that one day we'd all be millionaires, and movie gods, and rock stars. But we won't. And we're slowly learning that fact. And we're very, very pissed off. :popcorn:

---

### Post by Yellow Pasque on 2008-03-27
The open-source drivers (radeonHD and ati/radeon) don't support TV-out on your video card yet. Neither does the Ubuntu version of fglrx.

Your lone option is to use the latest proprietary Catalyst driver (8-3).
Driver download: [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)
Install guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by MeTylerDurden on 2008-03-27
Hestitant to install anything , but i did install from this Ubuntu Gutsy Installation Guide:sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
 That is method one for installing driver from this link 
Catalyst Install Guide: Click Here        I dont know if this did anything .. and i was not sure if i was to proceed..   seems that alot of the HD3850 users are solid pros.. i am a beginner


Fuxx off with your sofa units and string green stripe patterns, I say never be complete, I say stop being perfect, I say lets... lets evolve, let the chips fall where they may. 
:popcorn:

---

### Post by MeTylerDurden on 2008-03-27
I may just leave well enough alone.. the only issue right now is if the svideo tv out works , ,, and who knows maybe it is..  i am just going to cut off my hands and walk away !

Do you hear me now?
Tyler Durden: No I didn't quite catch that Lou.
[Lou hits Tyler again]
Tyler Durden: Still not getting it.
[Lou hits Tyler a few more times]
Tyler Durden: Ok, I got it. Sxxt I lost it.
[Lou continues to beat up Tyler] 
:popcorn:

---

### Post by Yellow Pasque on 2008-03-27
> the only issue right now is if the svideo tv out works

Have you tried it? (And no, I don't need Fight Club quotes attached to the reply. Trust me, objective reality really does exist. I've drank over 1,000 bottles of cough syrup and lived my life based on isolation and fear, so I know what you're going through. Log off whatever little world you've created for yourself and come back. It's not as bad as you think :) )

---

### Post by MeTylerDurden on 2008-03-27
Installation

For most users it won't be necessary to go into installation and configuration details of the driver. Ubuntu 7.10 (Gutsy) provides a notification saying that there are restricted drivers available. You just have to go there (Restricted Drivers Manager) and enable the "ATI accelerated graphics driver". Ubuntu will then install and configure the driver for you. If this does not provide the optimal solution you were looking for, please read ahead.
[edit] Method 1: Install the Driver the Ubuntu Way

This will install the driver that is currently in the repositories. It may be older than the current version from AMD.

sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

The second line of the above may not be necessary. If apt says it cannot find the "linux-restricted-modules" package, try line 3. If that fails, check your sources.list (see top of page)

If the system complains about dependencies, use your preferred package manager to download python2.4 and, if necessary, its dependencies.
THIS IS AS FAR AS I WENT AS THERE WAS NOTHING SAYING TO 'PROCEED"      RESTRICTED DRIVERS MANGER SAYS I DONT NEED RESTRICTE D  DRIVERS... 

  People do it everyday, they talk to themselves... they see themselves as they'd like to be, they don't have the courage you have, to just run with it:popcorn:

---

### Post by MeTylerDurden on 2008-03-27
sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a



 Thats what i entered in terminal. :)

---

### Post by MeTylerDurden on 2008-03-27
please give me a moment to try tv out.. thanks

---

### Post by MeTylerDurden on 2008-03-27
Ok,  i plugged svideo to rca adapter into pc then plugged rca into tv in on tv. then put channel of tv to AUX  .    that should do the trick/ 
    I put on a video from hulu and nothing played on the tv  i am not sure if the grapphics card is supposed to auto detect that you plugged into svideo (tv out)   or not.   i cannot find anything in my forum search on that...                            :popcorn:

---

### Post by MeTylerDurden on 2008-03-27
after some more searching  i found this and entered into terminal  sudo apt-get install xorg-driver-fglrx

---

### Post by MeTylerDurden on 2008-03-27
ok that driver installed and restarted pc.  says i am still using vesa driver .. i give up .. surrender .   i quit...

---

### Post by MeTylerDurden on 2008-03-27
In a last response I would have to say  that ATI  has no customer service and is not the place to go for answers.. So purchase a video card that you know is compatible.   ATI OR MSI  JUST LEAVE THEM BE..       they just lack good customer service period. :popcorn::popcorn::popcorn:

---

### Post by soxs on 2008-03-28
I am using an Phenom and a ATI HD 3870 and the normal driver is doing well... the one from the repositories i mean, but I did not test any *special* futures

---

### Post by Yellow Pasque on 2008-03-28
> **soxs said:**
> I am using an Phenom and a ATI HD 3870 and the normal driver is doing well... the one from the repositories i mean, but I did not test any *special* futures
You're also using Ubuntu 8.04...

---

### Post by MeTylerDurden on 2008-03-28
Well the HD 3850 comes with  2 DVI out ports and one SVideo .   I could get the svideo to work if i unplugged my monitor and plugged in my tv to svideo  and restarted pc.    Though the pic on tv was impossible to view becuase of the line that flickered across it..   
   I wish i woulda known about alt + print screen   hold down and slowly press  r s e i u b  to initiate restart..       well for 170 plus shipping  i would like to use my card with all the capabilities ,  i coulda just got a 50 dollar card for what i get.   :popcorn:


That's right; one can make all kinds of explosives using simple household items...

: If one were so inclined.

---

