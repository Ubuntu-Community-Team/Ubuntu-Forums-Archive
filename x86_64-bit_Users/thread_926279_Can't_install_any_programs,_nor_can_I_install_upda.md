---
title: "Can't install any programs, nor can I install updates......"
date: 2008-09-21
forum: x86 64-bit Users
---

### Post by DJSchmidty on 2008-09-21
Haven't been on Ubuntu in a while, and decided to go back on it for a lil...

I have a red arrow for updates, so I goto install them, but then I get an error that reads this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

so I goto run that line in the terminal and I get this:

dpkg: requested operation requires superuser privilege

I also went to go install some new cool programs that I wanted, but I get the same error...

a lil help?
Thanx in advance...
-Schmidty

---

### Post by malrost on 2008-09-21
It's telling you that you need to be a superuser to run the application. You can use sudo to run a command as superuser like this:

```
sudo dpkg --configure -a
```

It will ask for your password, enter it, et voila.

---

