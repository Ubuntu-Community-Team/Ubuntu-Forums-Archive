---
title: "Invisible Characters Torchlight"
date: 2011-07-20
forum: Wine
---

### Post by dragonboss on 2011-07-20
Installed torchlight in wine and after a few tries with some errors and a reinstall of wine and torchlight, I finally got torchlight running, with one problem. All monsters and characters do not appear in game. Your character appears in the menus but not in game. Strangely, all the weapons appear and the shadows as well. Is there a fix for the invisible characters?

---

### Post by P-I H on 2011-07-21
On my installation, with an AMD Radeon graphic card, I used winetricks to set glsl option to disable.

---

### Post by dragonboss on 2011-07-21
What steps do I have to take to set glsl to disable.

---

### Post by Soulcage on 2011-07-21
Disable it in the registry [http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

---

### Post by P-I H on 2011-07-22
To start Winetricks in Unity, just use the Dash. Open the Dash, type **w** and select Winetricks. It is also possible to use the command **winetricks** in the terminal.
In the first menu select **Select steam (Steam)**, in the second menu select **Change settings** and in the third menu mark the setting **glsl=disable** and click **OK**.

I used Winetricks to install Steam. In case there is no steam alternativ in the first menu I suppose it is OK to select **Select the default wineprefix**.

---

### Post by dragonboss on 2011-07-22
I don't see the section for Direct3D to disable glsl in the registry

---

### Post by dragonboss on 2011-07-22
Steam is not installed.

---

### Post by Soulcage on 2011-08-07
You have to make the entries or w/e.

---

