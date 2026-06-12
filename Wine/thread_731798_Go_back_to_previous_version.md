---
title: "Go back to previous version"
date: 2008-03-22
forum: Wine
---

### Post by javafiend on 2008-03-22
How do you go back to a previous version of Wine?  I have 0.9.57 and want to go to 0.9.55.

---

### Post by schiznik on 2008-03-22
Have a look into apt-pinning. You will end up with something similar to the below (this is for preventing dapper-backports from updating all of my server):```
~$ cat /etc/apt/preferences
Package: *
Pin: release a=dapper-backports
Pin-Priority: 400
```

---

### Post by javafiend on 2008-03-22
Well, I found the 0.9.55 .deb file in the Wine archive and installed that.  Unfortunately, I still couldn't get EQ2 to work :(

---

