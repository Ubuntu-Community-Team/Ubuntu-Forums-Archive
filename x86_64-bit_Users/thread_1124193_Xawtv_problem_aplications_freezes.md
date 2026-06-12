---
title: "Xawtv problem: aplications freezes"
date: 2009-04-13
forum: x86 64-bit Users
---

### Post by radovic on 2009-04-13
Hello, I have a problem running xawtv on my 64bit Ubuntu 8.10. I am using latest kernel, I have MSI TV@nywhere Master tv card that runs OK on Ubuntu 8.04 32bit. The problem is that when I try to run xawtv, it just blanks the screen, nothing happens, i have to reset X in order to exit (ctrl+alt+backspace), there are no error messages, and no config file for xawtv that should be made when running the aplication for the first time. Does anyone know how do I fix the problem. I also have a web cam, I tried pulling it out when starting, but no luck.

---

### Post by cariboo on 2009-04-13
I would suggest you open a terminal and type:

```
xawtv -c /dev/video0
```

Substitute your video device for the one in the command above. If that works you can edit the launcher in the Sound & Video menu.

Jim

---

### Post by radovic on 2009-04-16
Could not make it work, I switched to 32bit Ubuntu, and everything works!

---

