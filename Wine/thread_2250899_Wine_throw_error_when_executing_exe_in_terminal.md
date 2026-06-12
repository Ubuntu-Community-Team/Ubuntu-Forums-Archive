---
title: "Wine throw error when executing exe in terminal"
date: 2014-10-31
forum: Wine
---

### Post by komppa97 on 2014-10-31
Hello guys!
I tried to launch setup.exe in terminal "wine setup.exe" but it throw few errors.. What you think about that?

User@User:~$ wine setup.exe 
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:client_security_SetBlanket 0x7d5d0544, 0x13a5c8, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7d5d0544
err:seh:raise_exception Unhandled exception code c0000005 flags 10 addr 0x152250a

Thanx!

---

### Post by komppa97 on 2014-10-31
In graphical version it didnot say anything and wont start

---

### Post by Mark Phelps on 2014-11-01
Unfortunately, LOTS of Windows apps run poorly, or not at all, in Wine.  Might help if you told us the app and version you're trying to use.

---

