---
title: "Realtek Wireless issues"
date: 2016-10-31
forum: openSUSE and SUSE Linux Enterprise
---

### Post by renejesusgv on 2016-10-31
I have this netbook too but I did not find an answer that worked for me in ubuntu, Im using openSuse tumbleweed,  the connection still fails but its more stable than ubuntu. 
check if this config works for you.

```
renejesusgv@linux-azlq:~> grep [[:alnum:]] /sys/module/rtl8821ae/parameters/*
/sys/module/rtl8821ae/parameters/debug:1
/sys/module/rtl8821ae/parameters/disable_watchdog:N
/sys/module/rtl8821ae/parameters/fwlps:N
/sys/module/rtl8821ae/parameters/int_clear:N
/sys/module/rtl8821ae/parameters/ips:N
/sys/module/rtl8821ae/parameters/msi:Y
/sys/module/rtl8821ae/parameters/swenc:N
/sys/module/rtl8821ae/parameters/swlps:N
```

---

### Post by chili555 on 2016-10-31
> Im using openSuse tumbleweed, I don't know how we can help you. Suse is a mystery to me.

---

### Post by QIII on 2016-10-31
@ renejesusgv:

Please use the default font and color.  Please enclose all console output in code tags.

Thanks.

---

### Post by renejesusgv on 2016-11-01
It is not an ubuntu-specific issue, there are many bugs reported,  [https://bugzilla.kernel.org/show_bug.cgi?id=150861](https://bugzilla.kernel.org/show_bug.cgi?id=150861) hopefully we will have a solution soon

---

### Post by howefield on 2016-11-01
Posts moved to own thread and to the "*openSUSE and SUSE Linux Enterprise*" forum.

---

