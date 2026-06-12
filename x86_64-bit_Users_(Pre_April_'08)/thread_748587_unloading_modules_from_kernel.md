---
title: "unloading modules from kernel"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by defenestratos on 2008-04-07
If I use ndswrapper for my RT2500 wireless can I somehow unload the RT2500 module from the kernel? It is causing me problems on suspend to ram/disk by not being able to unload. Chmod says it is FATAL "in use." Will it screw my wireless up?

Here is the link to the other question relating to this. ;)


[http://ubuntuforums.org/showthread.php?t=697025](http://ubuntuforums.org/showthread.php?t=697025)

---

### Post by defenestratos on 2008-04-11
No-one is answering this. Is it in the wrong forum or is it simply a dead question no-one wants to think about? I'm feeling left out.

---

### Post by njparton on 2008-04-11
```
rmmod
```
 
[http://ubuntuforums.org/showthread.php?t=201623](http://ubuntuforums.org/showthread.php?t=201623)

---

### Post by Jouke74 on 2008-04-11
Yup, or blacklist...

---

### Post by NullHead on 2008-04-11
Blacklist is a bit harsh. I suggest using rmmod for example: ```
sudo rmmod <module> 
or for ndiswrapper 
sudo rmmod ndiswrapper
```

You can check the status of all the kernel modules by doing: ```
lsmod
```If you want to know if ndiswrapper is loaded use this: ```
lsmod | grep ndiswrapper
```

---

### Post by njparton on 2008-04-11
I believe you can also do ```
modprobe -r
``` which takes dependancies into account.

---

### Post by defenestratos on 2008-04-12
No go.

> hugo@hugo-laptop:~$ sudo rmmod rt2500
Password:
ERROR: Module rt2500 is in use
hugo@hugo-laptop:~$ sudo modprobe -r rt2500
FATAL: Module rt2500 is in use.
hugo@hugo-laptop:~$


Can I force it to unload? is stopping me from suspending to ram or disk.

Thanks for the helpful replies!

---

### Post by NullHead on 2008-04-12
It's a networking driver right? Well I'd try this then: ```
sudo /etc/init.d/networking stop
``````
sudo rmmod rt2500
```

---

### Post by defenestratos on 2008-04-12
Dear Nullhead,

I tried your code and I succeeded in unloading the module! After that I tried to hibernate but just got the black screen of death on resume. The fan went crazy and no buttons did anything. Just turned it off and then on again...

The other thing is after I stopped the networking of course the web disappeared. How do you start it again?
 
I think we are getting somewhere!

---

### Post by NullHead on 2008-04-12
Ok after you get networking and your module unloaded you can reload them using these: ```
sudo /etc/init.d/networking start
``````
sudo modprobe rt2500
```

---

