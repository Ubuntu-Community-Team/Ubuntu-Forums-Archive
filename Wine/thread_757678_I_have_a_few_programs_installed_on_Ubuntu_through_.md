---
title: "I have a few programs installed on Ubuntu through Wine, and need to remove them."
date: 2008-04-17
forum: Wine
---

### Post by michaelfougnie on 2008-04-17
Wine seems to be as unreliable as actually using Windows. I tried Applications>Wine>Remove Wine Software and went through the uninstaller dialogs, but a few things remain. I need to get rid of iTunes and a few other things so that I can install an older version of the same stuff that I know works.

---

### Post by chewearn on 2008-04-18
Perhaps the issue should be rephrased as: iTunes removal is unreliable (I think iTunes is the real culprit here).

---

### Post by happyhamster on 2008-04-19
As a last resort you can always delete the hidden .wine folder in your home dir (this means you'll have to re-install everything you had working under wine). To be able to see hidden files, go to Places --> Home Folder and press ctrl-h.

- After getting rid of .wine, you can create a new one by running the command

wineprefixcreate

- or run winecfg to be able to configure wine:

winecfg

---

### Post by jaggedseven on 2008-04-19
i had the same prob. everything i installed in wine would not uninstall. wish i could help but i ended up just uninstalling wine and loading up virtual  box.

---

