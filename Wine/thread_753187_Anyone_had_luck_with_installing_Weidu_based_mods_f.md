---
title: "Anyone had luck with installing Weidu based mods for Baldurs Gate?"
date: 2008-04-12
forum: Wine
---

### Post by Melhisedek on 2008-04-12
I installed BG2 with ToB expansion and wanted to have so mods installed as well. Like Fixpack and Tweakpack and so on. Most of the latest mods are Weidu based (If I understand it correctly that is some kind of installer and compiler for Infinity engine based games but don't take my work for it). According to readme files after extracting files it needs msdos prompt will show up and you'll answer what mod components you want to install and so on. 

Mods extract fine but no prompt shows at all :( 

Anyone had any luck with this?

---

### Post by bears on 2008-05-21
Hello,

I have also recently tried installing the old BG games after buying the Forgotten Realms megapack to get some of the expansions I missed. Also I wanted to try some of the Infinity Engine mods, as you are trying.

On a new 8.04 Ubuntu Installation, each of BG, TOSC, SoA and ToB installed perfectly well under Wine simply by clicking on setup.exe on each DVD. Note that in this edition, the CDs are repackaged as one DVD per title, so there was no problem with disk swapping.

However, I did note that some of the launcher applications on the DVDs were unable to spawn the setup programs. Wine obviously still does miss some of the lesser used features of the various Windows APIs.

When I got onto installing mods, the Weidu system is really the best way to integrate installing multiple mods (if they support it, of course). The Weidu system seems to universally use a two-part routine which first unpacks to your game directory, and then runs an installation executable. Unpacking always seems to work, running the installer never seems to work. 

This is simply because the spawning of a process to run the installer goes pear-shaped by not providing the required execution environment. However you can run all of these installers MANUALLY whenever you want in these simple steps.

1. Press alt-F2 to open a "Run Application" Window, type ""wineconsole cmd"" (with or without the quotes) and press the "run" button.

2. You will be presented with a Windows 2000 command prompt, sitting in your home directory in the Z: drive. Change to the C: drive and to the directory where you have installed your game.

3. In the game directory type ""dir *.exe"" to see a list of executable files. All of the Weidu installers should be there in the form Setup-xxxx.exe, where xxxx is some name related to the Weidu mod being installed.

4. Just type the name of the executable installer you want to run and press return; you will get the normal Weidu Q&A installer session.


Hope this helps.

B.

---

