---
title: "Hide partiton"
date: 2008-08-02
forum: x86 64-bit Users
---

### Post by vikrant_me on 2008-08-02
I am the primary user on my machine, i would like to hide my partition from the following commands:

* df -lh
* mount 
* The places menu in the taskbar which lists mounted partitions

---

### Post by Rocket2DMn on 2008-08-03
I don't think you can hide partitions, but you can set it up so that they don't automatically mount.  This is achieved by adding the "noauto" option to the fstab entry of the corresponding partition.

---

### Post by cariboo on 2008-08-03
If you are worried about other people using your computer, create a separate user for for other people, set it up so that they can auto login and set them up as a limited user, check out System-->Administration-->Users and Groups. Click Add User enter the info then click User Privileges. There is a list of permissions you can set for this user. Just make sure to log out when you are finished using the computer.

Jim

---

