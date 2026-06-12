---
title: "problems running half life 2 under wine in ubuntu 7.10"
date: 2008-01-09
forum: Wine
---

### Post by luke9511 on 2008-01-09
hello everyone hope your all well, i just installed ubuntu on my desktop after a bad virus attack on windows and im wanting to try and get some of my games running in linux, so i chose half life 2, well i got steam installed and working fine and i installed half life 2 no problems, but when i go to start half life 2 it gets to the loading screen for the main menu and then the screen turns black and i cant see or do nothing only way out is to alt+tab out and close it, was wondering if anyone knew of anything i can do to fix this? fyi compuiz is off

---

### Post by aoanla on 2008-01-09
> **luke9511 said:**
> hello everyone hope your all well, i just installed ubuntu on my desktop after a bad virus attack on windows and im wanting to try and get some of my games running in linux, so i chose half life 2, well i got steam installed and working fine and i installed half life 2 no problems, but when i go to start half life 2 it gets to the loading screen for the main menu and then the screen turns black and i cant see or do nothing only way out is to alt+tab out and close it, was wondering if anyone knew of anything i can do to fix this? fyi compuiz is off

You're going to need to give us more information, probably.
What version of Wine did you install, for a start, and what graphics card and drivers you're using.

---

### Post by luke9511 on 2008-01-09
latest wine on a ATI Radeon X1600 512mb video card 2 gigs of ram and a 2.2ghz cpu not sure of the drivers im using the restricted drivers if that means anything

---

### Post by mojoo on 2008-01-09
i have exactly the same problem with hl2 and css
as soon as i start the application from steam they show the loading screen and lock up or drop back to steam.
i searched a lot for an answere to this the last weeks but wasnt able to find a solution.
But i found out that this issue seams to occure often.
Some people said that disabling the steam ingame message service solved thier probs but not for me .
although i have no real prove for this, i think this problem is related to ati cards and the direct3d system of wine.

---

### Post by luke9511 on 2008-01-09
> **mojoo said:**
> i have exactly the same problem with hl2 and css
as soon as i start the application from steam they show the loading screen and lock up or drop back to steam.
i searched a lot for an answere to this the last weeks but wasnt able to find a solution.
But i found out that this issue seams to occure often.
Some people said that disabling the steam ingame message service solved thier probs but not for me .
although i have no real prove for this, i think this problem is related to ati cards and the direct3d system of wine.in the launch options for half life 2 put this >  -novid -dxlevel 70 -width 1024 -height 768thats how i got it working though i gameplay is choppy and stuff, i still need to know if i should install my video card drivers or if the restricted drivers are fine?

---

### Post by mojoo on 2008-01-10
i tried all the parameters out there -novid heapsize -nosound and so on nothing works

---

### Post by aoanla on 2008-01-10
Indeed, ATI card owners seem to have more issues with Wine than nVidia card owners, but many still manage to get things working after some tweaking. 

Since you just said you have the "restricted drivers" enabled, that probably means that you're using the version of the ATI fglrx drivers that comes with Ubuntu. These are somewhat older than the current cutting edge drivers - you *may* find that upgrading to the Catalyst 7.12 Linux drivers improves matters for you.
Go here:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
for more information.


(A note: versions of wine between 0.9.47 and 0.9.49 may have issues with Steam and Source-engine games. If you try different versions of Wine, don't bother with those versions - skip back to 0.9.44 or so.)

---

### Post by luke9511 on 2008-01-10
> **aoanla said:**
> Indeed, ATI card owners seem to have more issues with Wine than nVidia card owners, but many still manage to get things working after some tweaking. 

Since you just said you have the "restricted drivers" enabled, that probably means that you're using the version of the ATI fglrx drivers that comes with Ubuntu. These are somewhat older than the current cutting edge drivers - you *may* find that upgrading to the Catalyst 7.12 Linux drivers improves matters for you.
Go here:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
for more information.


(A note: versions of wine between 0.9.47 and 0.9.49 may have issues with Steam and Source-engine games. If you try different versions of Wine, don't bother with those versions - skip back to 0.9.44 or so.)thanks to your very helpful and usefull info i managed to get new drivers installed with no problems and they have gotten rid of the lag i was having in battlefield 1942 and im getting ready to try half life 2 and will edit this post when im done :) thanks alot

EDIT:half life 2 works great now, though the textures are messed up they are in rainbow colors but i will try the settings i had to try and fix it, thanks alot for the help

---

### Post by aoanla on 2008-01-10
Rainbow textures seem to be caused by issues with the shaders in DX9. 
-dxlevel 81 should work, without removing as much of the eyecandy as -dxlevel 70 would.

---

### Post by luke9511 on 2008-01-11
> **aoanla said:**
> Rainbow textures seem to be caused by issues with the shaders in DX9. 
-dxlevel 81 should work, without removing as much of the eyecandy as -dxlevel 70 would.
well i have been trying on dx80 and gotten it under that havent tryed under 81 or 70 yet though, but if i had to guess it might be there under 81 and might not be there under 70 but i will find out when i try

---

### Post by Rafadagaffer on 2008-01-11
> **luke9511 said:**
> latest wine on a ATI Radeon X1600 512mb video card 2 gigs of ram and a 2.2ghz cpu not sure of the drivers im using the restricted drivers if that means anything


I've got the same video card and the exact same problems. I was using the latest drivers from the ati website and managed to get the game working at direct x 7..

I'll be sticking to xp for gaming, gutsy for everything else.. 

You may want to try setting the memory size for your graphics card in wines registry.

Open up a terminal window, 

```
regedit
```

Navigate to HKEY_CURRENT_USER>>Software>>>WIne>>Direct3D.

Create a new string called "VideoCardMemory" and then put the amount of memory your graphics card has, 512, in the data value. 

Restart steam and then see if it works. The games would only play at DirectX7 though...

---

### Post by luke9511 on 2008-01-11
> **Rafadagaffer said:**
> I've got the same video card and the exact same problems. I was using the latest drivers from the ati website and managed to get the game working at direct x 7..

I'll be sticking to xp for gaming, gutsy for everything else.. 

You may want to try setting the memory size for your graphics card in wines registry.

Open up a terminal window, 

```
regedit
```

Navigate to HKEY_CURRENT_USER>>Software>>>WIne>>Direct3D.

Create a new string called "VideoCardMemory" and then put the amount of memory your graphics card has, 512, in the data value. 

Restart steam and then see if it works. The games would only play at DirectX7 though...already did the memory thing and the textures are still messed up on all dx levels but im not going to worry about it further, though i may try it on cedega

---

