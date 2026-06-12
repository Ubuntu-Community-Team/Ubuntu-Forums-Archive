---
title: "ssh_64-bit"
date: 2008-10-14
forum: x86 64-bit Users
---

### Post by coffee is the colour on 2008-10-14
I have 2 new 64-bit Dell Desktops.  I installed the ubuntu 64-bit gutsy distro on both of them, but I am having problems trying to get the 2 desktops to communicate with each other via ssh.  I had a look in the /etc/initd directory and there is no ssh file.  Would this have anything to do with the problems I'm encountering.

Any Suggestions?  Many Thanx,

---

### Post by felker2 on 2008-10-14
Use "sudo apt-get install ssh" to install the SSH-server.

After that, check with "ssh localhost"; you should be able to logon.

If that works, connect from the other machine.

HTH

---

### Post by cariboo on 2008-10-14
You need to install the **openssh-server** on at least one of the computers. Openssh-server is available in the repositories.

Jim

---

### Post by Vadi on 2008-10-14
[Click]("apt:openssh-server") to install (apt: links are lazy-friendly!)

---

### Post by felker2 on 2008-10-14
> **Vadi said:**
> [Click]("apt:openssh-server") to install (apt: links are lazy-friendly!)

Wow! Cool URL! ;-)

---

### Post by Vadi on 2008-10-14
Feel free to make use of it ;)

---

