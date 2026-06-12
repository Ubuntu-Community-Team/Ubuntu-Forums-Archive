---
title: "wine in the terminal"
date: 2008-09-01
forum: Wine
---

### Post by eman7613 on 2008-09-01
okay, so to run a program you do "wine something.exe", but is there a way to tell the terminal to use wine to open exe's so that "./something.exe" would just run? similar to how "./something.bin" would launch that application.

---

### Post by loboc on 2008-09-01
You could write a script for each exe you use if you have more that 3  i could see it not being worth it but 

```

#!/bin/bash
wine foo.exe

```

save that as foo.win 

then in the terminal 

chmod +x ./foo.win

to make it executable

---

### Post by aoanla on 2008-09-01
The problem you're having is conceptual - the terminal doesn't /open/ anything - it executes commands. Since Windows executables can't be executed directly by the kernel...

---

### Post by eman7613 on 2008-09-01
> **aoanla said:**
> The problem you're having is conceptual - the terminal doesn't /open/ anything - it executes commands. Since Windows executables can't be executed directly by the kernel...

bash isnt part of the kernal either, its a program, jut like wine just like bin files just like the exes im trying to turn. what i want to know if there is a way to configure or edit bash to automatically use wine if i point it at an exe.


@loboc
im going to be running lots of exes from the commandline, so thats probably going to be more work then the inconvinves of adding the word wine

---

### Post by aoanla on 2008-09-01
> **eman7613 said:**
> bash isnt part of the kernal either, its a program, jut like wine just like bin files just like the exes im trying to turn. what i want to know if there is a way to configure or edit bash to automatically use wine if i point it at an exe.

No, because you are missing the point. Bash knows how to run ELF binaries, and how to follow instructions in scripts.
It doesn't know how to run some random exe file.

---

### Post by loboc on 2008-09-01
the hacky way to do it would be hacking around in the .bash_profile startup script in your ~ directory and some how piping all your command through grep and conditionally tacking wine on to the fron of them when .exe is inthere. I dont know if its even possible

---

