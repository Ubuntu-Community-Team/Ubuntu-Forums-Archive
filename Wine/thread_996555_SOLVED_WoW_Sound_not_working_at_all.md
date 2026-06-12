---
title: "SOLVED: WoW Sound not working at all"
date: 2008-11-28
forum: Wine
---

### Post by Zagoofeek on 2008-11-28
To those of you who are having problems with your WoW. My WoW was not working ever since I switched to Linux. Well, I got it fixed. 
I have Ubuntu 8.10 and Wine 1.1.9. 
So I went to the Wine cfg. on the Applications tab, selected for my Windows Version Windows XP (even though I have Vista).
Went to the Audio tab and selected OSS, Hardware Acceleration on Full, Default Sample Rate at 44100, Default Bits Per Sample at 16, and no Driver Emulation selected, then apply and close that out. Then went to the World of Warcraft folder, WTF folder, open the Config.wtf and added 
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"

I already added the SET Sound information to the Config.wtf folder and my sound was still not working.
So now my sound works. I had nothing and now it works great. I hope this helps someone out.
:biggrin:

---

