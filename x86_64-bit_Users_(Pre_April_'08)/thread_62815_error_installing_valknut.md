---
title: "error installing valknut"
date: 2005-09-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by kb_ganesh on 2005-09-06
i have just installed ubuntu linux a few days ago..was trying to install valknut, the network file sharing client for usage on my lan..

i get this error when i do ./configure inside the valknut folder..

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

can someone tell me what i must add as an option to ./configure to overcome this problem?

am using ubunut 5.04 on a amd64 2800+ machine..

EDIT:-

i overcame this error by installing x-window-system-dev using synaptic..and then had to install qt..

so i now decided to try out valknut...it said dclib is not installed..so, i downloaded dc-0.3.7.tar.bz2 which had both dclib and valknut in it..i installed dclib without any problems..and went to the valknut folder to install it..but i keep getting this error that says that dclib is not installed..

```
"configure: error: DCLIB must be installed. Use --with-libdc=<path> to set correct path."
```

can someone please help me out?

(please dont ask me to use synaptic to install valknut/dcgui..i tried it already but i can get only 0.3.3 whereas i need 0.3.7)

thanks for any help

EDIT 2:
have got the deb packages from [http://packages.debian.org/unstable/libs/libdc0](http://packages.debian.org/unstable/libs/libdc0) ..and vlaknut's up and working  :smile:

---

### Post by kb_ganesh on 2005-09-09
any ideas anyone?

---

### Post by kb_ganesh on 2005-09-11
doesnt anyone know of any solution? i have been able to get hold of the deb package of valknut-0.3.7 from debian packages website..still have the same problem of dclib-0.3.7 not installed..can someone make a deb package of dclib-0.3.7? please.....

---

