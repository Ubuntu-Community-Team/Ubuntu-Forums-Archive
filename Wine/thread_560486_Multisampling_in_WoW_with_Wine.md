---
title: "Multisampling in WoW with Wine"
date: 2007-09-26
forum: Wine
---

### Post by Demrien on 2007-09-26
Hi im using Ubuntu to play World of Warcraft with Wine for a month now an everything is fine except im having some performance problems.
I read most of the guides in these forums about how to improve wine (registry tweak and so on).
The Problem is that in some areas of the game I have only 5-10 fps with every option on minimum while in windows  I have something around 30+ with everything in highest possible. The only possible reason I found is that while running wow in Linux I cant change the multisampling. Instead of diplaying the colour depth ans the sampling rateit just shows "56hz" without aditional options. 
Its pretty obvious that this isnt the right setting.
Im running Ubuntu Feisty Fawn with the latest wine and the also the latest ATI Drivers.
My System is a Pentium 4 3.2Ghz
1GB RAM
ATI Radeon X700XL

I searched through the forums but i couldnt find someone with the same problem.

---

### Post by hikaricore on 2007-09-26
I find it hard to belive that you couldn't find ANYONE who's having trouble with WoW on an ATI card..

The inability to change many things in the video options with WoW in OpenGL mode is well known, and this issue has existed as long as WoW has be able to run /w WINE on Linux.
ATI cards getting bad framerates in WoW is also well known and mentioned in hundreds of threads in this very forum.  The ATI drivers which have been a menace for a long time ARE getting better, but it's still going to be awhile before they match up to their ***dows counterpart.  There are several tips for improving ATI performance here: [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

You have three choices when it comes to editing video settings.
Do it manually, change them in D3D mode, or get this addon: [http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html) (which will allow you to change many settings in the video configuation window)

Also in my personal experience changing the multisampling rate doesn't work quite right (even under ***dows) and it reverts back the next time you start the game anyway.

---

### Post by Demrien on 2007-09-26
Well of course i could find som threads about what you mentioned.
I did know most of the things you said but what i wanted to know is if there is a way to magically mage it possible to have more multisampling options or just a real one. I do know that the ATI drivers in Linux pretty muh sucks but i cant belive that the difference between those drivers is that big, i mean its like it is only using 10% of its capacitys. Besides i did try running it in d3d mode. It doesnt improve much becaus i can only choose 1xmultisampling while in windows it is up to 6x. furthermore i did try a nvidia card with even more power and i couldnt find a difference. Besides a lot of people with worse system are running it in wine without any problems oder difference to Windows. So they must have done something I didnt and therefor my question is what it could be.

---

