---
title: "big issues installing outkafe"
date: 2007-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicoladimaria on 2007-05-07
outkafe is an opensource suite to handle internetcafe. 
I'm trying to install it in my ubuntu 64 7.04 but I get this error
```
nicola@nicola-desktop:~$ sudo sh outkafe-linux-5.0.0.run
Verifying archive integrity... All good.
Uncompressing OutKafe Installer: Linux.........................
        libglib-1.2.so.0 => not found
        libgdk-1.2.so.0 => not found
        libgtk-1.2.so.0 => not found
        libgdk_pixbuf.so.2 => not found
        libpq.so.4 => not found
./installergui: error while loading shared libraries: libglib-1.2.so.0: wrong ELF class: ELFCLASS64

```

thanks

---

### Post by Kilz on 2007-05-07
> **nicoladimaria said:**
> outkafe is an opensource suite to handle internetcafe. 
I'm trying to install it in my ubuntu 64 7.04 but I get this error
```
nicola@nicola-desktop:~$ sudo sh outkafe-linux-5.0.0.run
Verifying archive integrity... All good.
Uncompressing OutKafe Installer: Linux.........................
        libglib-1.2.so.0 => not found
        libgdk-1.2.so.0 => not found
        libgtk-1.2.so.0 => not found
        libgdk_pixbuf.so.2 => not found
        libpq.so.4 => not found
./installergui: error while loading shared libraries: libglib-1.2.so.0: wrong ELF class: ELFCLASS64

```

thanks

It looks like OutKafe is a 32bit application. You have a choice. You can either compile a 64bit version. Or you can follow the[ instructions I gave]("http://ubuntuforums.org/showpost.php?p=2609434&postcount=2") in a post with a similar error to try and make the 32bit version run.

---

### Post by nicoladimaria on 2007-05-07
> **Kilz said:**
> Or you can follow the[ instructions I gave]("http://ubuntuforums.org/showpost.php?p=2609434&postcount=2") in a post with a similar error to try and make the 32bit version run.
damn ... looks like it's working.
I'll let you know

EDIT: It works !!!

---

### Post by Cappy on 2008-01-05
You can speed this up with getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and use
```
sudo getlibs -l libglib-1.2.so.0 libgdk-1.2.so.0 libgtk-1.2.so.0 libgdk_pixbuf.so.2 libpq.so.4
```

If you need 64-bit libraries instead you can use
```
sudo getlibs -64 -l libglib-1.2.so.0 libgdk-1.2.so.0 libgtk-1.2.so.0 libgdk_pixbuf.so.2 libpq.so.4
```

---

### Post by Kilz on 2008-01-05
Yes they could, if anyone was still following this thread, Its quite old. Back then Im not sure I had even tried your great script, getlibs should be a default package on the 64bit version.

---

### Post by Cappy on 2008-01-05
> **Kilz said:**
> Yes they could, if anyone was still following this thread, Its quite old. Back then Im not sure I had even tried your great script, getlibs should be a default package on the 64bit version.

Someone IMed me about it so I thought I would update this thread a bit. Getlibs wasn't out at the time you made that post.

---

### Post by Script Warlock on 2008-01-05
heres from CAPPY! thanks alot and it helps very much... more power to you guys...:guitar:

Re: outkafe
Quote:
Originally Posted by boyet
do you have any guide for me on how to install outkafe for my ubuntu gibbon? i haven't decided yet on what type of processor i'll be using for my internt cafe this coming february..but sure enough ubuntu is my server..


Download [http://outkastsolutions.co.za/outkas...d=13&Itemid=31](http://outkastsolutions.co.za/outkas...d=13&Itemid=31)
Extract outkafe-linux-5.2.3-x86_64.run.bz2
Change to the directory in terminal and run
Code:

sudo sh outkafe-linux-5.2.3-x86_64.run

If you get library errors try getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
Code:

sudo getlibs -64 -l libraryname.so.1 anotherlibrary.so.2

if that doesn't work and it needs 32-bit libraries instead use
Code:

sudo getlibs -l libraryname.so.1 anotherlibrary.so.2

---

### Post by Script Warlock on 2008-01-06
> **Kilz said:**
> Yes they could, if anyone was still following this thread, Its quite old. Back then Im not sure I had even tried your great script, getlibs should be a default package on the 64bit version.kilz what about setting up the database for outkafe which called schema how will i intall it to the pgadmin3 i hve created the database a.k.a mydb and now don't know how to add ths schema to pgadmin

---

