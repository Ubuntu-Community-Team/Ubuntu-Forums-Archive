---
title: "User problem..."
date: 2007-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by _mOrgoth_ on 2007-05-03
Every time I reset my PC i get this message at system start: "User's $HOME/.dmrc file is being ignored. This prevents default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others user's"

WTF???!!!!:confused:

---

### Post by Kilz on 2007-05-03
> **_mOrgoth_ said:**
> Every time I reset my PC i get this message at system start: "User's $HOME/.dmrc file is being ignored. This prevents default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others user's"

WTF???!!!!:confused:

Is it possible you set the [chown]("http://www.ss64.com/bash/chown.html") or [chmod]("http://www.ss64.com/bash/chmod.html") wrong for a file and ended up doing the whole directory?.

---

### Post by _mOrgoth_ on 2007-05-04
Possible... When I installed wine I used sudo command and it make it root. Now... to fix that I used this command:
sudo chown -R admin:admin /wine
but it allways sad that "theres no such file or directory"
so I tried this:
sudo chown -R admin:admin wine
and that work...
Now I fixed wine but I am geting that error..  Can I fix it somehow???

---

### Post by Kilz on 2007-05-04
> **_mOrgoth_ said:**
> Possible... When I installed wine I used sudo command and it make it root. Now... to fix that I used this command:
sudo chown -R admin:admin /wine
but it allways sad that "theres no such file or directory"
so I tried this:
sudo chown -R admin:admin wine
and that work...
Now I fixed wine but I am geting that error..  Can I fix it somehow???

Yes you can fix it, edit this command to change LoginName to the name you login with.

```
sudo chown -R LoginName:LoginName /home/LoginName
```

---

### Post by _mOrgoth_ on 2007-05-04
Tried... didn't help.... Have any other ideas?

---

