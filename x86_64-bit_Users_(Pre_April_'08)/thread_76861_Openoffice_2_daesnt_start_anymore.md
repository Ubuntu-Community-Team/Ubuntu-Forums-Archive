---
title: "Openoffice 2 daesnt start anymore"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by _P_ on 2005-10-15
After the last upgrade  Openoffice stop working with this error

/usr/lib/openoffice2/program/javaldx: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/pagein: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/soffice.bin.real: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

any help?

thanks

---

### Post by scottgr on 2005-10-16
First of all it might be worth establishing if those files actually exist on your installation.  They're pretty standard files so I'd be fairly surprised if they weren't.  If they don't exist try to find which package provides them and then install that.  If they do exist then it may be they're not in the path that openoffice searches so adding the correct path might help.  If thats not the case then perhaps someone else might come up with a better suggestion than just uninstalling and reinstalling!

---

### Post by _P_ on 2005-10-16
i have this libs installed , 
i thing it is a path problem but i don't know hot to set it

can you help me?

thanks

---

### Post by Teroedni on 2005-10-16
Reinstall them using synaptic and see if that works
if not
Reinstall openoffice 2

---

