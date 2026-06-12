---
title: "expert-level file-type association"
date: 2015-08-04
forum: Wine
---

### Post by xuancong84 on 2015-08-04
I have installed Wine1.7. I realize that if I chmod an EXE file as executable, and run it in a terminal using "./test.exe", it will automatically invoke wine to load the program and run it.
1. How is this kind of file association achieved? I changed /usr/bin/wine into some other executable program (call it ProgramA), now when I run "./test.exe", it says "cannot execute binary file: Exec format error", however, ProgramA is not executed at all. So obviously, this kind of file association is done inside /usr/bin/wine itself.

2. I want to run every EXE file using "LC_ALL=zh_CN.UTF-8 wine" instead of just "wine". How to do it?
The following solution does not work:
mv /usr/bin/wine /usr/bin/wine-orig
echo "LC_ALL=zh_CN.UTF-8 /usr/bin/wine-orig $*" >/usr/bin/wine
I thought shell-level or MINE-level file association is such that whenever an EXE file is to be executed, /usr/bin/wine is launched. However, it is not that simple.
Apparently, changing the content of the binary executable /usr/bin/wine breaks the EXE file association.

---

### Post by TheFu on 2015-08-04
It isn't wine - it is bash.
I would just set this environment varialbe inside my ~/.bashrc file:
```
export LC_ALL=zh_CN.UTF-8
```

This link explains how to modify .. 
[https://stackoverflow.com/questions/10942919/customize-tab-completion-in-shell](https://stackoverflow.com/questions/10942919/customize-tab-completion-in-shell) explains more.

BTW - Linux doesn't use extensions. It uses the "magic number" at the beginning of files to determine a file type.  Use the "file" program to query the type of any file.  Bash has a completion-module that will use extensions to help complete commands using a {tab}. Don't think that is related to this at all. This package may not be installed on all systems.

For example:
```
$ file /bin/bash 
/bin/bash: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=4ead65aeca4e9f1eabf3a0d63eb1f96c225b25fd, stripped
```

This system is running 3.16.0-45-generic kernel on Ubuntu 14.04.2 LTS.

Having the background will be useful to setting expectations.

---

### Post by xuancong84 on 2015-08-04
I do know the export command.
I have "export LC_ALL=en_US.UTF-8" in my .bashrc file. I need to keep "export LC_ALL=en_US.UTF-8"  so that other program can function properly.
In other words, I would like to implement a wine wrapper which particularly deals with EXE files. And I want my wrapper to be called when EXE files are executed.

Your solution is what I already know and does not solve my problem.

---

### Post by TheFu on 2015-08-05
Did you actually read the linked solution?

---

### Post by xuancong84 on 2015-08-05
Yes, of course, I have read your link.

Unfortunately, your link is talking about something else. And that one has nothing to do with the wine executable itself. See the difference:
1. For bash completion, if I modify /usr/bin/wine, "wine <tab><tab>" still lists only .exe files, because it's handled by the "bash completion package", and changing the wine executable does not touch the "bash completion package setting" at all.
2. For my question, if I modify /usr/bin/wine, "./ProgramA.exe" will no longer invoke wine, and you get "cannot execute binary file: Exec format error".

In other words, the .exe file association is dynamically determined by /usr/bin/wine, not by bash or any other package, i.e.:
1. if /usr/bin/wine is the installed version, then "./ProgramA.exe" == "wine ProgramA.exe", /usr/bin/wine is invoked
2. if /usr/bin/wine is my modified version, then "./ProgramA.exe" != "wine ProgramA.exe", /usr/bin/wine is not invoked; since ProgramA.exe is not a Linux binary executable, you get "Exec format error"

Do you understand my question better now? That is why I call this thread "expert-level".

---

### Post by yoshii on 2015-08-23
It just seems like you are trying to rename wine.  How is that supposed to do anything other than mess up the system?  Of course wine can't run if you rename (and thus disable) parts that it needs to run.  Right?

---

### Post by xuancong84 on 2015-08-23
> **yoshi2 said:**
> It just seems like you are trying to rename wine.  How is that supposed to do anything other than mess up the system?  Of course wine can't run if you rename (and thus disable) parts that it needs to run.  Right?

Nope. I did not mess up the system because I just changed /usr/bin/wine into a shell script which calls "LC_ALL=zh_CN.UTF-8 <original-wine>":
mv /usr/bin/wine /usr/bin/wine-orig
echo "LC_ALL=zh_CN.UTF-8 /usr/bin/wine-orig $*" >/usr/bin/wine

Thus, if the system is as before, which simply use /usr/bin/wine to execute every EXE file, everything should work out correctly.

---

### Post by mc4man on 2015-08-23
You could probably approach from the file manager side, set your mime association for .exe to a custom .desktop that sets the env & opens wine on the target/arg1 file. Either directly in the .desktop on Exec= line or if need be via a script that is called from the Exec= line.

Or set up a diversion in /usr/bin where wine is moved to a new name (wine.real) & /usr/bin/wine is a script that sets env & calls wine.real
(I used to to that a long time ago with a couple of apps for some forgotten reason & manner, if I can [find the thread]("http://ubuntuforums.org/showthread.php?t=1771405&p=10883304&viewfull=1#post10883304")(s) about will link as I remember there were 3 files involved to do this.. (orig., script, link or something like that.

Or do both to cover both FM & cli uses if both are possible, wine isn't used here so can't say..

---

### Post by xuancong84 on 2015-08-25
> **mc4man said:**
> You could probably approach from the file manager side, set your mime association for .exe to a custom .desktop that sets the env & opens wine on the target/arg1 file. Either directly in the .desktop on Exec= line or if need be via a script that is called from the Exec= line.
You haven't understood my question correctly. Please re-read my post and every reply before you think you can answer.

> **mc4man said:**
> Or set up a diversion in /usr/bin where wine is moved to a new name (wine.real) & /usr/bin/wine is a script that sets env & calls wine.real
Exactly what I have tried in reply #7, it doesn't work.

---

### Post by yoshii on 2015-09-06
why are you chmodding EXEs?  EXE's aren't linux executables, so chmodding them for execution isn't likely to result in much of anything?  
i really don't understand how this is all "expert".  wine works OK, seems like you are confusing it and puzzled why it doesn't work as intended.

---

