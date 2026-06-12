---
title: "Keyboard layout problem"
date: 2008-10-20
forum: x86 64-bit Users
---

### Post by bettertennis on 2008-10-20
I have just upgraded to Beta 8.10, almost everything works great so far, but My KB layout is somehow wrong.  When I push backspace, I get ] , and when I push the apostrophe it does backspace.  I hve tried all internal KB layouts, where can I correct this problem, it is frustrating to write ANYTHNG.

 - Seth

---

### Post by Jozza The Wick on 2008-11-27
Others have had similiar problems - myself included.

Try this thread:

[http://ubuntuforums.org/showthread.php?t=341545](http://ubuntuforums.org/showthread.php?t=341545)

In particular,

xmodmap -e "keycode 48 = apostrophe quotedbl"

worked for me....

Hope this helps!

---

### Post by jmacx81 on 2008-11-27
sounds like somehow your default keyboard came to be a quarty keyboard

strange

---

