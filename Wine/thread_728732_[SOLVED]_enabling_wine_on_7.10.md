---
title: "[SOLVED] enabling wine on 7.10"
date: 2008-03-19
forum: Wine
---

### Post by Living2007 on 2008-03-19
How do I start Windows Base programs through WINE in Ubuntu 7.10

---

### Post by Thanoulis on 2008-03-19
Usually Ubuntu understands the EXE type and does it automatically, but you can always type
```
wine <path to application>
```

---

### Post by Living2007 on 2008-03-19
As a shortcut?

---

### Post by jacksaff on 2008-03-20
As the command for your shortcut to execute (not sure how easy this is to find in gnome but in kde it's simple so I assume gnome is too) type
wine "path to the exe"
Obviously, change path to the exe to the address of your program.
Do use the quotes though, as windows allows spaces in file names and unix doesn't, and you'll probably have a couple of spaces in the path in the fake windows directories.

---

