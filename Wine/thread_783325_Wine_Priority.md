---
title: "Wine Priority"
date: 2008-05-05
forum: Wine
---

### Post by Trance56k on 2008-05-05
I have Wine run at priority -10. But it's getting anoying everytime I start Wine I have to change the Priority. Is there a way to keep the priority at -10?

---

### Post by lesergi on 2008-05-05
Do you set it with "nice"??

---

### Post by Trance56k on 2008-05-05
nice?

---

### Post by lesergi on 2008-05-05
How do you set priorities?

---

### Post by Trance56k on 2008-05-05
The system monitor.

---

### Post by lesergi on 2008-05-05
Nice is the program that sets priority.

If you want set a priority you must run nice:

```
nice -n 9 wine App.exe
```

This sets wine priority to 9, if you want smaller than 0, you must run with sudo:

```
nice -n -10 wine App.exe
```

If you run Wine from desktop shortcut, edit it and add nice command to the command to execute.

Salut!

---

### Post by Trance56k on 2008-05-05
Woot thank you!

---

### Post by lesergi on 2008-05-05
To you!


Bye!

---

