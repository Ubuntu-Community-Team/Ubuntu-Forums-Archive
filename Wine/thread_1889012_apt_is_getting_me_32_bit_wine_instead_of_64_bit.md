---
title: "apt is getting me 32 bit wine instead of 64 bit"
date: 2011-11-30
forum: Wine
---

### Post by mathgirl on 2011-11-30
Hi, I was going nuts about ```
-ksh: wine: not found [No such file or directory]
``` every time I try to run wine, even though
```

macubuntu$ which wine
/usr/bin/wine

```

Then I realized
```

macubuntu$ file $(which wine)
/usr/bin/wine: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```
wine is the only 32-bit executable in /usr/bin

How to I trick apt into getting me the correct version of wine?

---

### Post by Tweak42 on 2011-12-01
It should be 32bit.  Wine64 is experimental.  It's rather tricky to explain, try reading the wiki entry here:

[http://wiki.winehq.org/FAQ#head-b89ca9d7cdf2bc2ddfb23b3e5829219df48524f8](http://wiki.winehq.org/FAQ#head-b89ca9d7cdf2bc2ddfb23b3e5829219df48524f8)

---

### Post by mathgirl on 2011-12-01
The wiki seems to imply that I should be able to get away with the 32-bit binaries apt gets me.  So why can't I execute wine?  :confused:

---

### Post by jacksaff on 2011-12-01
Wine needs an argument.
Try 'wine --help' for example.
To run a windows program you need to enter 
wine /path/to/my/program.exe

---

### Post by mathgirl on 2011-12-01
I don't think I'd get that error from the shell if wine were found but wine itself complained.  Regardless, same behavior with an executable fed to wine:

```

macubuntu$ file notepad.exe 
notepad.exe: PE32 executable for MS Windows (GUI) Intel 80386 32-bit
macubuntu$ wine notepad.exe 
-ksh: wine: not found [No such file or directory]
macubuntu$ 

```

---

### Post by jacksaff on 2011-12-01
You need to tell wine where to find notepad.exe
If your shell session is currently in the same directory as notepad.exe then your command will work. Otherwise you need to include the path to notepad.exe so wine can find it to run it.
If it's in /home/yourusername/desktop for example you run it with
wine /home/yourusername/desktop/notepad.exe

---

### Post by mathgirl on 2011-12-01
That's why I started with
```

macubuntu$ file notepad.exe 
notepad.exe: PE32 executable for MS Windows (GUI) Intel 80386 32-bit

```
to demonstrate that notepad.exe was in the current working directory.  'file' isn't any better at finding things than 'wine' should be :)

---

### Post by mathgirl on 2011-12-01
Is there a way to retitle this post?  I should probably name it

-ksh: wine: not found [No such file or directory]

since I was wrong in thinking the 32-bitness was the problem.

---

