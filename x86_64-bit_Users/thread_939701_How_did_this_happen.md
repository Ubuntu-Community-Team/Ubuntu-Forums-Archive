---
title: "How did this happen?"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by tesla.coil on 2008-10-06
hi i wanted to remove yum frm the system so i typed in the command ```
sudo-get remove yum*
``` so what happend after was it removed most of my application nearly all of them including gimp firefox,thunderbird,compiz,metacity and nearly most of the appz i donno why ! what do i do to revert this and restore everything to normal? it has almost removed most of the gnome libraries as well.help me!!

---

### Post by Sef on 2008-10-06
Try this from the terminal or command line:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Yellow Pasque on 2008-10-06
Sef's suggestion will reinstall the default Ubuntu packages and get you a working system. To see what other packages were uninstalled, look at /var/log/apt/term.log

---

### Post by tesla.coil on 2008-10-06
thanks a lot boys everythings fine at the moment thanks again

---

