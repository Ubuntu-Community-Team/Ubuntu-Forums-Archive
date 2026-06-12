---
title: "World of Warcraft Burning Crusade Graphics?"
date: 2008-09-02
forum: Wine
---

### Post by Ray Hunt on 2008-09-02
I recently converted an old Dell PC with 
P4 2.6gHz 
1.2Gb RAM
GeForce FX5200 128MB AGP 8x
Intel onboard sound

from WinXP to Ubuntu Linux and have been struggling the past few days getting WoW Burning Crusade up and running using wine. I installed WoW by copying the folder via network connection from another WinXP MCE box. I used the Wine hack and added the following lines to the WoW config file

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"

One would expect life to be good however I'm getting unusual green video artifacts on the screen where any outdoor landscape is present (grass, hills, mountains, paths, bodies of water, etc) Is this the video flickering effect that I've read of or something different? The next part of my question is would this be a hardware issue or is something missing on the software side?

---

### Post by Ray Hunt on 2008-09-04
After talking w/a few guild members (thx to Liern & Antarus) it's a pretty safe bet the GPU is the culprit. Waiting for the new GeForce 6200 card to arrive. Will post update after the upgrade.

---

