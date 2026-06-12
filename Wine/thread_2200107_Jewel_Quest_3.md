---
title: "Jewel Quest 3"
date: 2014-01-17
forum: Wine
---

### Post by nintendo.joe.fareb on 2014-01-17
I'm trying to get Jewel Quest 3 working on WINE but it isn't. This is the output from the terminal:
```

joe:Jewel Quest III$ ./JewelQuest3.exefixme:win:EnumDisplayDevicesW ((null),0,0x33f778,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f7e0,0x00000000), stub!
wine: Call from 0x7b83ac5f to unimplemented function msvcr80.dll._crt_debugger_hook, aborting
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.
joe:Jewel Quest III$ 

```
It appears to be a problem with msvcr80.dll. That file is in the directory but I have no way to find what's wrong with it. I've tried uninstalling it and reinstalling it. If someone has it working please can they send the DLL/ tell me how to fix it?
(it's ubuntu 13.10 and wine 1.4.1 btw)

---

### Post by Mark Phelps on 2014-01-19
The link is to the WineHQ wep page for the game -- but I must tell you that a Silver rating makes it all but unplayable:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=10647]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=10647")

---

