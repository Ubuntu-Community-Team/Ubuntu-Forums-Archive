---
title: "Error while updating - corrupt dependency info for gcc-4.3"
date: 2009-01-30
forum: x86 64-bit Users
---

### Post by s13_mills on 2009-01-30
Hi all,

Had trouble today while updating - I normally update packages one by one so as if I have any trouble installing I have a shorter distance to go back, anyway, today when I updated some packages related to gcc-4.3, it removed gcc-4.3 and will not reinstall, saying it needs gcc-4.3 base version =87b333. This is wrong, as I have checked on the Ubuntu website, and it says it should need gcc-4.3-base version = 4.3.2-1ubuntu12. I imagine the file where the information regarding this dependency has gotten corrupt (no idea how/why!) but I'm pretty sure if I can just edit it out, it will reinstall fine.

My machine is usable without gcc-4.3, but I can't install packages like build-essential, which I may need in the future.
aptitude show gcc-4.3 tells me it needs =87b333, but /var/lib/dpkg/available has the right version dependency.

So I guess my question is, where is the file I need to edit?! Any and all help appreciated, thanks in advance! I am using Ubuntu 8.10 64-bit with latest kernel from repos.

---

### Post by s13_mills on 2009-01-30
Solved it - removed the updates repository from my list (just unhecked it in Synaptic, could have removed/commented it in sources.list) ran apt-get update, put the updates repository back in my list then ran apt-get update again. After that, I was able to install gcc-4.3 and the other things I wanted with no trouble.

---

