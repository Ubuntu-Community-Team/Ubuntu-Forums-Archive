---
title: "missing file?"
date: 2007-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by marmot1101 on 2007-08-31
I am having a goofy problem attempting to install Sun Application Server on Feisty server.  I download the file, or bring it over via cd, copy the file to /root.  From there, I chmod the file, list to make sure I did it right, then attempt to run the installer.  It says "no such file" even though it is clearly there.  The "find" command will find the file, but "locate"  will not.  See below:

root@ciclin3:~# ls -l
total 41820
-r-xr-xr-x 1 root root 42771779 2007-08-31 10:17 sjsas_pe-9_0_01-p01-linux.bin
root@ciclin3:~# chmod 777 sjsas*
root@ciclin3:~# ls -l
total 41820
-rwxrwxrwx 1 root root 42771779 2007-08-31 10:17 sjsas_pe-9_0_01-p01-linux.bin
root@ciclin3:~# ./sjsas*
bash: ./sjsas_pe-9_0_01-p01-linux.bin: No such file or directory
root@ciclin3:~# find sjsas*
sjsas_pe-9_0_01-p01-linux.bin
root@ciclin3:~# locate sjsas*
root@ciclin3:~#

Any Ideas?

---

### Post by Kilz on 2007-08-31
> **marmot1101 said:**
> I am having a goofy problem attempting to install Sun Application Server on Feisty server.  I download the file, or bring it over via cd, copy the file to /root.  From there, I chmod the file, list to make sure I did it right, then attempt to run the installer.  It says "no such file" even though it is clearly there.  The "find" command will find the file, but "locate"  will not.  See below:

root@ciclin3:~# ls -l
total 41820
-r-xr-xr-x 1 root root 42771779 2007-08-31 10:17 sjsas_pe-9_0_01-p01-linux.bin
root@ciclin3:~# chmod 777 sjsas*
root@ciclin3:~# ls -l
total 41820
-rwxrwxrwx 1 root root 42771779 2007-08-31 10:17 sjsas_pe-9_0_01-p01-linux.bin
root@ciclin3:~# ./sjsas*
bash: ./sjsas_pe-9_0_01-p01-linux.bin: No such file or directory
root@ciclin3:~# find sjsas*
sjsas_pe-9_0_01-p01-linux.bin
root@ciclin3:~# locate sjsas*
root@ciclin3:~#

Any Ideas?

Have you made sure the file is chmod'd to make it executable. The error is sometimes used to say it cant find the executable file named as such. Since you are rying to run it as an executable this is most likely whats happening imho.

---

