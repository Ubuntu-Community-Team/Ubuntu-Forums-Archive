---
title: "TEW2004 for wine"
date: 2008-04-08
forum: Wine
---

### Post by davebridges on 2008-04-08
Hi I am tinkering with a windows game that I used to play.  It installed fine with wine but upon running i get an error message "Run-time error '429':  ActiveX component can't create object"

Anyone have any workaround ideas?

---

### Post by miggl on 2008-07-02
Trying the same. Any solution?

---

### Post by cogadh on 2008-07-02
Considering Wine does not have ActiveX controls functionality, you probably need to install it:
```
cd ~/.wine/c_drive/Program\ Files/
wget http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz
tar -zxvf mozcontrol.tgz && rm mozcontrol.tgz
cd mozcontrol/ && wine regsvr32 mozctlx.dll
```
That being said, it still doesn't work all that well, so you might still be stuck.

---

