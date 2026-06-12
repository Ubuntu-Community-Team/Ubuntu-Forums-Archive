---
title: "How to install 32-bit libraries on a 64-bit system?"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by M. Trident on 2008-11-24
I recently upgraded our server from 32-bit to 64-bit Ubuntu 8.04.  However, when I tried to reinstall a critical piece of software, I discovered that it isn't supported in a 64-bit OS.  After talking with the software's customer support, they assured me that it was still possible to get it to install (as others have), but that I would first need to install 32-bit X11 libraries for it to link against.

I googled and searched the Ubuntu forums but I wasn't able to find anything about how I might do this.  I didn't see any way to get 32-bit versions using apt-get either.  I could be missing something obvious though, as I am more of a linux user than an admin.  Does anyone have any suggestions or points on how to do this?

---

### Post by xebian on 2008-11-24
> **M. Trident said:**
> I recently upgraded our server from 32-bit to 64-bit Ubuntu 8.04.  However, when I tried to reinstall a critical piece of software, I discovered that it isn't supported in a 64-bit OS.  After talking with the software's customer support, they assured me that it was still possible to get it to install (as others have), but that I would first need to install 32-bit X11 libraries for it to link against.

I googled and searched the Ubuntu forums but I wasn't able to find anything about how I might do this.  I didn't see any way to get 32-bit versions using apt-get either.  I could be missing something obvious though, as I am more of a linux user than an admin.  Does anyone have any suggestions or points on how to do this?

There is the ia32-libs package which has some but not all the 32-bit libs.  In such case you need to install them manually into the /usr/lib32 directory.  You can search for packages that has '32' in their name , or has 'i386'.  Hope this helps.

---

### Post by stmiller on 2008-11-25
Yeah install all of the ia32* packages.

Then you can install and run most any 32bit software like google earth, picasa, skype, etc.

:popcorn:

---

### Post by Kilz on 2008-11-25
[Getlibs]("http://ubuntuforums.org/showthread.php?t=474790") is the solution for any 32bit libs not in ia32* packages.

---

### Post by Krupski on 2008-11-25
> **M. Trident said:**
> I recently upgraded our server from 32-bit to 64-bit Ubuntu 8.04.  However, when I tried to reinstall a critical piece of software, I discovered that it isn't supported in a 64-bit OS.  After talking with the software's customer support, they assured me that it was still possible to get it to install (as others have), but that I would first need to install 32-bit X11 libraries for it to link against.

I googled and searched the Ubuntu forums but I wasn't able to find anything about how I might do this.  I didn't see any way to get 32-bit versions using apt-get either.  I could be missing something obvious though, as I am more of a linux user than an admin.  Does anyone have any suggestions or points on how to do this?

Geez... everyone makes it so difficult.

Just type this at a command line:

```

sudo apt-get -V install ia32-libs

```

It will install all the stuff you need to run 32 bit apps in 64 bit Linux. You will notice that a new directory named "lib32" appears in your root directory... FWIW.

-- Roger

---

