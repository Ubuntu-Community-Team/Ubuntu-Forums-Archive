---
title: "Monitoring mode with orinoco under Breezy PPC"
date: 2006-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by traumtaenzer on 2006-01-13
Hello!

I got a question concirning the monitoring mode for an orinoco-card under Breezy PPC. So instructions concerning hoary, I found on the wiki worked fine, I could recompile the modules and install the new drivers. After the breezy update there was still no problem, I used the instructions concerning hoary just updated the patch , so I used the patch for kernel version 2.6.12.
Now I had to reinstall Breezy on my Powerbook Pismo, but I can't get the drivers to run, the way I did before. I also tried the breezy specivic instructions, but there I just get thousands of compile errors. Has anybody got experience with this topic under PPC?

Thanks in forth, rainer

---

### Post by ssam on 2006-01-13
have you tried installing gcc 3.4 and compiling with that?

everything in breezy apart from the kernel is compiled with gcc4, but they had to do the kernel with 3.4. if you are compiling kernel stuff you should use 3.4

---

### Post by traumtaenzer on 2006-01-14
Yes I,ve installed it, because the new instructions said i should do it, but i'm not sure if it was used in the install

---

### Post by ssam on 2006-01-14
you might have to change the simlinks in /usr/bin/

have a look at
```
ls -l /usr/bin/gcc*
```
i get
```
lrwxr-xr-x  1 root root      7 2006-01-03 14:11 /usr/bin/gcc -> gcc-4.0
-rwxr-xr-x  1 root root 100976 2005-09-16 13:54 /usr/bin/gcc-3.3
-rwxr-xr-x  1 root root 105948 2005-09-16 17:38 /usr/bin/gcc-3.4
-rwxr-xr-x  1 root root 117492 2005-10-01 17:40 /usr/bin/gcc-4.0

```
which means that gcc is just a link to gcc-4.0

use
```
sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
```
to set the symlink to point to gcc-3.4

have a read of
```
man ln
```
if you are unsure of this process.

---

### Post by traumtaenzer on 2006-01-14
Thanks for your help. So I found the actual problem, the drivers were just copied to the wrong directory using make modules_install, because there are 3 kernel directories in my /lib/modules directory. I've copied them to all 3 and now I've got the monitoring mode

Thanks a lot again!

---

