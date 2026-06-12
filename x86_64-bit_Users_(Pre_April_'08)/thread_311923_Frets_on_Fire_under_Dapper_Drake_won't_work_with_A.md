---
title: "Frets on Fire under Dapper Drake won't work with AMD64"
date: 2006-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravalox on 2006-12-03
I am attempting to run the latest and greatest Frets on Fire on my Dapper Drake ubuntu installation on my Athlon64 system, and when I do so I get this error message:
```

ImportError: libvorbisfile.so.3: cannot open shared object file: No such file or directory

```

Anyone have a notion as to why?  I have a /usr/lib/linvorbisfile.so.3

---

### Post by atoponce on 2006-12-03
How did you install the game?  That game rocks, btw

---

### Post by ravalox on 2006-12-03
I just downloaded the binaries and untarred the file to my home directory.  It is killer, I just wish I could get it working on an AMD64 box.

---

### Post by fabertawe on 2006-12-04
If it's a 32bit game then you'll need to locate the missing **i386** lib from [Ubuntu packages]("http://packages.ubuntu.com/") and **extract and copy** to '/usr/lib32'. Do not force install the debs. Repeat as necessary until it runs!

Paul

---

