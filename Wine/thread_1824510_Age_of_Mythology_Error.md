---
title: "Age of Mythology Error"
date: 2011-08-13
forum: Wine
---

### Post by laagamer on 2011-08-13
Hello! 

I'm currently trying to run AOM on my laptop with Ubuntu 9.10

I'm trying to run it through Wine 1.3.15

I have winecfg set to "Windows XP" and sound drivers set to "OSS".

When I try to run through the desktop icon, the Age of Mythology logo comes up and freezes there permanently.

I also used  the command "winetricks corefonts vcrun6" from this site ([http://www.bytechip.com/2011/06/how-...blems-in-wine/](http://www.bytechip.com/2011/06/how-...blems-in-wine/)) on the recommend someone gave in an old AOM post I read to try and solve the DLL problems. This resulted in the 2nd line of the code to appear. 

When I try to run AOM through the terminal I get three errors which are:


nick@nick-laptop:~/AOMD1/aom$ wine aom.exe
fixme: ole: DllRegisterServer stub
err:module:import_dll Library RockallDLL.dll (which is needed by L"H:\\AOMD1\\aom\\aom.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\AOMD1\\aom\\aom.exe" failed, status c0000135




If anyone knows what I can do about this I would greatly appreciate it! I'm honestly stumped. Not a clue what any of those things are. =/

Thanks!

---

### Post by laagamer on 2011-08-14
Bump. Help Please? ):P

---

### Post by laagamer on 2011-08-18
B-B-B-Bump!

---

### Post by raja.genupula on 2011-08-19
hey man i read that  playonlinux is good for playing games of .exe in ubuntu . try it once .

---

### Post by laagamer on 2011-08-22
Thanks man! 

I'll try that once I get back to civilization with internet! lol

I just solved my original problem after downloading the DDL file mentioned above and placing it in the disk folder. That is what solved the pathway error I'm assuming as well.

Only problem is now, when I start AOM up, the original logo screen freezes right there and doesn't change.

Running through terminal I get a regular start up, but then freezes and terminal says:

fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB: (0x1353b8 )
fixme:msctf:LangBarMgr_ShowFloating STUB: (0x1353b8 )
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x20020, 0x134660) : stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x134660) : semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec58,0x00000000), stub!

I have no idea what any of that even is! :(

Any help would be greatly appreciated guys! And thanks again dude I'll try running it through that Playonlinux ASAP.

---

