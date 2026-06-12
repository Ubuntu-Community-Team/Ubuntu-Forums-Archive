---
title: "Problem installing mod_evasive"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by cjtjamandra on 2008-05-20
I have a 64 bit ubuntu server and iam trying to install mod_evasive. but in the steps where i will execute the command:

```
sudo /usr/bin/apxs2 -cia mod_evasive20.c
```


an error has occured:

```
line 1222: x86_64-linux-gnu-gcc: command not found
```

what does this error mean?

please help.. thx

---

### Post by Cappy on 2008-05-20
Try installing
```
sudo apt-get install build-essential
```

---

### Post by cjtjamandra on 2008-05-20
Thanks it solved the problem. :)

---

