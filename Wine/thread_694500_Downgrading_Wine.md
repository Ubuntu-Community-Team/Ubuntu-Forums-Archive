---
title: "Downgrading Wine"
date: 2008-02-12
forum: Wine
---

### Post by SoberWarlock on 2008-02-12
If I downgrade WINE would I have to restart all my settings or it just downgrades it like a breeze :confused:

I am trying to run Team Fortress 2 without much FPS loss, but I seem to be getting major low FPS and most of the people I see using Team Fortress 2 with good FPS are using the old version so might as well try it out.

---

### Post by hyperair on 2008-02-12
It'll downgrade easily.

---

### Post by Sammi on 2008-02-12
Older version are found here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Just go into Synaptic, do a search for Wine, and do a complete uninstall. Then download a deb from the site above, double click the deb file and choose install.

---

### Post by SoberWarlock on 2008-02-12
> **Sammi said:**
> Older version are found here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Just go into Synaptic, do a search for Wine, and do a complete uninstall. Then download a deb from the site above, double click the deb file and choose install.

If I uninstall wouldn't I lose all my settings and installed programs :confused: I don't want to re-install all my games......

---

### Post by SoberWarlock on 2008-02-12
> **Sammi said:**
> Older version are found here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Just go into Synaptic, do a search for Wine, and do a complete uninstall. Then download a deb from the site above, double click the deb file and choose install.

If I uninstall WINE wouldn't that cause my other programs under wine to uninstall :confused: I don't want to restart my whole entire settings....

---

### Post by happyhamster on 2008-02-12
No, uninstalling wine won't affect the programs you installed. They will still be in the hidden .wine folder in your home dir. Compare it to uninstalling the Gimp: the Gimp is gone, but the drawings you made with it still remain.
(You could also make a backup of the .wine folder for safety. To view hidden files and folders: go to Places-->Home Folder and press ctrl-h). 

- Anyway, to get rid of wine:

sudo apt-get remove wine

- Install the wine version you need.
- Update your configuration with the command:

wineprefixcreate

- And the new wine should be able to run your previous programs.
(Only thing I don't know if the previous menu-entries will work.)

---

### Post by andrewjoy on 2008-03-15
Yes this worked for me i was getting major problems in warcraft with my mouse in 0.9.57 went back to 0.9.56 with this method and it was fine

---

### Post by agtownz on 2008-03-15
If you happened to upgrade through any versions, all of them would be stored in Synaptic so just go there and change back to an earlier version.

---

