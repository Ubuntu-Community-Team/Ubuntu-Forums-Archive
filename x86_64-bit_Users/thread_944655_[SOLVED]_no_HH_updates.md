---
title: "[SOLVED] no HH updates"
date: 2008-10-11
forum: x86 64-bit Users
---

### Post by nss0000 on 2008-10-11
Gents:

I gotta re-ask this question:

Whenever I try to UPDATE HH-8.04.1 no update is provided and  I get the below error.


E: Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)
E: Unable to lock the list directory

The directories in question in-fact do NOT exist on my system. Can they be GOT or the issue hacked-around?

nss
*****

---

### Post by cariboo on 2008-10-11
The lock file is an empty file so all you have to do is create a lock file in /var/lib/apt/lists. to  do this open an Applications-->Accessories-->Terminal and type:

```
cd /var/lib/apt/lists
```

once in the the directory type:

```
sudo touch lock
```

Enter your password when asked. Note: your password will not be echoed back. To check that you created the file in the same terminal type:

```
ls -l lock
```

THe output should look like this:

```
ls -l lock
-rw-r----- 1 root root 0 2008-09-30 05:58 lock
```

Jim

---

### Post by nss0000 on 2008-10-11
CBOO:

Many thanks for your advice. Clear & to the point! Following your text, and with the additional trick of adding subdir:

         /var/lib/apts/list/partial

...  errors stopped and the download_updates are pouring in.

---

