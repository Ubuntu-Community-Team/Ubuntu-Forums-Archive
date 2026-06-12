---
title: "Photoshop Segfault"
date: 2008-07-08
forum: Wine
---

### Post by venicia on 2008-07-08
Photoshop CS2 blatantly refuses to run under Wine. The window opens, the loading screen appears, but halfway through "Initializing..." I get a Segfault.

```
venicia@laptop2:~/.wine/drive_c/Program Files/Adobe/Adobe Photoshop CS2$ wine Photoshop.exe
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
err:ole:create_server class {a1f4e726-8cf1-11d1-bf92-0060081ed811} not registered
err:ole:CoGetClassObject no class object {a1f4e726-8cf1-11d1-bf92-0060081ed811} could be created for context 0x4
fixme:keyboard:UnregisterHotKey (0x7002e,99): stub
fixme:keyboard:RegisterHotKey (0x7002e,99,0x00000000,27): stub
fixme:font:WineEngRemoveFontResourceEx :stub
Segmentation fault
```

---

