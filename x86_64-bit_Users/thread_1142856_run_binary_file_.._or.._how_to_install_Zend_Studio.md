---
title: "run binary file .. or.. how to install Zend Studio"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by echo47 on 2009-04-29
Hi all, I'm attempting to  install Zend Studio for Eclipse, I've downloaded the binary installer file (apparently it's some sort of EasyInstall executable made from Java) and when I try to execute it, nothing seems to happen:

```
jon@mabel:/usr/local/bin$ sudo sh ZendStudioForEclipse_6_1_2.bin 
jon@mabel:/usr/local/bin$ sudo ./ZendStudioForEclipse_6_1_2.bin 
jon@mabel:/usr/local/bin$ 

```

I think I've got the permissions set correctly to make the file executable.. I've also installed some 32bit compatibility libraries but I can't even get to the point where it starts spewing java errors.. any output at all would be a huge victory.  Sorry if this is a noob question, I'm pretty new to system administration in Linux. 
Thanks for any assistance

---

### Post by AvatarKava on 2009-05-07
Hi Echo,

I'm going to assume you're on Jaunty amd64 desktop.

First of all, you don't want to be running the Zend installer as root via sudo.  It's going to cause you a ton of problems - since the installer is running as root, most of the installed files will only be accessible to root (no good if you're logged in to your window manager with a different user).

Second, I would advise against placing the installer into /usr/local/bin in order to install it.  To draw an analogy to windows, that would be equivalent to placing an .exe installer into c:\windows\system32 in order to run the install.  It really won't 'hurt' anything, but you're no worse off than if you install from your desktop or home directory. By default, Zend will install into your /home/USERNAME/Zend directory.

Make sure you have both of the following packages installed:
```

> sudo apt-get install libc6-i386 ia32-libs

```

You did mention compatibility packages, but these two are the ones you really need to get Zend's installer running.

After that, make sure you have proper permissions to install with your user using chmod.

Feel free to PM me if you're still having issues after you install the packages above and fix the permissions on the installer.

---

### Post by sinu_reddi@yahoo.co.in on 2009-07-09
Hi avatar,
 
can you please tell what needs to be done in case of Jaunty i386 desktop!!
 
Thanks in advance..
 
Best Wishes,
Srini

---

