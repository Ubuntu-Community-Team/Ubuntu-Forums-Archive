---
title: "Current World of Warcraft situation"
date: 2011-12-14
forum: Wine
---

### Post by SlvrYeti on 2011-12-14
The only reason I need Windows now is to play World of Warcraft with the Mrs. Quick question, how stable is World of Warcraft 4.3.0 under Wine?

Want to ditch Windows altogether.

---

### Post by cwwilson721 on 2011-12-14
Works perfectly. 

HOWEVER:
[LIST]
[*]Must run Wow.exe, and NOT Launcher.exe. Search Google or this forum.
[*]Use a ATi/AMD or Nvidia card/chip. Intel just won't cut it in wine/WoW. There are SOME 'workarounds', but overall, OpenGL on an Intel chip just doesn't let you really play Wow/wine
[*]Use opengl (either '-opengl' appended to the end of the launch command, or edit config.wtf) (*NOTE: If you append the opengl command, Wow automatically edits the config.wtf file for you)
[*]Run in XP Mode
[*]Sound may/may not work. Chipsets/etc are the cause. If yours works, great, if not, turn it off
[*]Don't expect the same FPS at the same settings as in Windows. OpenGL in Wow doesn't have total support for all features. D3D does. However, sometimes, depending on your hardware, Wow./wine MAY have higher FPS than Wow/Windows.
[*]Updating patches can be a pain. Some have sucess by disabling "enable peer-to-peer" in the options for the downloader. Some can't get to the options in the downloader. To help this out, I have a VM (VMWare Player) with a legal copy of Win7 installed ONLY for patching. Odds are, you can't actually play Wow at a usable level in a VM, but patching/etc, works great. I then copy the entire World of Warcraft folder over to my wine install.
[/LIST]

There are quite a few guides in this forum for installing Wow/wine in Ubuntu. Just "Search This Forum" for "wow+install+howto" for a list

---

### Post by SlvrYeti on 2011-12-15
Thanks very much for the reply. I'll give it a try see how I get on and report.

---

