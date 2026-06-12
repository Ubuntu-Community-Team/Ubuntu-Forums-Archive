---
title: "VNCServer on amd64"
date: 2005-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by ::DoGG:: on 2005-06-29
Hello.
I i nstalled vncserver, got it tunning, nmap localhost gives me that port 5900 is open and vnc is listening on it.
When i type "vncviewer locahost" i got

```
VNC viewer version 3.3.7 - built Oct 28 2004 23:54:49
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0.0
```

It`s  probably not really complicated but i`m kinda new to VNC so if Yu gues could just help me out with this one..

---

### Post by Neurone on 2005-07-03
Hi Dogg,
  I think the reason why you can't connect with vncviewer is that the port :0.0 has been open vy a X manager which is not running vncserver.
  You should try using "vncviewer localhost:X", where X is the port opened by vncserver (try lookin at the vncserver log files, it is written which display(s)/port(s) it is using).

+

---

