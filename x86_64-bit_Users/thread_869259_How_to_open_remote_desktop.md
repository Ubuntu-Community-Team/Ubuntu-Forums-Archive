---
title: "How to open remote desktop"
date: 2008-07-24
forum: x86 64-bit Users
---

### Post by gretarsson on 2008-07-24
Hi I have 2 pc A and B (both running ubuntu 8.04) on local net but if I try to connect B I always got close connect I have no extra firewall and both with same port (5900) mark with allow remote connect.I have try find pc on local net and command number and ip address nothing works what more do I need to do?
Thanks

---

### Post by ptn107 on 2008-07-24
You have done System -> Preferences -> Remote Desktop and configured it?  On the general tab make sure 'Ask you for confirmation' is unchecked.  On the Advanced tab make sure 'Only allow local connections' is unchecked and 'Require encryption' is checked.

Are you using Applications -> Internet -> Remote Desktop Viewer to connect? or the command line?

---

### Post by gretarsson on 2008-07-26
> **ptn107 said:**
> You have done System -> Preferences -> Remote Desktop and configured it?  On the general tab make sure 'Ask you for confirmation' is unchecked.  On the Advanced tab make sure 'Only allow local connections' is unchecked and 'Require encryption' is checked.

Are you using Applications -> Internet -> Remote Desktop Viewer to connect? or the command line?

Hi I am using Applications -> Internet -> Remote Desktop but I always com into close connect/port I thing it have some thing do do about my rouder firewall if port 5900 is open or not.
but if I go in remote desktop / connect /find then I got up list of all users on localnet but all I got is connection to host was closed.

---

### Post by cariboo on 2008-07-27
Go to System-->Administration--Network Tools and click on the scan tab, enter the ip address of the computer you are trying to connect to, it will show if port 5900 is open or not. If it is not go to the computer and make sure the remote desktop server is setup and running.

JIm

---

