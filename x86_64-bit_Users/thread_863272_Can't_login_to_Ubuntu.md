---
title: "Can't login to Ubuntu"
date: 2008-07-18
forum: x86 64-bit Users
---

### Post by pspmasterpro on 2008-07-18
I modifed my login screen and after I reboot and try to login but the login window never diaplys. All I see is the background color and the cluster nothing else. I think I've damaged the login somehow is there a way I can fix this without having to repartition and reinstall Ubuntu.

---

### Post by tuxxy on 2008-07-18
If you messed it up in the xorg try and run a ttyl by doin ctrl alt & F1 at error screen , login from the prompt and try 

```
startx 
```

if no luck, you could reconfigure the xorg.

```

dpkg-reconfigure xserver-xorg
```

then try startx again

---

### Post by pspmasterpro on 2008-07-18
O.K. I pressed CTRL + ALT + F1 then it asked me for my username and password after that I typed ```
startx
```
and it gave me this error

```
Fatal Server error:
Server is already active for display 0 
If this server is no longer running, remove /tmp/.xo-lock and start again.

Invalid MIT-MAGIC-COOKIE-1 keygiving up
Xinit: Interrupted system call (errno 4):
unable to connect to x server
Xinit: no such process (errno 3); Server error
```

So I guess I have to reconfigure the xorg

---

### Post by tuxxy on 2008-07-18
Attempt the second command now and try startx again

---

### Post by naturalfreak on 2008-08-14
I tried enabling the ATI driver and that fixed things.  In Failsafe mode, System > Administration > Hardware Drivers then select the ATI driver.

---

