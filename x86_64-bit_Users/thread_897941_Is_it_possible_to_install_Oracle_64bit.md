---
title: "Is it possible to install Oracle 64bit?"
date: 2008-08-22
forum: x86 64-bit Users
---

### Post by MickSulley on 2008-08-22
Hi,
I'm trying to install Oracle 10g 64 bit 10g 10.2.0.1.0 on Ubuntu Hardy.  is this possible? I am hitting an error -
Error in invoking target 'install' of makefile
'/home/mick/oracle/product/10.2.0/db_1/ctx/lib/ins_ctx.mk'* See
'/home/mick/oraInventory/logs/InstallActions2008-08-16_02-18-22PM.log' for details

Is there a solution to this or should I just give up and install 32 bit?

Thanks
Mick

---

### Post by Sef on 2008-08-22
Have you installed build-essential?

```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by MickSulley on 2008-08-23
I ran that and then tried the install again and got the same error.

Any other ideas?

Thanks
Mick

---

### Post by Nepherte on 2008-08-23
There exists a i386 package here: [http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html](http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html)

Maybe you can try to force to install it by:
```
sudo dpkg -i --force <packagename>
```
I have to warn you about --force though. This is what the man page says about it:
```
Warning:  These options are mostly intended to be used by
          experts only.  Using  them  without  fully  understanding
          their effects may break your whole system.
```

If you don't want to risk it, you can continue reading with this page: [http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm](http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm)

Oracle isn't really debian based distro nor 64 bit friendly. It took me *a lot of time* to install the full oracle 11g database on ubuntu 64bit. If oracle is important for you, I suggest red hat/fedora based distros.

edit: it's also worth taking a look at that log file for more information:
```
view /home/mick/oraInventory/logs/InstallActions2008-08-16_02-18-22PM.log
```

---

### Post by jespdj on 2008-08-25
> **MickSulley said:**
> See
'/home/mick/oraInventory/logs/InstallActions2008-08-16_02-18-22PM.log' for details
Did you look in the log file as is suggested? What messages do you see there?

---

### Post by MickSulley on 2008-08-28
Hi,
Sorry for the delay in replying.  I have looked at the log file and cannot see anything that helps, but I would appreciate another opinion.

I have tarred the log file and attached it.

Thanks for your help

Mick

---

