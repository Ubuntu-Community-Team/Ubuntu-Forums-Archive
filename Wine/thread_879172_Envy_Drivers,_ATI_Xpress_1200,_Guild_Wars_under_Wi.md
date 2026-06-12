---
title: "Envy Drivers, ATI Xpress 1200, Guild Wars under Wine"
date: 2008-08-03
forum: Wine
---

### Post by Vakman on 2008-08-03
I have an ATI Xpress 1200 card which runs GW fine under Windows which is the only reason I have Windows. I have now tried using the Envy drivers which did not work before and do not work for me now. When I have the 8.7 Catalyst drivers I get a unrecoverable graphics error but when I have the Envy driver my screen becomes scrambled. Help. Just what drivers should I have to run Guild Wars under Wine. Below is a screenshot with the Envy drivers. Sorry about the quality, I had to take it with my camera and therefore it is not a screenshot. Anyway... help please :)
[ATTACH]80090[/ATTACH]

---

### Post by Spydr4590 on 2008-08-03
Hey Thisislaw!

I've done some research for you, specifically ATI users. Install the ATI drivers manually by following this guide [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29)

**NOTE**: You can not run compiz and games in window mode or you will get corruption like the picture you posted. You have to run them in fullscreen if you want compiz on and no corruption for games.

Scroll down to the how to of this link and you should be able to install guild wars with no issues.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

---

### Post by Vakman on 2008-08-03
Thank you, I will try this later. I am on Windows now for a bit to play Guild Wars. I will try later :) Thank you very much. I will post back if it works or does not work.

---

### Post by Vakman on 2008-08-04
Did not work. I still get a scrambled screen.

---

### Post by Spydr4590 on 2008-08-04
Another option you can try is -dx8 for directx 8 Also the -noshaders option may also help [http://wiki.guildwars.com/wiki/Command_line](http://wiki.guildwars.com/wiki/Command_line)

---

### Post by Vakman on 2008-08-04
Used that many times. Never helped me.

---

### Post by JUMBODUMBO on 2008-08-04
You need to use Catalyst 8.5 or earlier for games to work in Wine. Since Envy installs 8.6 these days you can't use that anymore.

---

### Post by Vakman on 2008-08-04
So if I get Catalyst 8.5, I should be fine?

---

### Post by Vakman on 2008-08-04
Well I have Catalyst 8.5 drivers now. Screen does not become scrambled anymore but now I have an unrecoverable graphics error. I have now added the registry keys it said to on the Guild Wars AppDB page and still did not help. Anything else?

---

### Post by Spydr4590 on 2008-08-04
This is how I have my registry setup.

[http://img505.imageshack.us/img505/2096/screenshotas4.png](http://img505.imageshack.us/img505/2096/screenshotas4.png)

---

### Post by Vakman on 2008-08-05
And it works for you?! You have an ATI card, correct? Maybe I entered them incorrectly. Direct3D... I should have that. I put them somewhere else. I will try that later and get back to you.

---

### Post by Vakman on 2008-08-05
Well I have tried to make mine look like yours but you have a few keys that I don't. Your opengl folder is something I do not have. Maybe I should do a fresh install and then I will not have had any mistakes? You can get Guild Wars working with your ATI card?

---

### Post by Spydr4590 on 2008-08-05
You don't need to do a fresh install, and the opengl folder is for wow (world of warcraft) to increase my FPS. The command that I use for wow won't fix GW. I would mess around with those registry commands. Sometimes you need different settings for different Ati cards. I just wanted to make sure you were putting the Direct3D folder in the correct place. Oh and another thing.. Don't run anything with sound besides the game you want to play. Otherwise the games usually crash.

I have two ATI 1900xtx cards, and a 8800GTS Nvidia, in three different systems.

---

### Post by Vakman on 2008-08-05
And which drivers should I have? 8.5 someone else said. Or should I have 8.7 like in that Method Two page?

---

