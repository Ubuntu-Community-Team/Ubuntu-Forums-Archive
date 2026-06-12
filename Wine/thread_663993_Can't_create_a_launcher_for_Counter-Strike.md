---
title: "Can't create a launcher for Counter-Strike"
date: 2008-01-10
forum: Wine
---

### Post by LordKael on 2008-01-10
Hi.. so, where's the situation:

I have Cedega up and running, and I have a "unofficial" version of Counter-Strike: Source. It's quite outdated and, well, sucks.. but it runs well (even on linux :D), and that's what some of my friends play.. so I use it to play with them...

Anyway, moving on. I used cedega to open the game (which is pre-installed):
sudo cedega hl2.exe -steam -console -game cstrike
This command has to be executed INSIDE the game folder, otherwise it just won't work (and yes, I used full folder).

I managed to create a desktop launcher and copied it to the game folder... the launcher, of course, uses the command:
gksudo cedega hl2.exe -steam -console -game cstrike


But now I can't create a workable launcher or link to that launcher, so I can actually have a game icon on my AWN, for example.

Anyone knows anything about this?

Thanks,
Kael.

---

### Post by shad0w_walker on 2008-01-11
1. By unofficial I am going to assume you mean pirated. The forums have strict policy on pirated content and regardless of how you sugar coat the word it will not be looked on with any more favour.

2. Why in the name of Tux are you running the game as root? The privilege separation is there for a reason and if you have to run as root to get the game loading you have done something wrong.

---

### Post by LordKael on 2008-01-11
Yes,, that version is actually pirated. I do have an orginnal version, with a valid cd-key and steam account... I use that version so I can play with my friends :P

I don't think the problem is "just" the root access... I can run the game, but the launcher has to be inside the games's folder. Same with terminal.. I have to navigate to the folder before I can execute the cedega command.

---

### Post by Amstell on 2008-01-11
point it to the directory of the file.  Don't use pirated software, open source is why you loose linux.

---

### Post by Perfect Storm on 2008-01-11
Wether or not. It's still piracy - If you have the activation code etc. contact whom made the game to send you a new copy, that's the legal way.

Generally note:
Piracy is hurting Open Source and linux in generally - so please don't do it. 
And we don't take piracy lighty in the linux community.

Thread closed.

---

