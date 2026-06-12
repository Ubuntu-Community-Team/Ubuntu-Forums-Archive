---
title: "CIV 4   Crashing   during &quot;Init Engine&quot;"
date: 2008-08-10
forum: Wine
---

### Post by daniel7860 on 2008-08-10
When i launch the Game  I a gray box appears and it loads, but when it gets to "Init Engine" it crashes,  it also changes my Resolution from 1440x900  to 1024x768. I have all the dlls installed and properly configured.Patched it to the latest version too. 

My Wine Version is 1.1.2
I am using Hardy and have a ATI Mobility Radeon X300 (compiz works just fine with Accelerated Graphics Enabled)

---

### Post by daniel7860 on 2008-08-10
here is a screen shot of my wineconfig, the ddls  for Civilization4.exe

---

### Post by Vadi on 2008-08-10
I followed these instructions for making Civ 4 work: [http://tombuntu.com/index.php/2007/10/24/civilization-iv-on-linux-updated-how-to/](http://tombuntu.com/index.php/2007/10/24/civilization-iv-on-linux-updated-how-to/)

---

### Post by daniel7860 on 2008-08-16
ye, i followed those instructions.

---

### Post by 4leite on 2008-08-16
I'm running latest hardy.

I installed with [this howto]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9501"). It's for BTS, but works for vanilla civ as well. The only overide I use is msxml3 (native). You need to set the overide before you install.

fresh install of wine.
cp following files from net or win install to .wine/drive_c/windows/system32/ (note that d3dx9.dll is a cp of d3dx9_33.dll)
d3dx9_26.dll d3dx9_32.dll d3dx9.dll msvcp71.dll msxml3.dll d3dx9_31.dll d3dx9_33.dll mscoree.dll msvcr71.dll msxml3r.dll
winecfg:
Libraries->New Overide->msxml3->Add Audio->OK->Apply Graphics->Emulate->[your screen resolution]->Apply
Applications->Version->WindowsXP->Apply
cd ~
wine civ_setup.exe
wine patch.exe
*The installers will complain but should work.

You will also need a no-cd cracked exe which you can google for. Wine doesn't cope with the copy protection on the game.

Sometimes you need to run the installer twice.
Emulating a virtual desktop should fix your screen size problem - I think you need to set it in game options as well.

The wine appdb has some solutions to common problems people have with the install.

---

