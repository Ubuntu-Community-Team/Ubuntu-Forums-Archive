---
title: "Uninstalling opera 9.5b2"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by s_spiff on 2008-05-04
Okay, tired installing using the .deb, but ended up with a seg fault. So downloaded the tarball, unzipped it, and ran the command  sudo ./install.sh which resulted in installation of opera, which again gives me the same issue. Now i wish to remove that installation. How do I go about it? there doesn't seem to be a uninstall.sh or a parameter which can be passed to install.sh to do the reverse. Anyone? 
I'm on amd64 Hardy Heron.

---

### Post by roberine on 2008-05-04
According to the installation file this is where all the
files are stored. So removing these files should completely
wipe Opera from the harddrive.

excerpt from install.sh
If you choose to do a standard locations install, files will be put into:/usr/bin, /usr/share/doc/opera and /usr/share/opera

Don't forget to remove ~/.opera
that's where your settings are stored.

---

### Post by s_spiff on 2008-05-04
hey did that. The menu item is still there and all the installation files in the filesystem still exist. but no issues, it hardly uses up any space, so I'll let it remain. Too bad it didn't work, many people seem to be raving about it!

---

### Post by roberine on 2008-05-04
If you right click on the menu there's an option to edit the menu.
You can then remove the entry.
What do you mean by: installation files in the filesystem still exist ??

---

