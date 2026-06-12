---
title: "can't run update manager"
date: 2008-05-24
forum: x86 64-bit Users
---

### Post by brunoscunha on 2008-05-24
For some days now the update manager icon, just next to the network icon is sending this msg: A problem occurred when checking for updates
I can't run the update manager, nothing happens, only from the console.
Could this be from a broken update, how can I correct this?

Thanks you

---

### Post by Sef on 2008-05-24
From the terminal: (Applications > Accessories > Terminal)

type this command:

```
sudo apt-get update
```

If that works, then type this command:

```
sudo apt-get upgrade
```

If you get any errors, please post them.

---

### Post by brunoscunha on 2008-05-25
I've tried both, no errors. It's when I do a mouse over on the update icon it gives that message. 
All that's connected with update manager, I can't run. This also happens when I log in as root too.
This happened suddenly.I did not go messing around with hardy. My guess is it has something to do with a broken update

---

### Post by Sef on 2008-05-25
Can you upgrade via Synaptic?  System > Administration > Synaptic Package Manager > Mark All Upgrades > Apply

---

### Post by brunoscunha on 2008-05-25
Yes that I can do, but clicking on preferences, editing software sources, show updates etc, nothing happens

---

