---
title: "wine"
date: 2008-10-31
forum: Wine
---

### Post by j d on 2008-10-31
how to uninstall wine

---

### Post by lH)4~mK0e on 2008-10-31
Go to a terminal:

```

sudo apt-get install wine

```

---

### Post by Bakon Jarser on 2008-10-31
go to terminal

```
sudo apt-get remove wine
```

---

### Post by lH)4~mK0e on 2008-10-31
Oh yes, uninstall.  Guess I read to fast.

If you need to remove the directory wine created (and any files in that directory including applications you installed):

```

sudo apt-get remove --purge wine

```

Note:  This will remove EVERYTHING you have put in your .wine directory.

---

### Post by j d on 2008-11-01
> **miwarlock002 said:**
> Oh yes, uninstall.  Guess I read to fast.

If you need to remove the directory wine created (and any files in that directory including applications you installed):

```

sudo apt-get remove --purge wine

```

Note:  This will remove EVERYTHING you have put in your .wine directory.

jan@jan-desktop:~$ sudo apt-get remove --purge wine
[sudo] password for jan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
it is installed alricht but the above is the answer maybe it was installed  from the web thank you

---

### Post by aoanla on 2008-11-01
..what do you mean "installed from the web"? The origin of the installation is irrelevant - what would matter is if it was installed from a .deb file (and therefore managed by apt/dpkg) or if you compiled it from source and installed it with something like "make install", in which case it isn't.

I assume, since apt has no record of ever installing it, that you did the latter?

---

### Post by j d on 2008-11-01
so i did do the latter from a source file but how can i uninstall it 
is the question thank you

---

### Post by david_kt on 2008-11-01
> **j d said:**
> so i did do the latter from a source file but how can i uninstall it 
is the question thank you

Open terminal and go to the top directory of the source code, where you install wine before. Uninstall using below command:
```

sudo make uninstall
```

DK

---

### Post by cogadh on 2008-11-01
> **miwarlock002 said:**
> Oh yes, uninstall.  Guess I read to fast.

If you need to remove the directory wine created (and any files in that directory including applications you installed):

```

sudo apt-get remove --purge wine

```

Note:  This will remove EVERYTHING you have put in your .wine directory.
Running that command just removes Wine and purges all of the install files (if Wine was installed from a .deb package), it does nothing to the .wine directory in your home directory. If you choose to reinstall Wine, everything you have already used Wine for will still be available to the new installation. If you want to remove the .wine directory, you need to run a separate command in your home directory:
```
rm -rf .wine
```

---

