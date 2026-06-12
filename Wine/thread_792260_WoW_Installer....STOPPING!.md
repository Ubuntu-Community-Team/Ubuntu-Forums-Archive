---
title: "WoW Installer....STOPPING?!"
date: 2008-05-12
forum: Wine
---

### Post by VampiricFang on 2008-05-12
I get to disk 2/8 for World of Warcraft, when it tells me to put in disc three I get an error message similar to "Application won't allow cdrom to unmount" something along those lines. I got frustrated and left, and decided I should console more knowledgeable people. Please help!

---

### Post by VampiricFang on 2008-05-12
Trying to install it again, this time Disc ONE gives me guff!

"Cannot unmount volume

An application is preventing the volume 'WoWDisc1' from being unmounted."

---

### Post by Jovec on 2008-05-12
Open a second terminal and type "wine eject d:" when the install is asking for the next disc.

Or

Copy the contents of all your WoW CDs into a single directory, and then run the Installer from there.  Technically you just need the entire contents from one disc, and the *,mpq file from each of the others, but IIRC Blizzard puts the necessary install files on every disc.

---

