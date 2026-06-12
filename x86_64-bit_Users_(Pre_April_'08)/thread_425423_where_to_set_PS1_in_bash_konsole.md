---
title: "where to set PS1 in bash konsole??"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by santana on 2007-04-27
Hi I would like to change my PS1 bash environment  variable. I tried to make the changes in 

/etc/profile
/etc/bash.bashrc
~bashrc

but didn't affect the konsole. The question is where is the bash configuration file for konsole??

---

### Post by sessine on 2007-04-27
You should see the changes the next time you start a shell, or you could do ```
source ~/.bashrc
``` to force the change on your current shell

[Edit] just noticed that you said ~bashrc, this should be .bashrc in your home area, not bashrc in /home.  This gets read last (as far as I know) so you should only need to edit this one. [/Edit]

---

### Post by santana on 2007-04-27
oh yeah, I chekced and I had put my PS1 command at the top of ./bashrc and so code bellow it was just resetting it. ooops that was stupid. thanks.

---

### Post by bashologist on 2007-04-27
> **santana said:**
> ~bashrc
> **santana said:**
> ./bashrc
```
foo@bar:~$ file ~bashrc
~bashrc: ERROR: cannot open `~bashrc' (No such file or directory)
foo@bar:~$ file ./bashrc
./bashrc: ERROR: cannot open `./bashrc' (No such file or directory)
foo@bar:~$ file .bashrc
.bashrc: ASCII English text
foo@bar:~$ 

```The file is actually located ~/.bashrc n_n

---

