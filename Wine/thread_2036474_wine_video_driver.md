---
title: "wine video driver"
date: 2012-08-02
forum: Wine
---

### Post by Unguidedone on 2012-08-02
I bought a new computer so i could play d3 in wine and seems i need to import a video driver from the windows partition and let ubuntu use it.

[IMG]http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/Workspace1_001.png[/IMG]

---

### Post by blade4 on 2012-08-02
Something you should know beforehand .....

[http://us.battle.net/d3/en/forum/topic/5978861022?page=1](http://us.battle.net/d3/en/forum/topic/5978861022?page=1)

Apparantly wine is detected as a cheating software by D3 . 

Let the slandering and badmouthing commence

---

### Post by Elfy on 2012-08-02
*Thread moved to **Wine**.*

>  Let the slandering and badmouthing commenceThat'll be a good way to get thread closed.

---

### Post by Mark Phelps on 2012-08-02
First of all, you need to know that you can't use Windows drivers in Linux; instead, you need Linux drivers.

Second, Wine is not a Windows emulator; therefore, it can not be used to install drivers.

If your current Linux video driver doesn't support the features needed to run the game, unless there is a Restricted driver that does, you're out of luck.

Linux is NOT a good environment for running Windows games.

---

### Post by cwwilson721 on 2012-08-02
Sigh...

This is why people DON'T use Linux...

My D3 install works fine.

You need:
[LIST]
[*]Proprietary Drivers installed for your video card (Settings > Additional Drivers). If this isn't available for you, good luck.
[*]Latest version of wine (Check stickies at the top of this forum on how to get the Wine PPA working for you)
[/LIST]

As for "it's cheating", that's BS. I've NEVER been banned, and use wine for MANY Blizzard games.

---

### Post by Unguidedone on 2012-08-02
> **cwwilson721 said:**
> Sigh...

This is why people DON'T use Linux...

My D3 install works fine.

You need:
[LIST]
[*]Proprietary Drivers installed for your video card (Settings > Additional Drivers). If this isn't available for you, good luck.
[*]Latest version of wine (Check stickies at the top of this forum on how to get the Wine PPA working for you)
[/LIST]

As for "it's cheating", that's BS. I've NEVER been banned, and use wine for MANY Blizzard games.


Ya wine is NOT banned and this is a fact lol (played d2 on it for going on 5 years now)

Oh well looks like ill have to boot into windows to play d3 grrrr :\

/////EDIT!!!!!!!

Here is the fix!

install dirconfig 
sudo apt-get update

enable s3tc texture compression

AND D3 WORKS!!!

but we still have a login error

so open terminal and 

sudo sysctl kernel.yama.ptrace_scope=0

before login

sadly its kinda choppy performance in wine even on my i7 rig :\

---

