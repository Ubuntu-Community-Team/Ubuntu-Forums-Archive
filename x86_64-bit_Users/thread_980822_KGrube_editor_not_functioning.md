---
title: "KGrube editor not functioning"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by Oldcowboy on 2008-11-13
After upgrading to 8.10 and installing KGrube editor,
it will not load. There are a few seconds of blinking on the main screen and then - NOTHING.

I tried accessing KGrube from the command line and nothing happened there either, even though Add/Remove shows that KGrube is installed.

Have others experienced this as well, and is there a solution?

---

### Post by cariboo on 2008-11-13
To run kgrubeditor from the terminal try:

```
kcmshell4 kgrubeditor
```

this starts the editor for me. Check to see that you have the command in your menu.

Jim

---

### Post by Oldcowboy on 2008-11-13
That did it! It works now from the shell and from the menu.

Thank you for your help.:)

---

### Post by Artemis_Fowl on 2008-11-15
It must be a packaging issue as it seems: [https://bugs.launchpad.net/ubuntu/+source/kgrubeditor/+bug/296887](https://bugs.launchpad.net/ubuntu/+source/kgrubeditor/+bug/296887)

---

