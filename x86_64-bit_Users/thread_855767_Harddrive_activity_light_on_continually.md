---
title: "Harddrive activity light on continually"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by desmith1944 on 2008-07-10
I am running Ubuntu 8.04 with AMD Dual 3600.
I don't know how long this has been going on. I just noticed today that my harddrive light is on continually. I thought that maybe there was a backup going on with simple backup config. 
I have checked the system monitor and it shows no process running.
I checked the resources and I have activity on both cpu ranging as high as 13% down to 3%.
I also having constant network activity.
Anyone have any ideas on this problem. Thanks, David.

---

### Post by Vadi on 2008-07-13
Do you have any torrent clients on?

---

### Post by jerome1232 on 2008-07-13
might want to post the output of:
```
netstat -tu
free -m
top
```

netstat -tu will display all you're open connections who they are to and what port they are on (is there a way to only show established?)

free -m will show ram usage (maybe swapping)

top - processes running

---

