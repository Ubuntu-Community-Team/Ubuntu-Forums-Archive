---
title: "Synaptic and update manager went down..."
date: 2008-08-27
forum: x86 64-bit Users
---

### Post by Barad on 2008-08-27
Hey all,
    I tried to install skype on my laptop running ubuntu. I ran a search in google to find out how to install it...I found that i have to install medibuntu.I write this lines ([https://help.ubuntu.com/community/Medibuntu#Installing%20Individual%20Packages](https://help.ubuntu.com/community/Medibuntu#Installing%20Individual%20Packages))  in the terminal. Then my update manager and synaptic crashed.. What should i do to get them running.



"Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--19:46:30--' is not known on line 1 in source list /etc/apt/sources.liCould not initialize the package information"

---

### Post by Kilz on 2008-08-27
It looks like you added a bad line to the sources.list file. We can try to restore the old one with these two commands.

```
sudo mv /etc/apt/sources.list /etc/apt/backupsources.list
sudo mv /etc/apt/sources.list~ /etc/apt/sources.list
```
Then do a ```
sudo apt-get update
```

---

### Post by kellemes on 2008-08-27
deleted

---

### Post by Barad on 2008-08-27
Well these lines helped, but i had to add ".d" after sources.list and now everything is perfect. :)

---

