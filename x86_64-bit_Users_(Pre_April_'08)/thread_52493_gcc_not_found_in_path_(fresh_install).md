---
title: "gcc not found in path (fresh install)"
date: 2005-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jakemikey on 2005-07-27
I'm running a home-built pentium D system on the AMD64-smp kernel.  I've gotten several errors while trying to compile various programs, including (paraphrasing -- I'm posting from my Mac right now)"no c compiler found - gcc not found in path".  I've checked and both gcc 3.3 and gcc 4 are in /usr/bin (which is part of the path). Typing gcc at the prompt gives a command not found.

What should I do?

Also, a perhaps unrelated point: while running configure for another program, I get an error on system/machine -- something along the lines of "x86_64-unknown-linux" not recognized, etc.

Thanks in advance,

Jake

---

### Post by bored2k on 2005-07-27
[QUOTE=jakemikey]I'm running a home-built pentium D system on the AMD64-smp kernel.  I've gotten several errors while trying to compile various programs, including (paraphrasing -- I'm posting from my Mac right now)"no c compiler found - gcc not found in path".  I've checked and both gcc 3.3 and gcc 4 are in /usr/bin (which is part of the path). Typing gcc at the prompt gives a command not found.

What should I do?

Also, a perhaps unrelated point: while running configure for another program, I get an error on system/machine -- something along the lines of "x86_64-unknown-linux" not recognized, etc.

Thanks in advance,

Jake[/QUOTE]
 1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install build-essential

---

