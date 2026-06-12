---
title: "Wine (9.18) and Photoshop 5.5"
date: 2006-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mooie on 2006-08-08
I just tried to install an old win copy of photoshop 5.5 using wine 9.18 using dapper 64-bit. the install went fine, but every time I try to run the program i get the error
```
ALSA lib ../../../src/seq/seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:palette:GetICMProfileA (0x580, 0x33dda8, 0x33dfac): partial stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33da1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x33da1c,0x00000000), stub!
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  213
  Current serial number in output stream:  213

```
there wasn't much info on this issue on the forums...  any info you could give would be greatly appreciated.

---

### Post by Mooie on 2006-08-09
ImageReady is working fine though...  I would REALLY like to have photoshop working, and I read about sombody having the same issue, but there are no sollutions that I have seen.  :confused:

---

### Post by RAOF on 2006-08-09
Such is the fate of Wine, sadly.  I'm rather more surprised when something **works** under wine than when something doesn't.

---

### Post by Mooie on 2006-08-09
yep, unfortunately...   its the only program I actually wanted wine for...  what programs actually work w/ wine? then I could tell myself that it was on my machine for a reason ](*,)

---

### Post by RAOF on 2006-08-09
Check out [winehq.org](winehq.org).  They've got a database of programs known to work fine, known to work with minor gotchas, and known to just plain fail.

---

### Post by Mooie on 2006-08-11
I checked the site, though there was nothing there of any use to  me, it said that it should install normally and "just work"...   oh well, i dont really need it that much anyways...:-(

---

