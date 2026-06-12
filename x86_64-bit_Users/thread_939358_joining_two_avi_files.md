---
title: "joining two avi files"
date: 2008-10-05
forum: x86 64-bit Users
---

### Post by papaw on 2008-10-05
can anyone give me the commands to join two avi files using mencoder. most i have found in google search doesnt work. thx in advance

---

### Post by altonbr on 2008-10-05
```
mencoder -forceidx -ovc copy -oac copy -o output.avi video1.avi video2.avi
```

Google can be annoying if you don't know what to search for. Maybe try concatenate next time? That's what I have my script saved as anyway.

Hope that helps!

---

### Post by papaw on 2008-10-06
thanks altonbr this worked

---

