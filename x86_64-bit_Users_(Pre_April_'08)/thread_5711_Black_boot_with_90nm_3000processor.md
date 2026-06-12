---
title: "Black boot with 90nm 3000processor"
date: 2004-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by zellmer006 on 2004-11-21
allright fairly straight forward, I load the downloaded livecd into the computer and tell it too boot linux, after that it seems to go through a download process, and then just goes to a black screen.  any ideas?
The Laptop is an Acer Ferrari 3400 :?:

---

### Post by cybrjackle on 2004-11-23
[QUOTE=zellmer006]allright fairly straight forward, I load the downloaded livecd into the computer and tell it too boot linux, after that it seems to go through a download process, and then just goes to a black screen.  any ideas?
The Laptop is an Acer Ferrari 3400 :?:[/QUOTE]

I can't reboot at the momment, but when the boot up options come up instead of hitting <enter> look through the options.  might be F4 or F5 has the noapic, try that.

---

### Post by cybrjackle on 2004-11-25
When the cd boots up, just hit F1 and then type the following:

```

linux noapic nolapic

```

---

### Post by waz on 2005-01-14
[QUOTE=cybrjackle]When the cd boots up, just hit F1 and then type the following:

```

linux noapic nolapic

```[/QUOTE]
 I have an acer ferrari 3200, almost same spec as 3400.

The liveCD works on my machine, but when i try to install I get the same problem.

tried the linux noapic nolapic, but still goes black after couple of pages or so  :(

---

