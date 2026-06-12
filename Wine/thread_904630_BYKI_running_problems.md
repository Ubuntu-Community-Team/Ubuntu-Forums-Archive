---
title: "BYKI running problems"
date: 2008-08-29
forum: Wine
---

### Post by Homosuperior on 2008-08-29
I've been trying to get a language program that is set up for windows to work on Ubuntu 7.10. I have read that at least one person has got the program to work on Linux, even though the company does "_**NOT**_ support Linux". I have gotten as far as installation, but when I try to run the program it gives me an error stating: "No valid Langs.txt found". I have tried altering the ini file as per others having the problems on other boards, I have used the appropriate dll overrides, and am still getting the error. I am able to run it still on Windows though, so I don't believe that it would be missing anything, but I could be missing something? Would re-downloading the program possibly fix this? or is there just a step that I am missing in the set up?
Thanks in advance!

---

### Post by cboteros on 2009-08-29
Hello, this is "exactly" and one year old tread, but I'm now also trying to run Byki on Ubuntu Jaunty.

Homosuperior, previously you mentioned:

> I have read that at least one person has got the program to work on Linux

Do you have the source from where this person got Byki running on Linux?

Or does anyone know an alternative to Byki in Linux?

---

### Post by cboteros on 2009-08-29
To answer myself on my first question, Byki 3.6 seems to be tested in Wine in 2006 working fine:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5797](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5797)

But I can't manage to make it work now, any clue anyome?

---

### Post by RabbitWho on 2010-03-06
And another six months later i'm trying the same thing and can't get it working. What did you do?

---

### Post by rossanthony on 2010-04-18
I've got the same problem. The program has installed, the .dll files are in the BYKI folder and it let's me get as far as choosing in which language to operate (and every attempt I hopefully click the "Never Ask Again" box) but then it crashes. 

Has anyone solved this yet? I confess to being a linux-newb, so it's very possible that I'm doing something wrong.

---

### Post by Ubivetz on 2010-05-14
I tried to run BYKI 4.0 with Ubuntu 7.10, 8.10 and newer.
It crashes before skin had started.

---

### Post by davegk on 2010-05-14
> **rossanthony said:**
> I've got the same problem. The program has installed, the .dll files are in the BYKI folder and it let's me get as far as choosing in which language to operate (and every attempt I hopefully click the "Never Ask Again" box) but then it crashes. 
I've setup a Lucid laptop for a friend a few days ago and she uses this BYKI software. I've got exactly same problem, as described by rossanthony here - BYKI installs fine, but on running only goes as far as language selection and that's it ... So the problem is perfectly reproducible :(

---

### Post by duke.tim on 2010-05-22
Byki 4 bulid 230 will work. You need to used winetricks add riched20 and riched32. I also needed to download iertutil.dll and rpcrt4.dll. after that use winetricks again and get urlmon. (make sure to go into wineconfig and set an override for the new dll's.

Here is the wine page I used for starting
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15086](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15086)

---

### Post by cboteros on 2010-06-18
Didn't work for me... :-(

Winde version: 1.2

How can I know the build of the Byki ? I just got the last version from their website today

---

### Post by duke.tim on 2010-09-11
I believe the latest version should work. some programs like BYKI need to have internet explorer. I would try installing ie6 from winetricks first. If that doesn't work you can try ies4linux
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

I normally have issues with installing ies4linux but using playonlinux, I can normally get it installed.

---

