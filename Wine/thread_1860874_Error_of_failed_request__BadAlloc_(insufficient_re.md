---
title: "Error of failed request:  BadAlloc (insufficient resources for operation)"
date: 2011-10-15
forum: Wine
---

### Post by demon_spells on 2011-10-15
Hi, 
I'm trying to run CCS PCWHD 4.114 and 4.048 on Ubuntu 11.10 using wine

it installs fine, when I run Pcw.exe .. it runs for like 2 seconds then disappears


```
wine ./Pcw
fixme:win:EnumDisplayDevicesW ((null),0,0x32f788,0x00000000), stub!
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -120, std (d/m/y): 28/10/2011, dlt (d/m/y): 1/04/2011
fixme:shell:DoEnvironmentSubstA ("%PROGRAMFILES%", 255) stub
fixme:shell:DoEnvironmentSubstA ("%APPDATA%", 255) stub
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:win:LockWindowUpdate (0x1008a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:dwmapi:DwmIsCompositionEnabled 0x32f99c
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Serial number of failed request:  858354
  Current serial number in output stream:  858507

```

any help?

---

### Post by demon_spells on 2011-10-15
anything?

---

