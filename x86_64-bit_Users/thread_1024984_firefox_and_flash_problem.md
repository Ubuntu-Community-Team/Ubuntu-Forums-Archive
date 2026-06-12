---
title: "firefox and flash problem"
date: 2008-12-29
forum: x86 64-bit Users
---

### Post by zekopasa on 2008-12-29
i was using firefox without any problem until i installed new updates of flash plugins.

when i open a flash application, cpu reaches %100, i cant watch video streams (youtube etc...), and sometimes firefox smashes up and i restart the system.

i installed shockwave flash 9.0 and 10.0 plugins and tried to install swfdec 0.84 but cant succeed -cant find libgtk2.0.dev-.

waitin for your helps

thank you.

---

### Post by Coreigh on 2008-12-29
Start Firefox in safe mode
```
firefox -safe-mode
```

Disable the Flash plugin; Tools>>Addons, Plugins Tab

The Flash module resides in your home folder in .mozilla/plugins

Close Firefox and run in "normally", 'Does it work now?' Reinstall Flash or an earlier version (9 instead of 10)


EDIT:
were you installing swfdec 0.84 from an apt package? or other means? Uninstall it too. if it is a package then 
```
sudo dpkg --purge swfdec
```
(Or whatever the package name is.)

---

