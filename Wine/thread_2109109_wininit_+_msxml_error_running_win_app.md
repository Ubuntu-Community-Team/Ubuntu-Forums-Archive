---
title: "wininit + msxml error running win app"
date: 2013-01-26
forum: Wine
---

### Post by frank604 on 2013-01-26
First of all, I have a post on the wine forums, however I wanted to expand my audience in hopes of insight that can lead to a solution. 

Original wine forum link: [http://forum.winehq.org/viewtopic.php?f=8&t=18203](http://forum.winehq.org/viewtopic.php?f=8&t=18203)

Program name: roomkey (hotel property management system that connects to a cloud database for tracking room reservation/guest portfolio)  

I'm on ubuntu 12.04 32bit with latest wine.  I have tried various versions of wine using builtin dll and native dll (msxml, wininit).  I have tried on archlinux as well.  All wine versions, combinations of winetricks (dll), and OS have resulted in the same error.

```
[POL_Wine] Message: Running wine- RoomKey.exe
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
fixme:win:LockWindowUpdate (0x10032), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x10032), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 190000
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domelem_setAttributeNode (0x206e68)->(0x19e9d4 0x1e3e634): semi-stub
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domelem_setAttributeNode (0x206e68)->(0x19eb3c 0x1e3e634): semi-stub
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domelem_setAttributeNode (0x206e68)->(0x19ebbc 0x1e3e634): semi-stub
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domelem_setAttributeNode (0x19eb30)->(0x19ec8c 0x1e3e60c): semi-stub
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domelem_setAttributeNode (0x19ed58)->(0x19ef14 0x1e3e628): semi-stub
fixme:ieframe:PersistStreamInit_Load (0x19e9b8)->(0x1faf28)
```

When I start up the app, and do nothing, the log will output up to the  internet_option_send/receive_timeout/data_send_timeout 190000

The  app starts up with a login window.  Username entry box, password entry  box, ok button and cancel.  Clicking on OK regardless of username/pw  entered will result in the following msxml errors.

**Issue: Cannot log in through windows app in wine.**

Any help is appreciated, any comments appreciated.

---

