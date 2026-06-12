---
title: "edit the permission problems"
date: 2008-09-18
forum: x86 64-bit Users
---

### Post by gardengxc on 2008-09-18
I read I had to edit my dhcp3-server file by opening it in a text editor as root. when I try to edit the file it says "could not save file /etc/default/dhcp3-server. you do not have permission necessary to save file.":confused: when I try to it says "you are not the owner. so you can't change these permissions":confused: this is my laptop and I'm the only one who uses it/installs any thing on it. how do I over come this?

ps the thread I read this of has been closed.

---

### Post by cariboo on 2008-09-18
THere are a lot of threads concerning permissions, use Google instead of the forums search, as it seems to find what you are looking for a lot easier. That being said, when you need to run a graphical program as root use **gksu <program>** for example in your case you would press Alt-F2 and in the window that opens enter:

```
gksu gedit /etc/default/dhcp3-server
```

Then enter your password when asked. You can now edit the file and save without any error messages.

Jim

---

### Post by gardengxc on 2008-09-18
thanks on both notes

---

