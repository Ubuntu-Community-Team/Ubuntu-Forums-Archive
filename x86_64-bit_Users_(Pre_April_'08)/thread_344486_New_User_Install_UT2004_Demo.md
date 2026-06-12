---
title: "New User Install UT2004 Demo ?"
date: 2007-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Red06C6 on 2007-01-23
Hello all.  I just built a 64-bit machine and installed ubuntu 6.10 64-bit without a hitch.

I really don't know Unix or Linux commands at all, so I'm relying on the GUI, which so far has been pretty good.

Here's my problem(s): Any help is appreciated, and I appreciate the patience!

First the system says that there are available updates, and when I click the install button I get this message: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I'm totally lost.

Also I downloaded the UT2004 64-bit demo.  It created a folder on the desktop, but I have no idea how to install it.  Any step by step suggestions?

Many Thanks!:D

---

### Post by pay on 2007-01-23
Do as the output says. Open the terminal and type```
sudo dpkg --configure -a
```To install the demo```
sh UT200464-bit.sh
```should open a iinstallation box similar to windows.

---

### Post by Red06C6 on 2007-01-23
Thanks you for the help!  I really appreciate that.  The system updates went in fine.

1 more question please for the UT2004 64-Bit demo:

red06c6@red06c6-desktop:~$ sh UT200464-bit.sh
sh: Can't open UT200464-bit.sh

What I have on my desktop is: 

/home/red06c6/Desktop/ut2004Demo/ut2004-lnx64-demo-3120.run

This is like learning a foreign language for me...So far though I'm impressed with ubuntu!:D 

Any guidance is appreciated.

---

### Post by janfsd on 2007-01-23
First you need to type (you should be in the folder where the installer is):
```
chmod +x ut2004-lnx64-demo-3120.run
```
and finally:
```
./ut2004-lnx64-demo-3120.run
```

---

### Post by dmn_clown on 2007-01-23
> **janfsd said:**
> First you need to type (you should be in the folder where the installer is):
```
chmod +x ut2004-lnx64-demo-3120.run
```
and finally:
```
./ut2004-lnx64-demo-3120.run
```

or you could just skip the permissions modding and do a 

```
sh ut2004-lnx64-demo-3120.run
```

Why make something executable when it doesn't need to be?

---

