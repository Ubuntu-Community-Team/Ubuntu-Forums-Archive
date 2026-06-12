---
title: "installing new doom3 build breaks libstdc++.so.5"
date: 2005-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by negatory on 2005-05-28
I've just installed the new doom3 build (1.3) as root and it overwrited my libstdc++.so.5 in /usr/lib .Now some programs complain that: "libstdc++.so.5: cannot open shared object file: No such file or directory" . How can I revert to my old library?I can't apt-get because it doesn't run exiting with the above error!
I've got Hoary 5.04 for 64bits.If someone just send me the file for that library will that work? (the files are libstdc++.so.5 and libstdc++.so.5.0.7)

Please help!

Pedro Carrico

---

### Post by negatory on 2005-05-28
I panicked I must confess...I've entered my hoary install cd and dpkg -i all the libraries related to gcc and it's working!Had to downgrade a few but nothing that a apt-get dist-upgrade can't solve...
Thanks for your patience.
Pedro Carriço

PS: be warned that the new doom3 build will break your libstdc++ when installing as root via [this](http://www.linuxquestions.org/questions/archive/33/2004/12/3/239484)  method.

edit: edited because of some bad english writing errors  :grin: ...

---

