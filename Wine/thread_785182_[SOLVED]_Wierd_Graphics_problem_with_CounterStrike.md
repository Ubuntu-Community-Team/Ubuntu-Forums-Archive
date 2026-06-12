---
title: "[SOLVED] Wierd Graphics problem with CounterStrike source after installing under Wine"
date: 2008-05-07
forum: Wine
---

### Post by AFarris01 on 2008-05-07
Ive been reading all over about how people have been getting Counterstrike source to work through their Wine installations, and since that game is the main reason why i still even use windows, i recently decided to give installing it a try.  

Everything seemed to go smoothly as far as installing and such went, but whenever i launch a game, i have a few problems that make it unplayable for me...but before ill get the 'essentials' out of the way:

OS: Ubuntu 8.04 'Hardy Heron' x86
Wine: 0.9.61
Game: CounterStrike Source (downloaded through Steam interface)

now for the 'fun' stuff.  whenever i launch the program, everything loads just fine, but when i actually get into the game, the graphics are horridly distorted... the player model is really badly stretched and distortedand i cant play the game

i looked around a bit and saw that some people had complained about the HDR option causing them problems, so i disabled it in the video panel before launching a game...but it didnt really change a lot.  it id remove a bit of the distortion, but the models are still badly distorted.  i would upload screenshots of the issues in action, but the picture upload tool wont let me.

anybody have any ideas as to what might be causing this, or what else i might be able to do to get it to work properly?

heres the command im currently using to launch CSS:

env WINEPREFIX="/home/andrew/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 240 -dxlevel 90

(i also tried -dxlevel 80 & -dxlevel 70 but these did not yield any different results than posted above)

i greatly appreciate any help/suggestions that anybody has!

SC
Andrew

---

### Post by Brynster on 2008-05-07
what video card are you using?

If its ATI based then you need to make sure the driver is 100% correct and upto date. However i don't have the skill to advise how to make sure its right.

I would search Google for Envy install script, works brilliantl for Nvidia and ATI.

---

### Post by AFarris01 on 2008-05-07
Thanks for the reply....

My graphics card is an Radeon HD 2600XT, and i was just using the binary driver from the ubuntu repositories on here.  ill give envy another try and see if that helps...either way ill post back!

---

### Post by AFarris01 on 2008-05-07
i let envy install the newest graphics card drivers, and i still have the same problem.

also, i tried to join a game my friend had running to see if it was just my char, or all char models that were distorted, and whenever i tried to join, it loaded up like normal, then when the game should have come up, crashed to wine desktop...is that related?

---

### Post by Brynster on 2008-05-09
it possibly could be related,

Could you post a screen shot so we can see what the distortion is please. Maybe that will give me or somebody else more of an idea whats happening under the hood.

---

### Post by AFarris01 on 2008-05-09
Sure thing, Ive got a screenshot from it the other day that i tried to uplaod, but it wouldnt take it before... worked fine this time though, so here it is, hope its helpful.

---

### Post by AFarris01 on 2008-05-13
so...any ideas anybody?

also, i just updated to Wine 1.0-rc1 and the graphics issue has been slightly improved, but now after i run CSS for more than about 15 seconds, it freezes/crashed back to wine desktop.  heres a screenshot of what it's doing still.  ive also included a screenshot of a bot in view to show how the graphic issues is affectinhg other player models too.

---

### Post by Inevitab13 on 2008-05-14
Kudos for actually getting it working. Mine won't even get past the loading screen with the 2 CT's and the Black loading box. And I'm using a 2600 Pro

---

### Post by AFarris01 on 2008-05-18
Inevitab13-
does it freeze or something at that screen?  ive seen a bunch of people saying they had that same problem, or at least a similar one.

---

### Post by AFarris01 on 2008-05-18
I dont know if this would be helpful in diagnosing this problem or not, but i cannot get any of my other valve/Sierra games to install either.  ive tried CS 1.0 retail, Half-life, Blue Shift, Empire Earth etc... none will install.  theyre all hanging in the installer except for Empire Earth, which installs, but then freezes when i try to run it. Im going to try installing HL2 through steam in a little while and see if that works, but i highly doubt it.

---

### Post by AFarris01 on 2008-05-21
HURRAH!!  i just fixed it.  heres what i did...

changed launcher to this:
env WINEPREFIX="/home/andrew/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 240 -dxlevel 90 -console

disabled pixel shader support (Configure Wine > Graphics > Uncheck "Allow Pixel shader support")

set sound output to OSS

now everything works perfectly.  no freezing, no odd graphics issues.  the only thing ive noticed is that on objects that would normally be being hit by a lot of sunlight are now abnormally white, but its not a big deal.  yey! me happy!

---

