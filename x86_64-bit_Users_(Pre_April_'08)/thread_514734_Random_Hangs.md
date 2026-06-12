---
title: "Random Hangs"
date: 2007-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by bwallum on 2007-08-01
Hi

I'm getting some curious behaviour. My Ubuntu AMD64 version sometimes freezes up. It appears to happen randonmly and only after some hours of use.

Has anybody else experienced this?

Regards
Bob

---

### Post by razeshkale on 2007-08-12
did you have all updates on system 
are  you using Beryl -> sometime this causes problem
are  you using Awant navigator this is also causing problem in my case
so i unistall Awant and thinking of Beryl too

so try this

---

### Post by se7en on 2007-08-12
I too am having this problem with an AMD64 processor. I'm not using Avant or Beryl. One thing I noticed is that sound continues to play and I can still move the mouse.

---

### Post by mashwebdesign on 2007-08-13
BWallum

I am using a pentium X86 system and I am having his same problem when viewing streaming videos.  It will hang right in the middle of the video and the audio loops untill i do a hard reboot.  At first i thought it was the video player itself, but it seems to do it intermittently with other various players.

But,  It has never frozen when im watching a DVD.  

I chalk it up to my video drivers.  But i could be wrong.

---

### Post by bwallum on 2007-08-13
all updated
loaded Beryl and removed it
not loaded Awant

I have found that selecting a drop down menu is the point of hanging. This has happened in Gimp and Firefox. I initially set up the system on 1MGb RAM. Subsequently I reduced this to 512Mb (noted in BIOS).

Since I have reinstalled the 1GB memory my problems have gone. 

Weird!

Regards
Bob

---

### Post by bwallum on 2007-08-13
My mouse cursor dissappears and the sound box is dead too. Just a frozen screen and no activity in the box except for the power supply fan hum.

---

### Post by bwallum on 2007-08-13
Are you using Envy?

---

### Post by mashwebdesign on 2007-08-13
Yes I am using envy for my NVidia Card in my laptop.

---

### Post by bwallum on 2007-08-14
Me too. just wondered if that was a source of the problem. I have been stable for a while now. The positive change event seemed to be putting 1GB of memory back in. I installed with 1GB then reduced it to 512MB, got a lot of hangs, then replaced the 1GB and all has been OK for the last couple of days. I have now got rid of the 512MB stick so can't test the hypothesis. Strange behaviour though, it's as though something in the system wants to keep using 1GB even though the BIOS said 512MB.

Not too sure where to go from here....

Regards
Bob

---

### Post by ljalg on 2007-08-15
I was having that issue, 7.04 randomly hanging.  I was attempting to tweak my xorg.conf file and my changes didn't take so I uninstalled the restricted nvidia driver through the restricted drivers manager, rebooted and then reinstalled it with the same tool.  I've only been playing with it for a few hours now over several days but it seems to be gone.

AMD X2
unbuntu amd64
nvidia 7300GS
1GB

I hope this helps

ljalg  O:)

---

### Post by Jouke74 on 2007-08-15
You might also want to check your memory when you boot from the Ubuntu install CD / DVD. Often it is a memory problem, or a problem with memory timings of various modules combined.

---

### Post by ljalg on 2007-08-16
Murphy's law, about 1/2 hour after posting that, it froze again.  I'm trying to check CPU temperatures and make sure it's not overheating.  air out the back seems fine but you never can tell.

Other than that I'm out of ideas, any feedback is appreciated.

ljalg  :confused:

---

### Post by maltman on 2007-08-29
I don't know if this is the same issue you're having, but I noticed some freezing on my new Feisty64 install. Brand new components too.
I think I've narrowed my issue down to the power supply. If I listen carefully, I could hear a switching noise coming from the power supply timed exactly with the freezing, and then after a few minutes it would unfreeze.
I believe it is due to a generic power supply causing my AMD64 X2 rig to be underpowered. I'm currently looking into purchasing a better power supply with much more adequate Amps on the 12Volt rail.

---

