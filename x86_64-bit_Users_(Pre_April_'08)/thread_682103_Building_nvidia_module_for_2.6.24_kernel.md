---
title: "Building nvidia module for 2.6.24 kernel"
date: 2008-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by mick8985 on 2008-01-29
I have built a kernel module for  the new 2.6.24 kernel, as this is the first tickless kernel for 64 bit, and I want to improve the battery life of my dell m1330, but the module will not load.
Is the current driver incompatible with the new kernel?

---

### Post by kuja on 2008-01-31
Hmmm, so you've build the new module, while running this new kernel?  If I do recall you'd have issues installing nvidia drivers for more than one kernel.. Hmmmmm, tried Envy?

---

### Post by PmDematagoda on 2008-01-31
Did you receive any errors while installing the driver? And did you try reconfiguring the X-Server after installing the driver? I was able to compile the Nvidia kernel on kernel 2.6.24 with no problems.

---

### Post by mick8985 on 2008-02-02
I initially ran the just ran sh NVIDIAetc.run and that builds the module without incident.
But when I load the module I got.

```
michael@michael-laptop:~$ sudo modprobe nvidia
FATAL: Error running install command for nvidia
```

Not very helpful, and dmesg | tail gives nothing that concerns this issue.

So I tried building it with module-assistant, which fails to build the module. 
Which method did you use to build the module?

---

### Post by PmDematagoda on 2008-02-02
I simply used the normal installation method and reconfigured the X-Server after successful installation, that should work on your PC as well.

---

### Post by mick8985 on 2008-02-02
By normal installation method, You mean the sh NVIDIAetc...run?

---

### Post by PmDematagoda on 2008-02-02
Yes. Just run it and reconfigure the X-Server afterwards, after that, start the GUI using:-
```
sudo /etc/init.d/gdm start
```

---

