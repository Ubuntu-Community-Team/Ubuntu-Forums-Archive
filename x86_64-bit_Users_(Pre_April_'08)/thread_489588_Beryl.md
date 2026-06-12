---
title: "Beryl"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Coron4x on 2007-07-01
I'm using Beryl for the first time, and when I finally got it working, I started playing with the options.  I think I changed the Desktop Manager from Beryl to something else, might have been Compiz or something.  Everytime I launch Beryl, my screen distorts to a greenish color and there are two screens, nothing is legible though.  How can I fix this in the terminal?

---

### Post by CheShA on 2007-07-01
You could try removing all your personal  beryl settings - 

```
mv ~/.beryl ~/.beryl_broken
```

failing that, the obvious thing to me would be to uninstall beryl:
```
apt-get remove beryl
```

that way you can get back to where you were and try to figure out what went wrong.

---

### Post by walkerk on 2007-07-01
```
metacity --replace
```

now you should be able to read.. you can undo whatever you did or try re-installing beryl..

---

