---
title: "ubuntu 11.10 wine 1.3 buggy"
date: 2011-11-15
forum: Wine
---

### Post by cracker89 on 2011-11-15
I recently upgraded to 11.10. Almost immediately my wine (1.3 as well as 1.2) installation started acting up and programs that ran seamlessly earlier started not working and reporting bugs, like microsoft word, etc. I cannot get them to work at all.
Infact, even on opening wine configuration, the same bug reports are repeated. Is anyone else facing similar problems?

I am posting the errors I recieve as under:

# On opening the configuration panel of wine, I recieve the following error:
```
EXCEPTION RAISED
Unhandled page fault on read access to 0x7aeeaa70 at address 0x7aeeaa70.
Do you wish to debug it?
[Yes][No]

```

It tells me that services.exe has crashed and needs to close.

A similar error/series of errors ensue on opening any application installed in wine. 

I have tried to uninstall and reinstall, reinstall wine multiple times. Deleting the .wine directory has also not helped to resolve the program. 

On typing ```
sudo apt-get install wine 1.3
``` in the terminal, i get the following response:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgfs-1.3-2 : Conflicts: libgfs-mpi-1.3-2 but 20110329-dfsg.2-1build1 is to be installed
 libgfs-mpi-1.3-2 : Conflicts: libgfs-1.3-2 but 20110329-dfsg.2-1build1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

Help a brother out? And Fast! :P
Thanks in advance.

---

### Post by nothingspecial on 2011-11-15
Moved to Wine.

---

### Post by Rasa1111 on 2011-11-15
Dang! 

Wish I had some knowledge to help here Cracker, my friend! 

All I can do to help is to BUMP this bad boy to the top. lol

Sorry mate, Good luck!

---

### Post by ergo-proxy on 2011-11-16
Use synaptics to repair broken packages, uninstall (with purge) wine and install it again using wine repository.

---

### Post by cpmman on 2011-11-23
Sorry mate I don't use wine (well ... not that sort) but as it's not marked solved here's a bump for you.
Good luck.

---

### Post by graphius on 2011-11-25
> **ergo-proxy said:**
> Use synaptics to repair broken packages, uninstall (with purge) wine and install it again using wine repository.

^This^
For some reason, the wine version in the Ubuntu repository is/was broken. I had to purge and reinstall, then reinstall Photoshop. I had Bridge working, but now it doesn't (might be my video card though, Maybe I will get a new one for Christmas...:)

---

### Post by ken631 on 2011-11-28
Had the same problem.  Followed suggestion on here to repair wine with synaptic and it appears when I upgraded from 11.04 to 11.10 wine 1.3 or 1.2 were never installed or updated so I had to install 1.3.  Just did it today in fact.

---

### Post by cwwilson721 on 2011-11-28
First, you need to REALLY uninstall wine, with a 'purge':
```
sudo apt-get remove --purge wine wine1.3
```(From your description, the install is a mess anyway) This WILL NOT destroy your .wine folder. All it has in it is data, not 'wine' itself. There is no reason to 'delete' it. You'd just have to reinstall whatever programs you want to run if you do so.

Next, install latest wine:
```
sudo apt-get install wine1.3
```

Then, run 'winecfg' to setup correct registry', etc, in your .wine folder:
```
winecfg
```

Let us know

---

### Post by eswald on 2011-12-08
Thank you.  I was also experiencing errors under Wine 1.3 (names in /etc/hosts not resolving, sudden crashes complaining about allocating space for X11 pixmaps, etc.) after upgrading to 11.10 Oneric.  Purging wine1.3 was about to do some nasty stuff, so I had to explicitly install ia32-libs-multiarch first.  Installing wine1.2 seems to have fixed the problems.

---

