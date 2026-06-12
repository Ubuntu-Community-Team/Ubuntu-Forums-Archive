---
title: "Problem installing Ubuntu."
date: 2007-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Selrach on 2007-06-24
I try to install it, but it stops withed the line "Killed". Anyone know why it does this?

---

### Post by Mr_bleu on 2007-06-24
It just reads, "Killed"?

---

### Post by Selrach on 2007-06-24
It says it right after Starting ACPI service...

---

### Post by Cappy on 2007-06-24
Try boot parameters:
```

noapic nolapic
```

---

### Post by Selrach on 2007-06-24
Tried that, its still not working.

---

### Post by BobCFC on 2007-06-24
If you remove quiet option you might get a more detailed error message

---

