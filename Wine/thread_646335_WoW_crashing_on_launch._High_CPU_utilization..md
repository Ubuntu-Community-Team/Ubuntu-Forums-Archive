---
title: "WoW crashing on launch. High CPU utilization."
date: 2007-12-21
forum: Wine
---

### Post by h0ser81 on 2007-12-21
Alright so I've installed World of Warcraft under Wine following the How To found on this forum. The install completes just fine but when I try to launch WoW all that happens is the hard drive thrashes for a little bit and then my CPU usage jumps to about 75% utilization and stays there. No window launches or anything. WoW creates a crash log and I have to kill the wineserver to get my cpu back to an idle state. I've enclosed the crash log text and the output from the CLI from wine. Any ideas as to what is keeping me from launching it? 

Output from wine in the CLI:
fixme:advap:SetSecurityInfo stub
fixme:powerprof:DllMain (0x7c870000,1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powerprof:DllMain (0x7c870000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34ede4,0x00000000, stub!

---

### Post by DarthOpto on 2007-12-21
I hope that this will help. 
I installed WoW last night and it works flawlessly. 
I followed the instructions found [here]("https://help.ubuntu.com/community/WorldofWarcraft")
This was a link I found off of the [WoWWiki]("http://www.wowwiki.com/Linux/Wine")
These instructions worked well.

---

### Post by h0ser81 on 2007-12-21
Those were the same directions I'd followed. But thanks for the effort,

---

### Post by Tadock on 2007-12-21
To me it looks like your launching WoW in DirectX Wine doesn't run the well under direct X with WoW. Try cd into the wow directory then 
wine ./WoW.exe -opengl
Let me know how it turns out

---

