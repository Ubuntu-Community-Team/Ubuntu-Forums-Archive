---
title: "Can't get HP DeskJet 720c to print"
date: 2005-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by manfo on 2005-07-14
Hello,
since gnome-cups-manager couldn't get my printer to work (it correctly detects it, and the queue also accepts every job, but they all disappear in a few seconds and nothing is printed--I think it's all redirected to /dev/null), I tried to add a new printer with sudo foomatic-gui.
Ok: the system detects the printer, I choose the appropriate driver (/usr/share/cups/model/foomatic-ppds/HP/HP-DeskJet_720C-pnm2ppa.ppd.gz), then the new queue is shown in the GUI, but I get the following error lines in the console:

```
lpadmin: add-printer (set model) failed: server-error-internal-error
Could not set up/change the queue "deskjet_720c"!
 * Usage: /etc/init.d/cupsd {start|stop|restart|force-reload}
invoke-rc.d: initscript cupsys, action "reload" failed.
```

...and still can't get nothing to print!  :neutral:

So, where am I wrong?
Thanks in advance!

---

