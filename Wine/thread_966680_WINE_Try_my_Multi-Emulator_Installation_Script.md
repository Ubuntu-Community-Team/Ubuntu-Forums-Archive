---
title: "WINE: Try my Multi-Emulator Installation Script"
date: 2008-11-01
forum: Wine
---

### Post by Dawey on 2008-11-01
Hi everyone! I made an easy installation script for many Windows-based emulators that downloads and installs them in a new wine prefix.

**Current emulators:**
Project 64 1.6
NO$GBA Free version
nullDC 1.0.3
MAMEUIFX32
Fusion

I wrote it to easily download emulators on different system, and I thought I would share it with you! I know, it's very basic, and I just started bash scripting two days ago, but the script does what is was created for.

**Some important stuff:**

1. How to run it:
Download the script from this thread
Extract
*chmod +x install_emulators*

2. What you need:
WINE
unzip (for NO$GBA and Fusion)
unrar (for nullDC)

3. All programs are placed in $HOME/.wine_emulators wine prefix.

4. You can make the startup scripts universal by moving them to /usr/local/bin

Example: *cd $HOME && sudo mv pj64 /usr/local/bin*


Feel free to try it out and write a few lines, It's fun to script and I would very much like to have some constructive criticism! :)

You can also download it from here: [http://www.freewebs.com/dawey/install_emulators]("http://www.freewebs.com/dawey/install_emulators")

---

### Post by krom303 on 2008-11-23
sorry,
the idea is brilliant, but it doesn't work for me: nothing happens at all...
how did you get nulldc 1.0.3 proprely installed? can you run games properly? i'm having problems with 1.0.0beta1.6 (slows down after a while,crashes no menus,..) and i couldn't get 1.0.3 running.

ciao! :)
david

---

