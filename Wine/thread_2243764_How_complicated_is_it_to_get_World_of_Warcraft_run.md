---
title: "How complicated is it to get World of Warcraft running on Ubuntu 14.04?"
date: 2014-09-11
forum: Wine
---

### Post by S2005x on 2014-09-11
I'm guessing I will have to use WINE. 

I have never tinkered with Ubuntu before. I have 2 PCs. One is a Win7x64 machine, and it's my primary machine.

I have a second that I have recently installed ubuntu on to play around. I'm seriously entertaining the idea of moving all my computers over to Ubuntu.

However, I do still tool around in the world of warcraft, and need to know if it is going to work. I want to be able to successfully run it on my 2nd machine before moving ubuntu into my primary.

There are actually a few windows programs that I'd like to run. WoW is just the first one that pops in mind.

---

### Post by uRock on 2014-09-11
I haven't set up WoW on ubuntu. Here's the official documentation for getting WoW on ubuntu to get you started. [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by S2005x on 2014-09-11
uRock again! 

Man, you're the best. Awesome avatar too. Breaking Bad was amazing. I need to go back and watch it all again... 

I'll read up on that, and see if I can get it working!

---

### Post by Zirts on 2014-09-12
There is a program in Sofware centre called PlayOnLinux. That program can literally one click install it for you.

---

### Post by S2005x on 2014-09-12
So that's an easier way than WINE?

I have installed WINE, and WoW is making me install the battle.net launcher now, and it won't let me get very far before crashing.

I'll try the PlayOnLinux tool later today :D

---

### Post by sffvba[e0rt on 2014-09-12
> **S2005x said:**
> So that's an easier way than WINE?

I have installed WINE, and WoW is making me install the battle.net launcher now, and it won't let me get very far before crashing.

I'll try the PlayOnLinux tool later today :D

PlayOnLinux uses Wine with custom scripts to install all the relevant additional stuff and set-up the environment to work automatically.  Recommended.  (Also check out Codeweaver Crossover, paid for but does the similarly).

---

### Post by S2005x on 2014-09-12
Awesome! I'll be sure to add it then, and work through that.

Right now I'm doing battle with my WiFi card, and I need to buy a new one (Already have another thread about that...) 

When that is resolved, I'll work on getting WoW to run :D

---

### Post by bapoumba on 2014-09-13
*Thread moved to **Wine**.*

---

### Post by S2005x on 2014-09-13
Thanks for moving this :D

However, I still get this error EVERY time I try to install it using Wine OR PlayOnLinux. It goes through the steps, then opens battle.net installer and asks me to log-in, so I do. Then it loads the battle.net launcher and it crashes, and gives me that error.

About 1 more day of headaches, and I'm going back to Win7... 

[IMG]http://i.imgur.com/07UZ3E4.jpg[/IMG]

---

### Post by CantankRus on 2014-09-13
Don't play it myself but just came across this recent article in my RSS feeds.
May be of help.
There is a section dealing with your above issue about a third of the way down the page.
The article also recommends to install the latest ppa version of wine...
> 2. Optional but recommended (using this will most probably result in not experiencing 
most of the errors described below, in the "fixing various crashes" section)
: install the latest Wine from the official Wine PPA: 

[**_[COLOR="#B22222"]How To Install World Of Warcraft In Ubuntu Or Linux Mint[/COLOR]_**]("http://www.webupd8.org/2014/09/how-to-install-world-of-warcraft-in.html")

---

### Post by S2005x on 2014-09-14
Do I need to uninstall previous versions of WINE or PlayOnLinux?

I'm afraid I don't know what PPA is. 

If I type the code into terminal, will it do this for me? 

```

[FONT=arial][SIZE=2][COLOR=#000000]sudo add-apt-repository ppa:ubuntu-wine/ppa
[/COLOR]sudo apt-get update
sudo apt-get install wine1.7[/SIZE][/FONT]
```

This is just for my future reference (I'm not home, I'm on a work PC)

```

[B]A. If the World of Warcraft installer / Battle.net crashes

If Battle.net crashes on start:

[CENTER][[IMG]http://3.bp.blogspot.com/-ciIjULI1FjI/VBLEpAUR0TI/AAAAAAAAUSs/eJ-Xg-WdCQ0/s320/wow-battlenet-error.png[/IMG]]("http://3.bp.blogspot.com/-ciIjULI1FjI/VBLEpAUR0TI/AAAAAAAAUSs/eJ-Xg-WdCQ0/s1600/wow-battlenet-error.png")[/CENTER]

Fix it by launching "Configure Wine" from the menu / Dash (or press ALT + F2 and enter: *winecfg*) 
and on the Libraries tab, under "New override for library", enter "dbghelp" (without the quotes), 
then click "Add". Next, select "dbghelp" under "Existing overrides" and click "Edit" and in the new pop-up, 
set it to "Disable":[/B]
```

---

### Post by CantankRus on 2014-09-14
An ubuntu PPA is a personal package archive where you may find later versions of an application
that may not be available yet in the official repositories.
Once the PPA is added to software sources it will be checked during normal system updates 
for updates from the added PPA.

I would remove playonlinux, and then just follow the guide from webupd8.
***NOTE*** You copy and paste one line at a time into the terminal, press enter and wait for it to finish.
It will upgrade wine from 1.6 to 1.7

The author states that doing the WINE upgrade may fix your issue.
If not try the bugfix.

....and if in your opinion the benefits you gain from using Linux are not worth the extra learning or time to configure
then maybe you should just stick to windows.
Many are here to help but it's your decision which way to go.

In my case I dual boot with Windows just for one old FPS game.
Not because the game won't run, but because the anticheat Punkbuster program
does not recognize Linux as a valid OS even though the game servers run on Linux.

---

### Post by S2005x on 2014-09-14
Thank you so much for your time! And your help! 

I was banging my head against the wall, and frustrated. I was also having hardware compatability issues with 3 different wireless cards. I finally just got an old router, and flashed DD-WRT onto it, and solved the issue. I'm going to continue trying to learn linux, and I'm still trying to see the benefits. So far, my favorite, is that it's free.

The support/community/forums are amazing. I've never had so many people jumping to help a newbie in any other community before.

When I get home from work, I'll give your directions a shot :D I'm sure we will get it figured out eventually. This is mainly my wife's computer. All she does on the computer is surf the web, watch youtube/netflix, listen to music (Gotta get Spotify working on Ubuntu), and she wants to try World of Warcraft again (She hasn't played in a few years.)

---

