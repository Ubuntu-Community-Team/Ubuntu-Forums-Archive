---
title: "Wine error after winecfg"
date: 2006-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by alijoe on 2006-10-11
Hello,
After installing wine with a help of HOWTO in this forum I try to config it by typing winecfg. Instead of configuration tool I recieve this:

joe@joe-desktop:~/Desktop$ winecfg
wine: creating configuration directory '/home/joe/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
wine: wineprefixcreate failed while creating '/home/joe/.wine'.
joe@joe-desktop:~/Desktop$ wineserver: could not save registry branch to /home/joe/.wine-5Doq93/system.reg : No such file or directory
wineserver: could not save registry branch to /home/joe/.wine-5Doq93/user.reg : No such file or directory

Am I doing something wrong? My PC: Motherboard K8N Neo4 Platinum -nVidia nforce4 chipset, CPU AMD athlon64 X2 4200+, 1024MB RAM.

---

### Post by Kilz on 2006-10-11
> **alijoe said:**
> Hello,
After installing wine with a help of HOWTO in this forum I try to config it by typing winecfg. Instead of configuration tool I recieve this:

joe@joe-desktop:~/Desktop$ winecfg
wine: creating configuration directory '/home/joe/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
wine: wineprefixcreate failed while creating '/home/joe/.wine'.
joe@joe-desktop:~/Desktop$ wineserver: could not save registry branch to /home/joe/.wine-5Doq93/system.reg : No such file or directory
wineserver: could not save registry branch to /home/joe/.wine-5Doq93/user.reg : No such file or directory

Am I doing something wrong? My PC: Motherboard K8N Neo4 Platinum -nVidia nforce4 chipset, CPU AMD athlon64 X2 4200+, 1024MB RAM.

If you used my [howto]("http://www.ubuntuforums.org/showthread.php?t=185557"), I suggest you read the etire howto. It looks like you didnt install the sidenet configuration script, and the rest of the error can be found in the Common Errors section.

---

### Post by alijoe on 2006-10-11
Dear Kilz
I am very sorry for not reading the whole HOWTO. It was only my mistake. After doing the whole job (installing sidenet and ATI graphic), everything was OK.
Thanks for prompt answer.

---

### Post by Kilz on 2006-10-11
> **alijoe said:**
> Dear Kilz
I am very sorry for not reading the whole HOWTO. It was only my mistake. After doing the whole job (installing sidenet and ATI graphic), everything was OK.
Thanks for prompt answer.

Its ok, we all get into a hurry sometimes. I know I do. Glad that the problems are solved now. :D

---

