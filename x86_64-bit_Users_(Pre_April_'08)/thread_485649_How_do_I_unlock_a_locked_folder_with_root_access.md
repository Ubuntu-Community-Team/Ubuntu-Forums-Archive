---
title: "How do I unlock a locked folder with root access?"
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lokk on 2007-06-27
My desktop folder is currently locked so I can't download anything to the desktop because it says I don't have the permissions. Currently the desktop folder says I need root access to change the permissions, but once in root access how do I unlock the folder for a regular user?

---

### Post by ESPOiG on 2007-06-27
sudo chown <user> /home/<user>/Desktop

<user> being your username

---

