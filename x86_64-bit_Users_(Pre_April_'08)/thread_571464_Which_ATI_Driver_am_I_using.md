---
title: "Which ATI Driver am I using?"
date: 2007-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by revchris on 2007-10-09
How do I know which driver I am currently using?

---

### Post by luisromangz on 2007-10-09
Check your /etc/X11/xorg.conf file's Device section.

---

### Post by John.Michael.Kane on 2007-10-09
Run the command below from a terminal. you will see a few lines one being the driver your using.
```
cat /etc/X11/xorg.conf|grep Driver
```

---

### Post by revchris on 2007-10-09
It says fglrx, but which version of the ATI driver?  I was on the ATI website and they have 8.40, but I saw on here someone had a link for 8.41.  So I was just trying to find out which one I have or if I need to download and install a newer one.

Thanks

---

### Post by John.Michael.Kane on 2007-10-09
This should output the info you want.
```
dmesg | grep fglrx
```

---

### Post by revchris on 2007-10-09
thats worked, thanks

---

