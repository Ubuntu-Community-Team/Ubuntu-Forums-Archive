---
title: "VBox Kernel Modules 2.6.24.22?"
date: 2009-01-04
forum: x86 64-bit Users
---

### Post by Krovas on 2009-01-04
Are they out there somewhere and I'm just not seeing them for some reason? The latest iteration that's available to me seems to be 2.6.24.21.

---

### Post by bford16 on 2009-01-05
> **Krovas said:**
> Are they out there somewhere and I'm just not seeing them for some reason? The latest iteration that's available to me seems to be 2.6.24.21.Not sure if this will help, but did you try to re-setup the kernel module by executing the following?```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by isparkes on 2009-01-06
Same problem - usually it takes a couple of weeks for them to be made available, but it seems a lot longer this time.

Anyone?

---

### Post by isparkes on 2009-01-06
> **bford16 said:**
> Not sure if this will help, but did you try to re-setup the kernel module by executing the following?```
sudo /etc/init.d/vboxdrv setup
```

Sorry, should have included this in the previous post:

```
sudo /etc/init.d/vboxdrv setup
```

answers with:

```
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
```

so no dice there...

---

