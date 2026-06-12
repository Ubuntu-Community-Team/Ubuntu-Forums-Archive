---
title: "bunzip2"
date: 2006-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by QueensGambit on 2006-05-27
im set up on linksys 2.4 broadband, i downloaded the driver but its dos.exe so i got    
get dosemu.tgz but when i try to open it says erro: permission denied, even in terminal tar xzvf.  .tgz,    any suggestions would be appreciated

---

### Post by Sutekh on 2006-05-27
The solutions to your problem could be numerous depending on some factors.

How did you download the file?  Where, which folder did you download it too?

Permission issues can usually be fixed with the use of sudo
```
**sudo** tar xvzf dosemu.tgz
``` should overcome your access denied error.

These links are some suggested reading

[http://psychocats.net/ubuntu/permissions.php]("http://psychocats.net/ubuntu/permissions.php")

[Ubuntu Wiki - Root and Sudo]("https://wiki.ubuntu.com/RootSudo")

---

