---
title: "HH_8.04.1 update failing"
date: 2008-09-25
forum: x86 64-bit Users
---

### Post by nss0000 on 2008-09-25
Gents:

Running x64HH_8.04.1  

 I've got a funny triangular icon with an "!" mark , where my update icon ought to be. When I try to manually update I get the ERROR MESSAGE:


E: Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)
E: Unable to lock the list directory


What? Any clue appreciated.

---

### Post by cariboo on 2008-09-25
Have you looked in /var/lib/apt/lists/ at the lock file? If there is one it should be owned by root and have file permission of 640.

Jim

---

### Post by nss0000 on 2008-09-25
crboo:

ayh@asusm2n:~$ cd /var/lib/apt/lists/
bash: cd: /var/lib/apt/lists/: No such file or directory

???

---

### Post by Sef on 2008-09-26
> ayh@asusm2n:~$ cd /var/lib/apt/lists/
bash: cd: /var/lib/apt/lists/: No such file or directory

???

The command is correct.  See if you can get do this:

```
cd /var/lib/apt/
```  If so, then the problem lies with the lists.

---

### Post by nss0000 on 2008-09-26
SEF:

I get this:

ayh@asusm2n:~$ cd /var/lib/apt/
ayh@asusm2n:/var/lib/apt$ ls -alr
total 48
drwxr-xr-x  2 root root  4096 2008-09-17 07:34 periodic
drwxr-xr-x  3 root root  4096 2008-09-16 09:40 mirrors
drwxr-xr-x  2 root root  4096 2008-09-16 10:07 keyrings
-rw-r--r--  1 root root 25655 2008-09-17 21:03 extended_states
drwxr-xr-x 61 root root  4096 2008-09-16 16:21 ..
drwxr-xr-x  5 root root  4096 2008-09-18 20:48 .
ayh@asusm2n:/var/lib/apt$ 

?? I seem to have no-LIST ?? What is it ... how do I get one ???

---

