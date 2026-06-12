---
title: "tomb raider anniversary"
date: 2008-02-11
forum: Wine
---

### Post by banished_one on 2008-02-11
I cant install the game, i run the exe with wine via terminal but i get a securom error. I found something about this on the wine website but im not sure what to do with it [http://bugs.winehq.org/attachment.cgi?id=8235](http://bugs.winehq.org/attachment.cgi?id=8235)
Or a TRA installation guide would be great :)

---

### Post by Sockerdrickan on 2008-02-11
Are you really running WINE 0.9.55? :D

---

### Post by mutation on 2008-02-11
I have tomb raider anniversary running at home and from what i remember i have to launch it from the command prompt and not the shortcut that is created.

---

### Post by banished_one on 2008-02-11
> **Tux0r said:**
> Are you really running WINE 0.9.55? :D

well no 0.9.54 do i need the .55 to make it work ?

btw this is what i get after running tra.exe

fixme: spoolsv:serv_main (0 (nil))
fixme: process:IsWow64Process (0xffffffff 0x221ad34) stub!
fixme: ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x221a520,0x00000004,0x221a51c) Unknown information class
fixme: process:IsWow64Process (0xffffffff 0x221a85c) stub!
fixme: process:IsWow64Process (0xffffffff 0x221a85c) stub!
fixme: ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme: ntdll:NtQueryObject Unsupported information class 3
fixme: debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x221940c): Stub!
fixme: win:EnumDisplayDevicesW ((null),0,0x22192b0,0x00000000), stub!

---

### Post by wingnux on 2008-02-11
A no-cd patch may help.

---

### Post by banished_one on 2008-02-11
wohoo works like a charm 

many thanks

---

