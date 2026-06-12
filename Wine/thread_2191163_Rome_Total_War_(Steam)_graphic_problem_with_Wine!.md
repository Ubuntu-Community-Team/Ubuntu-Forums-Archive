---
title: "Rome Total War (Steam): graphic problem with Wine!"
date: 2013-12-01
forum: Wine
---

### Post by gianluigi.narciso on 2013-12-01
Hi men of knowledge! :)
I'm a new user of Ubuntu (I'm running the 13.10 version right now) and of this forum. Hoping that this thread is in correct section, I start to describe you my problems. 

Two days ago, I bought in Steam the first Rome Total War. In the APPDB list of Wine, the game looks to be operating well ( [http://appdb.winehq.org/objectManager.php?sClass=version&iId=22972&iTestingId=60368](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22972&iTestingId=60368) ) and I found an installation guide using also PlayOnLinux. 
So I dowloaded PlayOnLinux from the Ubuntu Software Center... and through it I installed Steam. Then (always with PlayOnLinux) I configured Wine, his graphic and libraries (directx) options, I ran Steam, I logged my personal account and I installed, finally, my awesome strategy game :P 

So far, so good, but this is where the problems begin.
Infact now when, after running Steam from PlayOnLinux, I click "play game" (on my Steam's Library) appears the usual Wine which emulates the game, but it shows an incredible graphic problem that make impossibile do anything. 

Screenshots: [ATTACH=CONFIG]248225[/ATTACH][ATTACH=CONFIG]248226[/ATTACH]


P.s. I tried to change the version of Wine (1.7/1.5.9/1.4/1.3.34/1.3.26 etc...) using the PlayOnLinux configurations, but this "error" is never resolved. 


Ideas? Can anyone help me? 

Thanks!

---

### Post by gianluigi.narciso on 2013-12-15
Up please!

---

### Post by gianluigi.narciso on 2013-12-20
Up

---

### Post by gianluigi.narciso on 2013-12-28
Up

---

### Post by spupazza on 2013-12-30
I can confirm you that the old cd version works quite well for me (mods included).
For your steps it seems you did everything fine, so it's difficult to say if the problem is the steam version or not.

You probably better ask on official forum or twcenter.net. It might be more likely to find someone who run the steam version on linux.

---

### Post by novikov-dmitri-a on 2014-02-13
I have exactly the same problem as you. I've tried to launch the game in VirtualBox, but same issues. Have you got the solution? I'm suspecting that the issue is IntelHD graphic card.

---

### Post by novikov-dmitri-a on 2014-02-13
I've got this working. In my case the issue was Intel HD 3000 video card. I have Lenovo T520 with both Intel and Nvidia card. Running wine with "primusrun" (using NVidia) solved my problem.

---

