---
title: "Changing default plugin"
date: 2006-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by mickeysden on 2006-12-13
I am using edgy64. The default media plugin for firefox is totem. I tried uninstalling it, but it is required by ubuntu-desktop package. How can I set firefox to use mplayerplugin (it has better features, like full screen)

---

### Post by Kilz on 2006-12-13
> **mickeysden said:**
> I am using edgy64. The default media plugin for firefox is totem. I tried uninstalling it, but it is required by ubuntu-desktop package. How can I set firefox to use mplayerplugin (it has better features, like full screen)

Install the mozilla-mplayer package and make sure the totem-mozilla package is not installed.

---

### Post by mickeysden on 2006-12-14
But thats exactly what I said, i have installed mozilla-mplayer but it wont let me uninstall totem-mozilla unless i remove ubuntu-desktop

---

### Post by hakan69 on 2006-12-14
Hi!
I got the same message about desktop being uninstalled. I took a chance and went ahead, nothing unwanted happened and I got rid of totem. Desktop stayed just as before - perhaps it's a bug??

---

### Post by janfsd on 2006-12-14
No, it's not a bug, this ubuntu-desktop is more like a meta-package, it just indicates wich packages should be installed. However, when removed, none of the other packages should be removed.

---

### Post by drphilngood on 2006-12-14
Not sure if it´s the same but in 32bit edgy, I had the same problem so I deleted the totem plugin links in /usr/lib/firefox/plugins, now Mplayer is used by Firefox.

---

