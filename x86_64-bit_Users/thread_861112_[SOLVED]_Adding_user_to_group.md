---
title: "[SOLVED] Adding user to group"
date: 2008-07-16
forum: x86 64-bit Users
---

### Post by scottuss on 2008-07-16
Hi all, I have a problem that when I go to System > Administration > Users and Groups.

My problem is that I cannot "unlock" the advanced settings. If I try, the password entry box wobbles as if I entered the wrong password (which I am being very careful not to do!)

If I run the applet as root or via sudo, I don't get the option to unlock the features, the button is greyed out.

I would really appreciate any help with this guys
Thanks in advnace,
Scott

---

### Post by sisco311 on 2008-07-16
try to add the user to the group from the terminal:
```
sudo addgroup **username groupname**
```
or
```
sudo usermod -a -G **groupname0,groupname1,groupname2 username**
```

---

### Post by scottuss on 2008-07-16
sisco311 you are a genius! And such a fast reply!

I knew the Ubuntu community wouldn't let me down :)


:guitar:

---

### Post by Neo Dagger on 2008-07-17
Hi
I've had this problem in the past.:confused:  took me ages to figure out why it didn't like my password.  Then I checked the keyboard layout and it had somehow changed to USA.  Put it back to Uk and lo and behold, it let me in.  I had installed compiz fusion manager stuff so I am wondering if that had changed my settings.:?

---

