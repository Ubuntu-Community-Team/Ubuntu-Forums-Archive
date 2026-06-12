---
title: "Failed to fetch compiz-plugins"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by TripleE on 2006-08-28
I updated my XGL from the          Falcon generated repository         v6.06, but it cannot download the updated compiz-plugin:

```
W: Failed to fetch http://ubuntu.systemadministrator.org/pool/dapper/eyecandy/compiz-plugins_0.4-0ubuntu1_amd64.deb
  404 Not Found

```

Any suggestions?  Do I need it?  Thanks in advanced for the help.

---

### Post by aceracer24 on 2006-08-29
that repo for some reason has gone down and been down for the better part of a week. Do you need the update? No, everything is working fine right? If so then your good to go. If you really think you "need" it then here is my current sources.list. You can add remove as you plz, one of these updated for me but not sure which one it was. I think roaf's. 

```
###############################
#######Compiz/Xgl Repos########
###############################
deb http://www.beerorkid.com/compiz dapper main stable
##deb http://ubuntu.systemadministrator.org dapper eyecandy
deb http://ubuntu.moshen.de/ dapper all
##deb http://xgl.compiz.info/ dapper main
##deb http://ubuntu.compiz.net/ dapper main
##deb http://media.blutkind.org/xgl/ dapper main
deb http://raof.dyndns.org/falcon/ dapper all
```

---

### Post by TripleE on 2006-08-29
Thanks a bunch.  That was just too simple:D

---

