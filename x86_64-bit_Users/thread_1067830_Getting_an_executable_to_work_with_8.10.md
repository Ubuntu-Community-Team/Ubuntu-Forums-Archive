---
title: "Getting an executable to work with 8.10"
date: 2009-02-12
forum: x86 64-bit Users
---

### Post by bbqpope on 2009-02-12
I will preface this and tell you that I am rather new to this.  I installed ubuntu studio, 8.10 x86 64 onto my opteron machine, and it has been slow in getting everything to work.   I can dual boot now and I am beginning to tackle my other issues.   One is scanning.  I know about xsane, but I own a license for a program called Vuescan.  I don't want to learn a new scanner app, this one is very familiar and powerful. I got a .tgz file from their site. Inside are langauge files, help text, a .dat file and an executable file, which does not load up when i double click it, nor does it seem to launch from the terminal.  Do I need 32 bit support? I have not found a suitable answer elsewhere.

---

### Post by mikewhatever on 2009-02-12
You may need to give the file executable permissions. Right click on it, select Properties, then Permission tab, and check the box next to 'Allow executing file as a program'.

---

### Post by bbqpope on 2009-02-12
> **mikewhatever said:**
> You may need to give the file executable permissions. Right click on it, select Properties, then Permission tab, and check the box next to 'Allow executing file as a program'.

I tried that, I also installed libs32 and libs5c++, and it's still not working.  

So many non functional parts a linux fan does not make. -- eergh, I have no sound, no access to my raid, there are too many things that just don't work.

---

### Post by mikewhatever on 2009-02-12
Sorry to hear that.

---

### Post by jerome1232 on 2009-02-12
> **bbqpope said:**
> I tried that, I also installed libs32 and libs5c++, and it's still not working.  

So many non functional parts a linux fan does not make. -- eergh, I have no sound, no access to my raid, there are too many things that just don't work.

details, details, details.

What's the error when you try and launch the program from a terminal, the other issues are probably best suited for seperate threads.

---

