---
title: "Diablo 3 via PlayonLinux"
date: 2012-11-08
forum: Wine
---

### Post by Gotti on 2012-11-08
So I've installed D3 fine, but am having terrible FPS issues...im maxing out at around 9. I've read of other people having no issues at all. Just wondering if anyone else experienced this...

---

### Post by gerowen on 2012-11-08
> **Gotti said:**
> So I've installed D3 fine, but am having terrible FPS issues...im maxing out at around 9. I've read of other people having no issues at all. Just wondering if anyone else experienced this...

As a general rule, running any Windows game with Wine will reduce the performance.  You're using a 3rd party compatability layer to play it on a platform it wasn't designed for, so there's a little more overhead than using native DirectX on a Windows box.  Anyway, my point is that if your computer is borderline D3 compatable while running Windows, you're going to have some heartache trying to play it on Linux.  What kind of hardware are you sporting, and are you using your proprietary video drivers?

---

### Post by Dougie187 on 2012-11-09
I would actually recommend not playing Diablo 3 via wine/playonlinux.

They have recently banned several ubuntu users due to a bug that happens when diablo 3/warden/wine/ubuntu are used.

[http://www.playonlinux.com/en/topic-9679-Diablo_3_Ban_Information_Template.html](http://www.playonlinux.com/en/topic-9679-Diablo_3_Ban_Information_Template.html)

Either way, your best bet (if you don't want to get banned and lose $60) is to play on windows.

---

### Post by holastickboy on 2012-11-12
> **Dougie187 said:**
> I would actually recommend not playing Diablo 3 via wine/playonlinux.

They have recently banned several ubuntu users due to a bug that happens when diablo 3/warden/wine/ubuntu are used.

[http://www.playonlinux.com/en/topic-9679-Diablo_3_Ban_Information_Template.html](http://www.playonlinux.com/en/topic-9679-Diablo_3_Ban_Information_Template.html)

Either way, your best bet (if you don't want to get banned and lose $60) is to play on windows.

It's worth mentioning that not ALL Diablo 3 players have been banned, and its UNPROVEN that Wine is the cause of the bans.  While I can appreciate that there are a lot of players out there that may have been banned, it might be a little mean to scare someone into thinking it might not be a good idea, particularly when the users banned dont have any actual evidence.  Furthermore, there have been a lot of bans recently on accounts that dont even use Linux.

Been playing Diablo 3, SC2, WoW on Wine since launch, never been banned since the infamous ban years ago. Was playing on Wine back when Blizzard did ban Wine players (must have been 5-6 years ago now), but they admitted the problem virtually overnight and reinstated all accounts.

Blizzard is claiming that the currently banned accounts were banned for use of exploitive software, that has been in run in CONJUNCTION with Wine. Warden detects active Dlls, not Wine versions, kernel information, etc.

---

### Post by Dlambert on 2012-11-13
All depends on your hardware. Update your drivers, etc.

---

### Post by 420wizkid on 2013-02-06
ok so as to not waste time im running ubuntu 12.10 (quantal) 64 bit
kernel linux 3.5.0-23-generic
GNOME 3.6.0
3.8 GiB or ram
Intel® Core™ i3-2120 CPU @ 3.30GHz × 4
available disc space 362.6 GiB
now  then the issue I am having is this i copy a up to date version of d3  from my Microsoft computer launch d3 with wine it goes to checking for  updates for launcher gets about 2/3rds completed and then just stops no  use of my computer whatsoever what the hell am i missing? i am new from  Microsoft but this is not brain surgery for Christ sakes oh and im  running a ati radion hd 6700
can use World of Warcraft  just not diablo 3 and wine version 1.4.1 please bear with me

---

### Post by cbanakis on 2013-02-06
I would like to warn everyone about running Diablo III under Wine.

A friend of mine was banned because blizzards "Anti-Cheat" software does not differentiate between Wine, and other 3rd party apps that allow cheating.

We saw a bunch of forum posts of people claiming they were banned for using wine, but he had already been running it for several months, so we just figured those people were full of crap, and that they actually were cheating.

But after some time, he too was banned.

He definitely was not cheating.

Not sure if the problem has been fixed yet, but I can tell you that at the time, Blizzards only response to my friend, was to extend their middle finger.

They refused to reverse the ban, and did not have any response to the flaw in their system.
(They basically just said, "that's too bad, we are not doing anything about it")

---

### Post by cbanakis on 2013-02-06
> **420wizkid said:**
> ok so as to not waste time im running ubuntu 12.10 (quantal) 64 bit
kernel linux 3.5.0-23-generic
GNOME 3.6.0
3.8 GiB or ram
Intel® Core™ i3-2120 CPU @ 3.30GHz × 4
available disc space 362.6 GiB
now  then the issue I am having is this i copy a up to date version of d3  from my Microsoft computer launch d3 with wine it goes to checking for  updates for launcher gets about 2/3rds completed and then just stops no  use of my computer whatsoever what the hell am i missing? i am new from  Microsoft but this is not brain surgery for Christ sakes oh and im  running a ati radion hd 6700
can use World of Warcraft  just not diablo 3 and wine version 1.4.1 please bear with me

I'm not sure on your issue, when I set it up for my friend, he had to run a command in terminal before launching D3, or it would not work right, but I don't remember specifics.

As for World of Warcraft...

The linux community in general, is full of huge nerds.
And nerds love World of Warcraft.

Making sure World of Warcraft runs under Wine takes priority over EVERYTHING.

Of course I am exaggerating a bit, but you get the idea.

As far as I can remember, every release of WOW was running in Wine while still in beta, before you could even buy the game.

Anytime you are curious about a program with Wine, you can look it up at [http://appdb.winehq.org/](http://appdb.winehq.org/)

Gives ratings as to how well it works, and usually lists workarounds if any are needed for the program in question.

---

