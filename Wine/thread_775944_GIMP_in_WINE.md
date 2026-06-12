---
title: "GIMP in WINE"
date: 2008-04-30
forum: Wine
---

### Post by Houli on 2008-04-30
How do I get GIMP to work properly in WINE or how do I fix it in Xubuntu? I tried installing gimp-shop when I already had GIMP installed and gimp-shop didn't appear in the menu. GIMP stopped working then. I tried reinstalling them both but none of that works and when I try using GIMP in WINE massive font appears on the screen and I can't do anything. Help!

---

### Post by daschl on 2008-04-30
ok, first of all: why do you want to run gimp in wine? it works perfectly in gnu/linux and is shipped with ubuntu!

---

### Post by Cifra on 2008-04-30
> **daschl said:**
> ok, first of all: why do you want to run gimp in wine? it works perfectly in gnu/linux and is shipped with ubuntu!
HE said it doesn't work anymore.

Have you tried uninstalling the gimp and gimpshop with apt-get remove gimp or through synaptic?

---

### Post by Houli on 2008-04-30
Plz read the whole post. It won't run at all in Xubuntu. Neither will gimp-shop.
Cifra. This is what the result of that command is E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Het Irv on 2008-04-30
Try putting sudo in front of the command to run it as root.

---

### Post by Houli on 2008-04-30
It's working under Ubuntu now yay!

---

### Post by Houli on 2008-04-30
Now do any of you know how to move a text layer around the image?

---

### Post by nick09 on 2008-04-30
> **Houli said:**
> Now do any of you know how to move a text layer around the image?

Do you mean over the image layer?

If so then Layer --> Stack to move each layer.

---

