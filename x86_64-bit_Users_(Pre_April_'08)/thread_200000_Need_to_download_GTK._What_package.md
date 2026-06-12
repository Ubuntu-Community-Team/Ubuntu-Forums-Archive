---
title: "Need to download GTK. What package?"
date: 2006-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nitro on 2006-06-19
What package should I grab to get gtk. I am trying to compile some printer drivers but I can't seem to find the package that contains GTK. Is it in some crazy repository that I don't know about?

---

### Post by bukwirm on 2006-06-19
Seach for packages libgtk2 and libgtk2-dev, I think.

---

### Post by Nitro on 2006-06-19
[QUOTE=bukwirm]Seach for packages libgtk2 and libgtk2-dev, I think.[/QUOTE]

Both don't exist..

---

### Post by RAOF on 2006-06-19
```
>aptitude search libgtk2
...
i   libgtk2.0-common                 - Common files for the GTK+ graphical user in
iB  libgtk2.0-dev                    - Development files for the GTK+ library     
p   libgtk2.0-doc                    - Documentation for the GTK+ graphical user 
...

```
I suggest that libgtk2.0-dev is the package your after.

In general, you can use the search functionality of Synaptic/aptitude to find what you're loking for, faster and more easily than waiting for the forums to give you an answer ;)

---

