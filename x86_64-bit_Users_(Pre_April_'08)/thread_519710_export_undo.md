---
title: "export undo?"
date: 2007-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by kiryo on 2007-08-07
how can i undo this: export LIBGL_DRIVERS_PATH=/usr/X11R6/lib32/modules/dri/:/usr/lib32/:/usr/X11R6/lib/modules/dri/:
/usr/lib/

i tried to make my cedegas openGL work but instead i broke 3d acc -__-

It seems its not yet fixed in 64 mode

---

### Post by KIAaze on 2007-08-07
The export command only makes the variable active in the current shell and in subsequently executed commands (if you launch a new shell from the current one for example).
From the man:
> The  shell  shall give the export attribute to the variables corresponding to the specified names, which shall cause them to be in the environment
       of subsequently executed commands. If the name of a variable is followed by = word, then the value of that variable shall be set to word.

If you open a new terminal, it won't remember the variable you set.

To unset the LIBGL_DRIVERS_PATH in the current terminal, just do:
```
export LIBGL_DRIVERS_PATH=''
```

---

