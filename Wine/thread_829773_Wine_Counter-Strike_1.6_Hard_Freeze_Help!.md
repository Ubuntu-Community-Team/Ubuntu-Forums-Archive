---
title: "Wine Counter-Strike 1.6 Hard Freeze Help!"
date: 2008-06-15
forum: Wine
---

### Post by PrimoTurbo on 2008-06-15
I installed the latest Wine version from repos on Ubuntu 8.04, I then installed and updated Steam with no problems. I was able to launch counter-strike 1.6, edit all the in-game settings, and connect to a server. After a few minutes I would get a hard freeze, meaning I would need to restart. CTRL+ALT+BACKSPACE didn't work, nor did ALT+TAB.

I tried making my own server and connecting a few more times I get the same problem. I have noticed there are quite a few people complaining of this problem here, has ANYONE resolved it?

Thanks.

---

### Post by Sef on 2008-06-15
Moved to WINE forum.

---

### Post by n4p1 on 2008-07-16
I had that same problem...
My config: Kubuntu Hardy Heron on IBM T23 (all updates) and Wine 1.1.1.

---

### Post by OpposingForce on 2008-07-16
Same problem here, using wine 1.1.1 and CS 1.6 did a hard freeze on me yesterday as well.  I never bothered to go back into the game to try to reproduce this problem, thinking it to be an isolated incident.  But obviously that doesn't seem to be the case here.

Hardy
Wine 1.1.1
Toshiba Satellite Laptop
Radeon X1200

I played CS 1.6 in previous versions of WINE and not once did it ever lock up.  It only started happening in the new version of WINE for me.

---

### Post by Fred_E _krugar on 2008-07-17
I am not sure if this helps yall but I play CSS the only time I had hard freezes, was when I turned the resolution to high.

Try turning down the res and see if that helps.

---

### Post by n4p1 on 2008-07-17
I find a reason I think. When I turn off sound in wincfg, I can play cs... Can you guys try this and confirm?
ps. changing settings (res etc.) in graphics dosent help.

added:
I have sound only when I check ALSA (but game freeze my kubuntu) in wincfg. When I check OSS, JACK sound dosent work but cs dosent hang up and I can play.

---

### Post by daniel7860 on 2008-07-19
ALSA-sound:yes-game freezes
OSS or/and JACK-sound:yes- game still freezes
:confused:

---

### Post by cr4nk on 2009-01-03
i have same cs 1.6 freeze problem. I got the latest wine with ubuntu 8.10. I tried it on different resolutions using the opengl and it kept on freezing, but then i tried the software setting and the game played fine. The thing is that with the software setting on the graphix arent as good.

Its alright to play this way, but its far from being as enjoyable as with the better graphix. btw i got the intel 915gm with media accelerator 900.

>>EDIT Jan 3, 08, 5:16<<

I tried to play cs 1.6 a couple of times since yesterday with different configurations and it doesn't seem to not freeze after about 10sec of gameplay. I tried setting the graphics in game to opengl with different resolutions then the software setting and d3d?? (the 3rd choice), and all of them freeze. I also tried setting the audio driver in wine configuration to OSS and checking the Driver emulate checkbox and choosing hardware emulation from the drop down menu. It still froze with those settings.

The weird thing is that I actually played cs 1.6 with the opengl setting with widescreen resolution (i got widescreen laptop) for about an hour with no glitch or any problem, but i tired to connect to a different server and it froze again.

This leads me to believe it might be something with the servers that make it crash, maybe the valve protected servers dont recognise the cs on my linux or something. I will do more testing with this to try and figure it out, Ill update this once I find something.

---

### Post by cr4nk on 2009-01-03
Just as I have suspected. I can play with the widescreen settings and opengl selected in game. I played 2 servers with no anti-cheat for about 10min each with perfect results, everything seemed to work as I remember it workin on xp. BUT here is where I found the problem: When i joined a game with an anti-cheat enabled then the game froze about 15-20sec, I was just spectating someone after I picked a team and it still froze.

The anti-cheat somehow thinks that linux is a cheat, haha. Well thats where it needs to be fixed. If some other ppl could confirm this than mabe we can get this solved.

---

### Post by cim on 2009-02-17
hmm, i tried a lot of settings and my game still freezes too. i was hoping the forums here would have a fix =/

---

