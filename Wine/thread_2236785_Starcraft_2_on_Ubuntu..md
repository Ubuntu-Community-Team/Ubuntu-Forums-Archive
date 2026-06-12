---
title: "Starcraft 2 on Ubuntu."
date: 2014-07-28
forum: Wine
---

### Post by captainmanic on 2014-07-28
Hi,

I've tried numerous methods to get sc2 to work.

Currently i am receiving help at [http://us.battle.net/sc2/en/forum/topic/13088129309#1](http://us.battle.net/sc2/en/forum/topic/13088129309#1)

I need help with the help lol.

Forgive a noob have a read for me and let me know how to go about "installing a binary"

I've been able to extract a patched version of wine that is supposed to solve my problems, but i don't know how to get ubuntu to recognise or "install" it.

thanks in advance.

---

### Post by kira-yamato-2008 on 2014-07-29
[Here is the WineHQ AppDB page for StarCraft II]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882") since it has a platinum rating it should run fairly well.

[Wine HQ tutorial for installing the latest Wine on Ubuntu]("http://www.winehq.org/download/ubuntu"). That's how I did it on Lubuntu 14.04 but the tutorial is specifically for Ubuntu so it should work for you.

Hope that gets things up and running for you. If you have any other issues Play On Linux can be found in the Ubuntu Software Center, and it has a method built in for installing StarCraft II. You do still need Wine for Play On Linux by the way.

---

### Post by captainmanic on 2014-07-29
hi Kira. Thanks heaps for your response. I'm going to try installing the latest wine on ubuntu, although i had trouble doing that last time. It installed 1.7.22 instead of 1.7.23.

i was hoping to get help following thses instructions

"
    
Try the csmt wine patch for sc2. The framerate is amazing now way better than windows for me, I get 250 FPS on high graphics for early game.

Basically it changes how D3D works so even though sc2 isn't programmed to use multiple cores it does and its working great.

binaries: [http://lutris.net/files/runners/wine-1.7.1-patched.tar.gz](http://lutris.net/files/runners/wine-1.7.1-patched.tar.gz)
patch applied wine sources: [https://github.com/stefand/wine](https://github.com/stefand/wine)
raw patch: [http://www.winehq.org/pipermail/wine-devel/2013-September/101106.html](http://www.winehq.org/pipermail/wine-devel/2013-September/101106.html)

Also requires the following registry edit

HKCU/Software/Wine/Direct3D/CSMT = "enabled" "

---

### Post by Bucky Ball on 2014-07-29
*Thread moved to **Wine**.*

Welcome. You'll probably have more luck here.

---

### Post by kira-yamato-2008 on 2014-07-29
> **captainmanic said:**
> hi Kira. Thanks heaps for your response. I'm going to try installing the latest wine on ubuntu, although i had trouble doing that last time. It installed 1.7.22 instead of 1.7.23.  i was hoping to get help following thses instructions  "      Try the csmt wine patch for sc2. The framerate is amazing now way better than windows for me, I get 250 FPS on high graphics for early game.  Basically it changes how D3D works so even though sc2 isn't programmed to use multiple cores it does and its working great.  binaries: [http://lutris.net/files/runners/wine-1.7.1-patched.tar.gz](http://lutris.net/files/runners/wine-1.7.1-patched.tar.gz) patch applied wine sources: [https://github.com/stefand/wine](https://github.com/stefand/wine) raw patch: [http://www.winehq.org/pipermail/wine-devel/2013-September/101106.html](http://www.winehq.org/pipermail/wine-devel/2013-September/101106.html)  Also requires the following registry edit  HKCU/Software/Wine/Direct3D/CSMT = "enabled" "  That's good to know, now if I could only get my system to run an nvidia binary I could play Star Trek Online.

---

### Post by captainmanic on 2014-07-29
lol i'd love some help playing SC2 haha

by the by does blizzard charge money for people playing SC2 online? i never did figure that out?

any chance for a little help with getting all this installed on my pc?

---

### Post by captainmanic on 2014-08-01
I was really hoping for some help installing this csmt wine patch, i'm having trouble getting that help.

Anyone that can help me with this, it would be greatly appreciated

---

### Post by adec2 on 2014-08-01
Try using playonlinux, with that you can choose which wine version to use with starcraft including the csmt patch. Search for playonlinux i'm sure that will help you further

---

### Post by captainmanic on 2014-08-02
adec2 thank you very much. I started off in POL, but i didn't realise you could change the wine version, nor choose the patch.

the next step is changing the registry. Can i have some help with that?

[I][B]To all users of this patch: don't forget to enable the feature in the registry, or Wine will work as usual;
csmt.reg:

[HKEY_CURRENT_USERSoftwareWineDirect3D]
"CSMT"="enabled"[/B][/I]

---

### Post by captainmanic on 2014-08-02
I think i have this sorted, getting some help from POL forum. Thank you guys.

---

### Post by adec2 on 2014-08-02
If you select install in playonlinux then select the games tab above there is a starcraft 2 wings of liberty installer script which may help you. Anyway no problem hope you get it working captain :D

---

### Post by Bucky Ball on 2014-08-02
If you get this fixed, please share how you did it and mark the thread as solved to help others. Good luck.

---

### Post by sffvba[e0rt on 2014-08-03
> **Bucky Ball said:**
> If you get this fixed, please share how you did it and mark the thread as solved to help others. Good luck.

+1 I have not been able to get SC2 HOTS installed via Crossover or POL (a few months back both worked without issues :/)

---

