---
title: "CDEMU daemon will not start"
date: 2009-06-06
forum: x86 64-bit Users
---

### Post by phatbastard on 2009-06-06
I am using kubuntu jaunty x64 and cannot get the cdemu daemon started. I have installed cdemu-daemon, cdemu-client and both installed with no errors using deb packages.

phatbastard@phatbastard-desktop:~$ cdemu status
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon (bus: 'session')!

phatbastard@phatbastard-desktop:~$ cdemud
Starting daemon in local mode with following parameters:
 - num devices: 1
 - ctl device: /dev/vhba_ctl
 - audio driver: null
 - bus type: system
cdemud: cdemud_daemon_initialize: failed to request name on system bus!
Daemon initialization failed: Name request on D-BUS failed.

---

