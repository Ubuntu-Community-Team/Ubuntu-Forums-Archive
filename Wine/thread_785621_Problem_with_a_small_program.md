---
title: "Problem with a small program"
date: 2008-05-07
forum: Wine
---

### Post by source.decay on 2008-05-07
For an experimental physics class I am in, there is a small (~18kb) program that produces the photoelectric effect.  When I try and open up the .exe file, Wine takes over one of my processors, and never opens up the program.  Is there anything I can do to make it work?

Thank you!

---

### Post by cogadh on 2008-05-07
It would help to get some error output from Wine. Open a terminal, cd to the directory where you have the program and run it:
```
cd /path/to/program/
wine program.exe
```
When the program runs, Wine will output any errors to the terminal window.

---

### Post by source.decay on 2008-05-07
Here is the information that was outputted to the terminal.

Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.


Nothing else, and it has taken over my processor again.

---

