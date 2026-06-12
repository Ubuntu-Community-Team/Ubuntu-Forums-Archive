---
title: "Intestesting: Inconsistency detected by ld.so"
date: 2009-06-06
forum: x86 64-bit Users
---

### Post by Paintrick on 2009-06-06
Hello people,

All of a sudden today i got the following message:
Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 458: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!

in my log file for apache when i tried to start apache.

and then after that quite some time later,
i tried to run zf.sh script and got the exact same message on screen
not in a logfile this time.

Anyone knows a solution?

---

### Post by beastrace91 on 2009-07-03
Hey... I have also getting this same error message when I try to run ```
sudo apt-get install samba
``` Help? I really need to get file sharing working on my Jaunty.

~Jeff

---

### Post by beastrace91 on 2009-07-06
Hey, I found a solution to this issue. Run the following two commands in terminal: ```
sudo apt-get check
sudo ldconfig -v
```

Hope this works for you as well,
~Jeff

---

