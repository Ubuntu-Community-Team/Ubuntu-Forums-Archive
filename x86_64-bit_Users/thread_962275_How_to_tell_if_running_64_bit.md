---
title: "How to tell if running 64 bit"
date: 2008-10-29
forum: x86 64-bit Users
---

### Post by dbelcher on 2008-10-29
How do you tell if a program is a 64 or 32 bit program? I know in windows the task manager shows an asterisk by 32 bit programs. Is there anything similar in linux?

Thank-you
Dave

---

### Post by scragar on 2008-10-29
```
uname -m
```
x86_64 is 64 bit.

---

### Post by roelpeeters on 2008-10-29
> **dbelcher said:**
> How do you tell if a program is a 64 or 32 bit program? I know in windows the task manager shows an asterisk by 32 bit programs. Is there anything similar in linux?

Thank-you
Dave
When you want to detect if a program is 32-bit or 64-bit you can use the 'file' command from the command line. For example, use the following command:
```

file /usr/bin/amarok

```

The file command will show whether it is 32-bit or 64-bit. The file command needs the absolute path to the executable which can find out by using the command 'which'.
So, combining 'file' and 'which' you get the following (pay attention to the quotes):
```

file `which amarok`

```

Roel

---

