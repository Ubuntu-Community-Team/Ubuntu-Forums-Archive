---
title: "Major system upgrade. Will it work?"
date: 2019-06-17
forum: Wine
---

### Post by Tadaen_Sylvermane on 2019-06-17
I'm upgrading my current ivy bridge i5 system to include an AMD Rx570 gpu, ssd, new mobo, new case, new psu. I am mainly doing this to get back into an older game that I played 15+ years ago. I've gotten this game running in PoL quite well, save my hardware being horrible (no dedicated gpu, just i5 hd4k). My question is simple. Will a game run in Wine / PoL utilize the gpu properly or not? Will I get the acceleration I need to do this or should I go to Windows? This whole upgrade was for either this or World of Warcraft, this first game being my preference. I already own a W10 license, so acquiring that is already a non issue. I've flip flopped on linux or not based on some things I've read but if this will work fine then I may as well stay with what I know.

---

### Post by Mr. Swiveller on 2019-06-19
*Play on Linux* is really just a front end for Wine. Essentially, then, your question is whether Wine is capable of utilising your GPU. 

It should be - provided, of course, that you have installed the necessary drivers - although you may need to use the DRI_PRIME=1 command to force Wine to use the dedicated GPU rather than the one built into your CPU. 

Assuming you are in the folder containing the executable, the command could look like

DRI_PRIME=1 wine APPLICATION_NAME.exe

Where APPLICATION_NAME would, of course, need to be replaced with the real name of the executable.

---

### Post by CatKiller on 2019-06-20
You'll probably find it useful to be on the Hardware Enablement Stack, or maybe even use a PPA, to get the newer versions of the kernel and Mesa. AMD support is improving all the time.

Wine is fine at using accelerated graphics.

---

### Post by mastablasta on 2019-06-21
what is the game you need to run?

likely it should all work well. but you say you are having issue with 15+ year old game and intel HD 4000? this is odd because such old games should have no issues on this chip.

---

