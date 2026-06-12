---
title: "Ubuntu login"
date: 2005-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by koriel on 2005-03-26
I install ubuntu and I create a user..I can boot X with this user but when I try to boot as root the user and pass fields on the screen are cleared and I can't boot?Help....

---

### Post by ola on 2005-03-26
You shouldn't use the root-user. Instead you should log in as your normal user and use sudo (followed with your password) to execute a command that requires root privileges.

If you need root access for a longer time you could use sudo -s (s for shell) .

All other things that needs root privileges in Gnome should ask for the password (for example synaptics package manager).

---

### Post by koriel on 2005-03-26
and what if I need to mount a device?mount is supposed to be executed by root right?

---

### Post by mercurus on 2005-03-26
[QUOTE=koriel]and what if I need to mount a device?mount is supposed to be executed by root right?[/QUOTE]
 You can use sudo to mount devices, and then allocate the resulting filesystem a normal user as the owner. Additionally, all removeable media (CDs, floppies, USB drives and so on) can be mounted as a normal user by passing the "user" option to mount. Most removeable media will automatically be detected and mounted when it is inserted under Ubuntu.

---

