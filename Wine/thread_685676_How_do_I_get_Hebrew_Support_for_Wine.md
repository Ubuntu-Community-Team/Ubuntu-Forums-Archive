---
title: "How do I get Hebrew Support for Wine?"
date: 2008-02-02
forum: Wine
---

### Post by arielsegal on 2008-02-02
I'm trying to run windows applications with Hebrew interface under 
wine. From reading in wine site I understood that standard binaries do 
not support Hebrew. First I must 
install ICU and then d/l the wine source. if the installation script 
identifies ICU, it will compile wine with Hebrew support. 
I'm using Ubuntu 7.10 and have d/l and installed the files: 
icu4c-3_8_1-src.tgz 
wine-0.9.53.tar.bz2 
and all its dependencies. But the installation script does not seem to 
look for ICU. Anyway, my Wine still does not support Hebrew. 
I'll be grateful for your help,

---

### Post by mosestruong on 2008-10-17
The simplest method is to install wine from the repository, and then download usp10.dll from [http://www.dlldump.com](http://www.dlldump.com), and save it to ~/.wine/drive_c/windows/system32

Then run winecfg, and in the Library tab, add usp10 to use the native library.

---

### Post by doron387 on 2009-09-01
i am trying to search in emule hebrew file names but it writes squares instead of letters.
i did everything as said but it does not change the situation.
i tried also to change emule's language to hebrew and then all the menus are written in this "squares language"
( i use emule 0.49b on ubuntu 9.04 fully updated)
it did work in pclos 2007.
any idea ? it is one of the main reasons that i can't run only ubuntu and still need the m$win.
please set me free of it.
thnx 
doronb

---

### Post by jacksaff on 2009-09-01
If you're getting squares the issue is likely to be related to fonts. Either you don't have the correct font installed or wine is not finding it.

---

### Post by nivosh on 2009-10-05
> **mosestruong said:**
> The simplest method is to install wine from the repository, and then download usp10.dll from [http://www.dlldump.com](http://www.dlldump.com), and save it to ~/.wine/drive_c/windows/system32

Then run winecfg, and in the Library tab, add usp10 to use the native library.

I need the same help.
I used the advice you gave here but still getting question marks instead of Hebrew letters in the folder and file names.

I run linux mint 7 which is based on ubuntu 9.04.

Dows my system locale need to be Hebrew inorder to use the dll?

---

### Post by orduek on 2009-11-05
OK,
that helped me - thanks.
But now I have a problem.
I installed Office2007 but when I load it the Hebrew is written in reverse.
the only way to fix it is by opening with the command LANG=he.IL.UTF-8 wine ....

How can I tell wine to use LANG=he.IL.UTF-8 every time he opens something?

---

