---
title: "Vmware Problems havent looked for more"
date: 2007-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by thisismyusername on 2007-03-31
xxx@octacore:~$ vmware
/usr/lib/vmware/bin/vmware: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
xxx@octacore:~$ 

Anyways my question is has anyone had problems with feisty and libxcb-xlib... i have reinstalled the package twice and it still is not working.

trying 
 to copy the file to /usr/lib/bin/vmware/ causes vmware to give no output, simlinks do the same.

Any ideas?

Thanks

---

### Post by Cederien on 2007-03-31
It seems the last update for Feisty broke something surrounding libxcb-xlib.so.0.
[http://www.ubuntuforums.org/showthread.php?t=397578]("http://www.ubuntuforums.org/showthread.php?t=397578")
Unless someone finds a workaround I guess we will have to wait till the problem gets fixed.

---

