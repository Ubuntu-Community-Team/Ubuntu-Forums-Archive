---
title: "Gnome-RDP"
date: 2008-08-23
forum: x86 64-bit Users
---

### Post by rck1640 on 2008-08-23
I'm new to 64-bit version. I'm trying to use Gnome-RDP to connect to a school computer and I'm getting this error message: "*To logon to this remote console session, you must have administrative permission on this computer*."

I tried launching the Gnome-RDP in Terminal using sudo... but got the same result.

Any suggestions, solutions?

Thanks!

---

### Post by LateNiteTV on 2008-08-23
uuummmmm maybe you need admin access on the school computer?

---

### Post by rck1640 on 2008-08-23
I think the message refers to my Ubuntu computer. I can gain access using a KDE client in Suse. I think it thinks I don't have admin permission in Ubuntu.

How do I do that if sudo doesn't work?

---

### Post by LateNiteTV on 2008-08-23
```
sudo passwd root
```
this will allow you to activate the root acct.
```
su
```
this will make you root. try it now.

---

### Post by rck1640 on 2008-08-23
Thanks Late Night! That worked...

---

