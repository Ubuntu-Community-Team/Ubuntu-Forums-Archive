---
title: "Cant write to certain areas."
date: 2006-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Wafflesomd on 2006-08-22
So, it seems I cant write to certain folders, mainly, I wanted to add a skin to the skin directy for xmms (usr\share\xmms\skins)  But it wont let me.

Any help?

"/you do not have permission"

---

### Post by Kilz on 2006-08-22
Users do not have permission to write to every directory in Linux. You need sudo/root access for almost everything outside of the user area. open a terminal and type in 
```
gksudo nautilus
```
then type in your passsword when it asks. This will open up the nautilus as root/sudo. But be carefull what you do. Its possible to do damage.

---

