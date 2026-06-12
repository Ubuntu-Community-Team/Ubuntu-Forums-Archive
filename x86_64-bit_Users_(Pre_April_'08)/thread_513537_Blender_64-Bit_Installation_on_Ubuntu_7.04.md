---
title: "Blender 64-Bit Installation on Ubuntu 7.04"
date: 2007-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by onering on 2007-07-30
I'm using Ubuntu 7.04 64-bit.

What is the best way to install Blender3D 64-bit on my AMD X2 system?

1) Pakcage Manager (I think this will install the 32 bit versions?)
2) Use the install file from the Blender Site: [http://www.blender.org/download/get-blender-64-bits/](http://www.blender.org/download/get-blender-64-bits/)
3) Use the AMD 64-bit install .deb file from here: [http://packages.debian.org/stable/graphics/blender](http://packages.debian.org/stable/graphics/blender) 

Thanks.

---

### Post by Kilz on 2007-07-30
> **onering said:**
> I'm using Ubuntu 7.04 64-bit.

What is the best way to install Blender3D 64-bit on my AMD X2 system?

1) Pakcage Manager (I think this will install the 32 bit versions?)
2) Use the install file from the Blender Site: [http://www.blender.org/download/get-blender-64-bits/](http://www.blender.org/download/get-blender-64-bits/)
3) Use the AMD 64-bit install .deb file from here: [http://packages.debian.org/stable/graphics/blender](http://packages.debian.org/stable/graphics/blender) 

Thanks.

I would say the installer from the blender site. Your right the one in the repos is 64bit, and while its probably safe, a debian package may have issues.

---

### Post by zsouthboy on 2007-07-30
The 64-bit package will install automatically from Add/Remove Programs.

Note that 2.45 will be out shortly, and I've found that the package doesn't get updated right away (a few weeks at most).

---

### Post by stmiller on 2007-07-30
I think there may be a more recent version in Feisty-Backports.

Add/Remove>Prefs>Updates>check Feisty-Backports

---

### Post by onering on 2007-07-31
> **zsouthboy said:**
> 
Note that 2.45 will be out shortly, and I've found that the package doesn't get updated right away (a few weeks at most).

Do you mean that the 64-bit version from the Blender site does not get updated right away upon a new blender release?

---

### Post by jespdj on 2007-07-31
**NOTE!** Blender version 2.43, which is the version in the 64-bit Ubuntu repository (AFAIK), does **NOT** work correctly when compiled in 64-bit.

**Download the 64-bit version of Blender 2.44 from the Blender website.**
Do **NOT** use the 64-bit Blender 2.43 in the Ubuntu repository.

I have filed an Ubuntu bug report about this some time ago. At the time of Blender 2.43 it was well-known that it was not 64-bit safe and if you really wanted to compile a 64-bit version of Blender 2.43 you had to set a flag named "I_AM_STUPID" or something like that.

For some reason somebody decided to call himself stupid and he built a broken 64-bit Blender 2.43 and put it in the Ubuntu repository...

One of the known problems with 64-bit Blender 2.43 is that when you save files with it (with your 3D models), those files are not compatible with other versions of Blender.

---

### Post by onering on 2007-07-31
> Download the 64-bit version of Blender 2.44 from the Blender website.

OK, Thanks, I'll us the 64-bit version from the Blender website.  Any tips/tricks on installing it?

---

### Post by zsouthboy on 2007-07-31
I didn't make myself clear :)

1) Blender package in the ubuntu repositories is usually a few weeks behind. The blender website is obviously up-to-date, always.
2) Note that 2.43, indeed, is not 64-bit safe. (In fact, run blender from the console - the "YESIAMSTUPID" macro that is compiled in, prints to the console output informing you of this fact.) 2.44 and beyond are 64-bit safe - you may share .blend files between 32 and 64 bit hosts with no issue.
3) To install from the Blender website: unpack to a directory.
That's it. You can add it to your path, etc, if you want, but it is statically compiled, and requires no installation.

---

### Post by onering on 2007-08-01
I've downloaded 64-bit Blender from the Blender Website.  

1) I realize that I can uncompress the Blender program files and run them from anywhere.  However, to keep my Linux install clean, where is the preferred place to uncompress and place these types of programs?  /etc/blender?

2) How do you add the Blender program to the Applications|Graphics menu?

Thanks.

---

### Post by onering on 2007-08-02
Anyone?

1) Where is the preferred place to uncompress and place these types of programs? /etc/blender?

2) How do you add the Blender program to the Applications|Graphics men.

Thanks,

---

### Post by Kilz on 2007-08-02
> **onering said:**
> Anyone?

1) Where is the preferred place to uncompress and place these types of programs? /etc/blender?

2) How do you add the Blender program to the Applications|Graphics men.

Thanks,

1. I usualy place things added into /usr/local/NameOfApplication. That would be for users, on the local machine.

2. Im on Dapper, it has the alacarte menu editor. But I think I think Edgy and Feisty has a menu editing thing in System, Preferences.

---

### Post by stmiller on 2007-08-02
**[SIZE="4"]Blender 2.44 for 64bit is in Feisty Backports.[/SIZE]**

Just add Feisty Backports to your sources.list

```
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
```


:popcorn:

---

