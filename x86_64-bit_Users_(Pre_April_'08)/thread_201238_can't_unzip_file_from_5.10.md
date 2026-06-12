---
title: "can't unzip file from 5.10"
date: 2006-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by t_ras on 2006-06-21
I zipped all home directory when I moved from 5.10 to 6.06 expexting I might have troubles and will need to reinstall (which actualy happened :( ).
It is a 3.5 GB file I did through tar from command line.
Since I dont remember if I used tar or zip format (I think zip) 
I tryed both:
from windows it gets stucked unzipping,
from 6.06 I get this:
```
martin@terrenisrv1:~$ tar -xf hometar.tar
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers
tar: Error exit delayed from previous errors

```
Then it unzippes 1 of the files (in some deep directory) .
```

martin@terrenisrv1:~$ tar -zx hometar.tar

```
and gets stucked....
I tryed to boot with 5.10 live CD and unzipped from it, but it can't acces 6.06 HDD.

Any Idea?:confused:

---

### Post by rowanparker on 2006-06-21
What happens when you open it in File Roller?

---

### Post by incubus on 2006-06-21
I lack the knowledge to help there. I was surprised myself by a file that I couldn't `cat` in my amd64 installation.

Just out of curiosity, do you get any relevant information if you use "v" in the tar options? (v is for verbose)

$ tar xzvf <filename>
$ tar xvf <filename>
$ tar xjvf <filename>

But why can't you access the hard drive? We could also try that avenue.

incubus

---

### Post by steabert on 2006-06-22
What does the following give you:

$ file <filename>

and

$ tar tvf <filename>

---

### Post by t_ras on 2006-06-23
I get this:
```
martin@terrenisrv1:~$ file hometar.tar
hometar.tar: POSIX tar archive
martin@terrenisrv1:~$ tar tvf  hometar.tar
drwxrwxr-x admispconfig/admispconfig 0 2006-02-25 12:40:46 home/admispconfig/
drwxrwxr-x admispconfig/admispconfig 0 2006-05-12 21:32:30 home/admispconfig/ispconfig/
drwxr-xr-x admispconfig/admispconfig 0 2006-02-25 12:40:46 home/admispconfig/ispconfig/tools/
drwxr-xr-x admispconfig/admispconfig 0 2006-02-25 12:38:58 home/admispconfig/ispconfig/tools/clamav/
drwxr-xr-x admispconfig/admispconfig 0 2006-02-25 12:40:46 home/admispconfig/ispconfig/tools/clamav/lib/
-rwxr-xr-x admispconfig/admispconfig 911494 2006-02-25 12:40:46 home/admispconfig/ispconfig/tools/clamav/lib/libclamav.so.1.0.16
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers
tar: Error exit delayed from previous errors
martin@terrenisrv1:~$ tar xzvf hometar.tar

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

```
Opening in file roller gives the same error...
and it is

---

### Post by t_ras on 2006-06-23
File roller gives same "ovsolete header" error

---

### Post by rowanparker on 2006-06-23
Sounds like it could be a corrupt file.

---

### Post by t_ras on 2006-06-23
[QUOTE=rowanparker]Sounds like it could be a corrupt file.[/QUOTE]
:(

---

### Post by rowanparker on 2006-06-23
If it is, I really feel for you.

Just before I reinstalled Dapper, I backed up every setting (and email) in a folder then I forgot to put the folder on to disk :(. I lost every setting and email, rather annoying.

Rowan.

---

