---
title: "Copy time"
date: 2008-08-22
forum: x86 64-bit Users
---

### Post by IamNehalem on 2008-08-22
Hello friends,

How can i copy in linux a file showing me the exact time it took to make the copy? Terminal but also GUI if possible.

Thanx

---

### Post by Cheesehead on 2008-08-22
time - *run programs and summarize system resource usage* (see man time)

```
time cp file1 file1_copy
```

As with most shell commands, it can be reformatted, piped, used in scripts, etc.

---

### Post by IamNehalem on 2008-08-22
> **Cheesehead said:**
> time - *run programs and summarize system resource usage* (see man time)

```
time cp file1 file1_copy
```

As with most shell commands, it can be reformatted, piped, used in scripts, etc.

Thanks and to copy a directory with all it's contents?

---

### Post by philinux on 2008-08-22
[http://www.oreillynet.com/linux/cmd/cmd.csp?path=c/cp](http://www.oreillynet.com/linux/cmd/cmd.csp?path=c/cp)

---

### Post by elmoosecapitan on 2008-08-22
to copy a directory with all of it's contents:

```
cp -r /directorypath.../folder_1/folder_2/  /directorypath/folder_3/
```

you will end up with a COPY of 'folder_2' inside 'folder_3'

[http://linuxcommand.org/]("http://linuxcommand.org/")

---

### Post by IamNehalem on 2008-08-24
Thanks very much guys. Now let me tell you the reason i'm asking this: i wanted to do a copy test on ntfs partititions, reiserFS partitions and see what FS returns the better result. Also more intrigueing was the fact that i wanted to see if ntfs mounter partitions with ntfs-3g give the same result (or better) than native ntfs partitions under windows. I will post tomorrow the results. :)

---

### Post by IamNehalem on 2008-08-28
Hey guys!

Here are the test results:

---

### Post by elmoosecapitan on 2008-08-28
It seems like everything has been fixed; so the only thing left is to mark the thread as [SOLVED].

---

### Post by IamNehalem on 2008-08-28
> **elmoosecapitan said:**
> It seems like everything has been fixed; so the only thing left is to mark the thread as [SOLVED].
Yes thank you!

---

