---
title: "Portal 2 (wine 1.4rc6 and Pangolin)"
date: 2012-03-07
forum: Wine
---

### Post by zuti on 2012-03-07
So, trying my luck if someone else has this combination of software. 

I've been trying to get Portal 2 working with the current version of 12.04 and Wine 1.4. I was using the Wine PPA under 11.10, and Portal 2 would launch just fine, I also had a version of Wine I had compiled, which also worked just fine. 

Now that I'm trying Wine 1.4rc6 (or my own build that I used earlier under 11.10), I can't get Portal 2 to launch from Steam. This is what wine prints out: 

```
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
CClientSteamContext logged on = 1
Convar building_cubemaps has conflicting FCVAR_CHEAT flags (child: has FCVAR_CHEAT, parent: no FCVAR_CHEAT, parent wins)
Game.dll loaded for "Half-Life 2"
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0x230): stub
err:d3d:wined3d_wndproc Window 0x20154 is not registered with wined3d.

```

However... If I launch Steam, and run Portal 2 separately (wine blablab/portal2.exe), it works just fine.

Edit: I guess the only useful bit of info in that printout is "err:d3d:wined3d_wndproc Window 0x20154 is not registered with wined3d.", I just checked, and everything else except that is printed when I run Portal 2 successfully from the terminal.

---

