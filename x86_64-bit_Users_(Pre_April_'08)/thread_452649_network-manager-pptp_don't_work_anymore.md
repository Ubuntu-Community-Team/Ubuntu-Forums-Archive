---
title: "network-manager-pptp don't work anymore"
date: 2007-05-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by eyelessfade on 2007-05-23
For a long time my pptp connection worked like a charm using network manager, but one day it just didn't want anymore.

in dmesg I only get:
```

[ 1268.258595] nm-ppp-auth-dia[16903]: segfault at 0000000000000088 rip 00002aedb4b0d21b rsp 00007ffffbb41db0 error 4
```

when I try to connect. my old vpn script still work though.

I use amd64.

Found a fix also:
[http://www.wlug.org.nz/~crb/nm/feisty/](http://www.wlug.org.nz/~crb/nm/feisty/)
do the trick :)

---

