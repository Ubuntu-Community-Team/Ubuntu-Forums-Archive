---
title: "wildcard not working in gutsy"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-10-21
```
chris@ubuntu:~/.Trash$ sudo chown -Rc chris *      
chown: invalid option -- ~
Try `chown --help' for more information.
chris@ubuntu:~/.Trash$ sudo chmod -Rc 777 *  
chmod: invalid option -- ~
Try `chmod --help' for more information.
chris@ubuntu:~/.Trash$ 
```

This never happened before upgrading to Gutsy.

---

### Post by Jouke74 on 2007-10-23
Is your keyboard setting ok? "*" is being replaced by "~" somehow.

---

### Post by go_beep_yourself on 2007-10-24
How can I know? I had set my keyboard to standard us english. I'm not sure that this is a keyboard problem. Does it happen when you try it in Gutsy? This problem only started happening after upgrading to Gutsy.

---

### Post by Yellow Pasque on 2007-10-24
```
dan@harvest:~/.Trash$ sudo chown -Rc dan *
dan@harvest:~/.Trash$ ls -la
total 20
drwx------  2 dan dan 4096 2007-10-24 01:33 .
drwxr-xr-x 44 dan dan 4096 2007-10-23 23:57 ..
-rw-r--r--  1 dan dan 8313 2007-10-12 15:43 pidgin.desktop

```

---

