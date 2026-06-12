---
title: "Wine 1.4 + Terraria Error with .NET 4"
date: 2012-10-14
forum: Wine
---

### Post by Dudemister1999 on 2012-10-14
Hello, Ubuntu Forums! I have a slight problem. As you may notice, I am new to this forum, but I have had experience on others, so I will make this short and sweet :P



Here is my error:
```

alex@alex-Satellite-L305:~/Downloads/Terraria 1.1.2$ wine Terraria.exe 
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:module:GetModuleHandleExW should pin refcount for 0x79000000
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework.Game"

Unhandled Exception: fixme:advapi:RegisterTraceGuidsW (0xb1c47a, (nil), {8e9f5090-2d75-4d03-8a81-e5afbf85daf1}, 1, 0x32bc4c, (null), (null), 0xe626b8,): stub
System.IO.FileNotFoundException: Could not load file or assembly 'Microsoft.Xna.Framework.Game, Version=4.0.0.0, Culture=neutral, PublicKeyToken=842cf8be1de50553' or one of its dependencies. Exception from HRESULT: 0x80070002
   at Terraria.Program.Main(String[] args)

```I installed .NET4.0 using Winetricks.

I installed WINE 1.4 a few months ago. It updated once, I believe.

So, any idea on how to change this?

Thanks for your time and consideration,
-Alex / Dudemister1999

---

### Post by buntupanda1 on 2012-10-15
are you using steam for it  wine tricks or wine to install steam. and what version of Ubuntu are you using. i have terraria but i am using 11.10. did you get terraria for free from online storage if you did its most likely its corrupt. if you used steam right click terraria properties set launch options and type this in: -dxlevel 81. try reinstalling terraria it looks like a file is corrupt

---

