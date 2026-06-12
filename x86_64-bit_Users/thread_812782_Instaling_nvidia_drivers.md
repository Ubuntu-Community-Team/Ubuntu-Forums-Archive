---
title: "Instaling nvidia drivers"
date: 2008-05-30
forum: x86 64-bit Users
---

### Post by anksi4u on 2008-05-30
How do i install Nvidia drivers so that the command nvidia-settings work? I have installed hardy recently...

---

### Post by pixel :-) on 2008-05-30
try(i checked, there is such a package)

sudo ap-get install nvidia-settings

---

### Post by kingtaurus on 2008-05-30
Okay. First use the command pixel gives;
```

sudo aptitude install nvidia-settings

```
Then you may need to disable Xgl (if you are using it). To find out use:
```

ps x | grep Xgl

```

If it returns something like:
```

9043 ?        SL   610:05 Xgl :1 <snip>

```

Do the following:
```

touch ~/.config/xserver-xgl/disable

```

On restart of the Xserver, xgl will be disabled and you can use nvidia-settings.

---

### Post by Sef on 2008-05-30
> try(i checked, there is such a package)

sudo ap-get install nvidia-settings

Easier is System > Administration > Hardware Drivers > Click on the appropriate box, (if there is more than one) > click apply > reboot > Close.

Also it is apt-get, not ap-get.  (Yes, easy mistake to make.)

---

