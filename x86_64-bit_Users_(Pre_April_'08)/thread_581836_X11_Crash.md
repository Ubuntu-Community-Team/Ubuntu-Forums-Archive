---
title: "X11 Crash"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by FlyDiver on 2007-10-19
Running KDE. Startx and normal boot/logon generate message indicating cannot write to /tmp followed by reboot of X server. /tmp exists and console logon works correctly. Tried it a bunch of times an one actually worked but that was 2 days ago.

Thanks in advance

---

### Post by Cappy on 2007-10-19
Make sure your disk isn't full. ```
df -h
``` can show you this.

If not, go into the recovery console and try
```

chmod 777 /tmp

```

If that doesn't solve the problem try
```

chown $USER:$USER -r /tmp
chmod 777 -r /tmp

```

---

