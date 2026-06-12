---
title: "[SOLVED] Winecfg error msg"
date: 2008-01-06
forum: Wine
---

### Post by brett611 on 2008-01-06
I just installed wine for the first time and ran winecfg.  Got the following error msgs.  Don't care about printer related errors but at the bottom there are errors that seem like I should care about them...
thx


wine: creating configuration directory '/home/brett/.wine'...
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
wine: '/home/brett/.wine' created successfully.
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

---

### Post by hikaricore on 2008-01-06
> **brett611 said:**
> 
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0


Aside from the quoted section, there really are no errors in the output you posted.
fixme messages are normal output from WINE when running most titles.

---

### Post by brett611 on 2008-01-07
Awesome news.  Nothing like solving a problem due to it not being a problem.  Thanks!

---

