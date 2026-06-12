---
title: "Cortex Command 19"
date: 2007-12-30
forum: Wine
---

### Post by jasonpeinko on 2007-12-30
Im trying to get cortex command build 19 to work with wine, but it does not work installation goes fine but when i try to play it, it just sits there, when i try running from terminal i get a Segmentation fault (core dumped)


build 18 worked great btw.

my guess as too why it is not working is because of the registration system any help to get this working would be greatly appreciated

---

### Post by petriborg on 2008-01-15
I'd like to see this too.
I was trying to get the new build 20 working, but no joy.

Install went fine, no problems, but running game is a bust.

```

trace:loaddll:load_builtin_dll Loaded L"KERNEL32.dll" at 0x7b820000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Data Realms\\Cortex Command\\Cortex Command.exe" at 0x400000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\advapi32.dll" at 0x7ec80000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\gdi32.dll" at 0x7ecd0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\user32.dll" at 0x7ed70000: builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "krnl386.exe" : builtin
trace:dll:fill_init_list (krnl386.exe) - START
trace:dll:fill_init_list (krnl386.exe) - END
trace:dll:NE_CallDllEntryPoint Calling krnl386.exe DllEntryPoint, cs:ip=100f:1e43
trace:loaddll:MODULE_LoadModule16 Loaded module "system.drv" : builtin
trace:dll:fill_init_list (system.drv) - START
trace:dll:fill_init_list (system.drv) - END
trace:loaddll:MODULE_LoadModule16 Loaded module "gdi.exe" : builtin
trace:dll:fill_init_list (gdi.exe) - START
trace:dll:fill_init_list (gdi.exe) - END
trace:loaddll:MODULE_LoadModule16 Loaded module "user.exe" : builtin
trace:dll:fill_init_list (user.exe) - START
trace:dll:fill_init_list (user.exe) - END
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winex11.drv" at 0x7eaa0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\imm32.dll" at 0x7de50000: builtin


```

---

### Post by jasonpeinko on 2008-01-17
yeah, its disapointing, it has to be his lame sucirity addon

---

### Post by petriborg on 2008-01-17
I would like to confirm that I was able to get build 18 working in the current wine, 0.9.53.

Its sad to see his "security" thing break this, it was a pretty fun game :(

---

### Post by jasonpeinko on 2008-01-18
yeah, i hate how that works, i was so looking forward to playing it, it is stupid that it is his security is the thing that breaks it, i think it could have something to do that it registers the key to the computer.

---

### Post by petriborg on 2008-01-18
> **jasonpeinko said:**
> yeah, i hate how that works, i was so looking forward to playing it, it is stupid that it is his security is the thing that breaks it, i think it could have something to do that it registers the key to the computer.

How did you figure that out? I've been all over the net trying to figure out what was bloody wrong w/ Cortext that it would act this way. If you run wine in +all debug mode it actually looks like it exceptions out. The only fixme/err that shows up in the log appears to be a printer-service type message.

---

