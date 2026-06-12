---
title: "Help me install gimpshop pls"
date: 2006-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by srikat on 2006-07-29
[http://cmb.phys.cwru.edu/kisner/gimpshop/amd64/](http://cmb.phys.cwru.edu/kisner/gimpshop/amd64/) has a bunch of .deb files for installing gimpshop.

I uninstalled Gimp, downloaded all the above and started double clicking one after another to install gimpshop.

For some, I got a msg that a later version already exists and so I didn't opt to reinstall.

For one, I got a msg that an update is avail and so I updated that.

However, for 3 files I get dependency probs as in the screenshots attached.

Anyone has an idea to fix these and finish the installation? Currently I don't find a shortcut to gimpshop in Applications -> Graphics.

Thanks.

---

### Post by FluffyElmo on 2006-08-01
All three of the required packages in the screenshots are available via Synaptic. If you don't see them try enabling the Universe and Multiverse repositories. 

Run Synaptic (*System->Administration->Synaptic Package Manager*), and from the menu select *Settings->Repositories*. In the dialog click the *Add* button, check the boxes next to Universe and Multiverse and then click *Add*.

Exit out of the repository dialog and if you don't see a progress indicator then click the *Reload* button in the main Synaptic window. You should then be able to exit Synaptic and try installing the .deb files again.

If this doesn't work then it may be that Gimpshop wants specific versions of the libraries. Try this and report back if that is the case.

Good Luck!

---

### Post by jamesford on 2006-08-01
what makes it different from gimp? from the screenshots it looks just like gimp. i was hping it would be some kind of multi document inerface things instaed of all those thingies all over the desktop

---

### Post by FluffyElmo on 2006-08-01
It simply changes the menu structure and terminology to be more consistent with Photoshop. If you already know Gimp well there is really no point. If you're accustomed to Photoshop and similar Windows editors though it makes the transistion to and from the Gimp less jarring.

I think the Windows version also uses a plug-in that mimics a MDI interface, but the Linux version doesn't...why I don't know. I haven't actually tried this myself, but now that there is an amd64 port I may give it a go.

---

### Post by jehnx on 2006-08-13
Yeah, [GIMPshop](http://www.gimpshop.com) is simply made as a transitioning tool for those who are used to Photoshop, not for those who are already used to GIMP.  It just makes like a little easier.  ;)

---

