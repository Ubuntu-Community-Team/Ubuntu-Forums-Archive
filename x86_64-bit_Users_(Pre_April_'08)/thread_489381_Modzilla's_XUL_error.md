---
title: "Modzilla's XUL error"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by kzm. on 2007-07-01
anybody tried to get xul running under 64bit? if so, could (s)he give me some advise? i get this error, even with the most simple example:

```
(xulrunner-bin:30471): Gtk-WARNING **: Locale not supported by C library.
 Using the fallback 'C' locale.
```

---

### Post by praxis22 on 2007-07-01
If you're getting locale errors, it's because you have you location set to something that firefox doesn't support.  If it says to go back to the C locale, it means it's trying to sort out base defaults for languages, etc. 

Have you tried to restart firefox in safe mode, does that work? You may have to rebuild your profile if it does.

---

### Post by RAOF on 2007-07-02
Also, that's not an error :).  If everything else works, you can ignore that.

---

### Post by kzm. on 2007-07-02
well everything stops there.. so i experienced it as an error at least. :)

anyway. i dont use firefox to run it directly. i use xulrunner.. and i dont know how to convert the advise to it. it seems not fitting to this forum anymore, if its not a 32/64 problem, but may be praxis22 has another hint for me? the xul forum is very inactive...

---

### Post by fakie_flip on 2007-07-05
Try running it with strace.

---

