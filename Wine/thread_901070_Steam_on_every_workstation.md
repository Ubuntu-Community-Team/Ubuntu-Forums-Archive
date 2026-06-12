---
title: "Steam on every workstation"
date: 2008-08-26
forum: Wine
---

### Post by jtech55 on 2008-08-26
I'm using the latest version of ubuntu as well as wine. 
However when running Steam on one workstation[desktop], and switching to another,
 Steam appears on the workstation I switched to :confused:. Honestly no idea why this is happening. 
I was curious to know if anyone has gotten Steam **to stay** on one workstation?



](*,)

---

### Post by jacksaff on 2008-08-26
It's likely that your files are not stored on the workstation but centrally on a server instead. Whenever you log on to a ws it gets your stuff from the server, including everything you put there last time (ie steam). 
Another scenario is your workstations update from a common image and you've installed stuff to that so now they all have it.
Or your station could be a thin client and do very little computing itself at all...
What exactly is your hardware set-up?

---

### Post by ad_267 on 2008-08-26
I think he means workspaces. I noticed this too but wasn't that worried about it. I don't know any way to fix this.

---

### Post by lightstream on 2008-08-26
> **ad_267 said:**
> I think he means workspaces. I noticed this too but wasn't that worried about it. I don't know any way to fix this.

Yeah it happens with me too. With regular windows, you can select 'Always on visible workspace' to make the window 'follow' as you rotate the cube, but Steam windows seem to do this by default.

Other Wine apps do not exhibit this behaviour, it seems to be only Steam, so surely there must be a way to stop it happening?

---

### Post by jtech55 on 2008-08-26
> **lightstream said:**
> Yeah it happens with me too. With regular windows, you can select 'Always on visible workspace' to make the window 'follow' as you rotate the cube, but Steam windows seem to do this by default.

Other Wine apps do not exhibit this behaviour, it seems to be only Steam, so surely there must be a way to stop it happening?

This is exactly what I mean. Steam is apparently set to be 'Always on visible workspace' and right clicking on Steam its set by default to be 'only on this workspace'... when really its always on visible workspace.

note, i just want to do this because when im playing a game off steam, ex:doom 3, css, dods, i want to be able to switch to another workspace without Steam and the game **following**. I tried using wine to emulate a virtual desktop to fit my whole screen, but when i run games in the virtual desktop, the games do not become fullscreen on the virtual desktop. The games i run off Steam, oddly, resize the virtual desktop, making it smaller, so ill be winding up playing doom in a 300x300 box... originally set as a 1000x1000 box in wineconfig.

i do hope someone has a solution for what im trying to do? :confused:

---

### Post by malimo on 2008-12-27
Same Problem here... [Steam always on visible workspace]
[LIST]
[*]Ubuntu 8.10 x64
[*]Wine 1.0.1
[*]+SteamInstall.msi
[/LIST]

---

