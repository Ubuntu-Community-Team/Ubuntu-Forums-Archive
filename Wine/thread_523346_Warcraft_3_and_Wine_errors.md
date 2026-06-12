---
title: "Warcraft 3 and Wine errors"
date: 2007-08-11
forum: Wine
---

### Post by supazio on 2007-08-11
When i try to run The Frozen Throne, I get this:
```
supazio@dellbox:~$  wine /home/supazio/.wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1b3430) : stub, simulating 64MB for now, returning 64MB left
err:seh:setup_exception stack overflow 1256 bytes in thread 000f eip b7dbadc3 esp 00240b18 stack 0x241000-0x350000
err:ntdll:RtlpWaitForCriticalSection section 0x110020 "heap.c: main process heap section" wait timed out in thread 0010, blocked by 000f, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x110020 "heap.c: main process heap section" wait timed out in thread 0010, blocked by 000f, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc2f2e0
```Anyone know what to do?

---

### Post by cogadh on 2007-08-11
Do you have an accelerated driver for your video card?

---

