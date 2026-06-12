---
title: "Find?"
date: 2006-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by confusimo on 2006-10-18
Xbunut 6.06 DD.

Ubuntu has a find command.  But Xbuntu doesn't.  Like search local HD for files.  Or amI missing something?

Thanks,
Confusimo

---

### Post by yota on 2006-10-18
You can install/reinstall the findutils package, the find command is there.

> 
yota@linbook:~$ which find
/usr/bin/find
yota@linbook:~$ dpkg -S /usr/bin/find
findutils: /usr/bin/find


Hope this helps!

---

### Post by siersmak on 2006-10-18
I think confusimo is looking for a GUI find utility in Xubuntu.  Try installing the xffm package, which adds Accessories -> Find Utility to the XFCE menu.  At first glance the xffm find utility is the same as the gnome find utility.

-Ken

---

### Post by confusimo on 2006-10-18
I did that thatnkfully synaptic had that and I installed claw4 also and now it says search for files in Accessories.  Don't remeber if it ever did before.  But what it is now workd great. 

Thanks,
Confusimo

---

