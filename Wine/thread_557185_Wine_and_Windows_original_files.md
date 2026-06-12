---
title: "Wine and Windows original files"
date: 2007-09-22
forum: Wine
---

### Post by burnt water on 2007-09-22
I currently have a windows xp license and was wondering if it is possible just to use the window's dll's instead of wine's opensource versions?

---

### Post by DoktorSeven on 2007-09-22
For the core functionality, like low level stuff, DirectX, etc, no.  The Wine versions translate Windows system calls into equivalent Linux ones, so they can't be replaced. 

DLLs that are not implemented in Wine, though, can definately be copied over and used (for example, Visual Basic runtime DLLs and other similar ones).  

But if you're thinking that copying over DirectX DLLs to make it run better, it won't.  In fact, it won't run at all. :)

---

### Post by cogadh on 2007-09-22
Not entirely true. Wine does not have any built in implementation of the d3dx9_##.dll files and those can be copied into your Wine directory. They can sometimes help with Direct3D based games and they don't harm Wine at all. Additionally, nearly any Windows DLL can be used in place of the built in Wine DLLs. The only exceptions are kernel32.dll, gdi32.dll, user32.dll, and ntdll.dll. Those DLL files should _never_ be overridden. 

If you do choose to use a Windows native DLL in place of an existing Wine DLL, make sure you don't overwrite the Wine one. If the Windows DLL fails to work, you'll want to be able to get the Wine one back.

---

### Post by Dark Aspect on 2007-09-22
Just to butt in what would happen if I delete my windows folder in wine and copy and paste the one from an actually windows installation?

Despite almost losing 1.5GB would it make games/Applications work better?

---

### Post by hikaricore on 2007-09-22
> **Dark Aspect said:**
> Just to butt in what would happen if I delete my windows folder in wine and copy and paste the one from an actually windows installation?

Despite almost losing 1.5GB would it make games/Applications work better?


..... no

no no no no no no no

That is an absolutely terrible idea.

---

### Post by cogadh on 2007-09-23
Yeah, what he said. :)

Just because a Wine DLL *can* be overridden with a native Windows one, doesn't mean it *should* be. Some of the Wine DLLs are actually better than their Windows counterpart and replacing them will negatively impact Wine severely.

---

### Post by lisati on 2007-09-23
Be careful: Windows has its expectations about what information goes where in its system calls, and Linux has its own expectations. The challenge arises because what goes where is usually different between the OSes - which is why we have tools like Wine.

---

### Post by Rizado on 2007-09-23
> **cogadh said:**
> If you do choose to use a Windows native DLL in place of an existing Wine DLL, make sure you don't overwrite the Wine one. If the Windows DLL fails to work, you'll want to be able to get the Wine one back.Doesn't matter if you overwrite the files in windows/system32 because they are only there incase a program checks there for a file. Thoose files aren't even the real dlls, they are somewhere else.

---

### Post by cogadh on 2007-09-23
Yes the "real" DLLs are actually in /usr/lib/wine but you still shouldn't overwrite the DLLs in ~/.wine/drive_c/windows/system32 with native Windows DLLs. I've overwritten them in the past and changing or deleting the override settings in winecfg didn't set things back to the way they were. I believe it has something to do with how Wine determines DLL load order (I think the default is Native first, then Built-in), but I'm not really sure.

---

### Post by zzzzzZZZZzzz on 2007-09-23
Does a list of "safe to copy" or "Files that are beneficiary to copy" exist? If so where might it be found?

---

### Post by cogadh on 2007-09-23
Not that I am aware of, there is only the list of files you shouldn't override (kernel32.dll, gdi32.dll, user32.dll, and ntdll.dll). Basically you should really only override a DLL if an application run with Wine produces an error based on a particular DLL. When that happens, it may be worth it to try a Windows native DLL in place of the Wine one, to see if it will correct the problem. Otherwise, you shouldn't need to override any of them. 

Also, there are DLLs that are not implemented in Wine (like the D3D ones I mentioned above) which can be added to Wine when an application demands it. If no application has asked for it, don't bother adding it.

---

### Post by bliffle on 2007-09-26
Talking about DLLS....I'm trying to get a little XP app called "TotalMedia3" running under wine, and of course it blewup first time looking for "mfc42u.dll", which, IIRC is part of Microsoft Foundation Classes (thus the 'mfc') which is used by many apps and programs, so it's not an oddball.

I don't have the XP big library "C:\windows\system\system32..." mounted yet so that's what I'll do later tonight. Probably will solve my problem.

While spelunking around I found that I now have a directory called "/usr/lib/wine/" with a bunch of files with names like "msvidc32.dll.so", which I'm assuming was installed by Synaptic when I installed wine itself.

I think that "msvidc32.dll.so" is a system object with a bunch of dll equivalents bundled together.

On another experimental computer it seems as though wine looked around and found the "C:/windows/system/system32" directory sitting on my XP partition and actually used that when I brought up XP Firefox 2.0.0.7 on that 2nd computer.

I'm pretty impressed by this so far.

Tonight I'll improve the dll environment and try "TotalMedia3" again and if it works I've solved one of the few problems remaining to get myself totally off XP and onto ubuntu! As it is I seldom use XP anymore and only a couple of little nits remain to be solved.

This is really great!

All Hail the power of ubuntu!

---

### Post by cogadh on 2007-09-26
When you first run Wine it creates a hidden ".wine" directory in your home folder. The ".wine/drive_c/windows/system32" folder is the one that should be used for DLL overrides. Don't set Wine to access your XP system32 folder directly, as it will not work right. If you choose to use Windows native DLLs, copy them from your Windows system32 folder into the Wine system32 folder, then use winecfg to set a Library override for each DLL copied.

---

### Post by bliffle on 2007-09-26
Thanks, cogadh.

---

### Post by bliffle on 2007-09-26
Oh oh. The plot thickens.

Per cogadhs caution a couple posts ago, I figured it shouldn't be necessary to have my old XP system anywhere in sight, that wine should establish it's own libraries.

So I didn't hookup the old XP.

But then, where is that needed "mfc42u.dll" that TotalMedia3 is looking for? It's not in the library wine has setup:

john@JHT40UUU:~$ **ls -l .wine/drive_c/windows/system32**
total 2316
-rw-r--r-- 1 john john   2488 2007-06-05 18:42 advapi32.dll
-rw-r--r-- 1 john john   1032 2007-06-05 18:42 advpack.dll
-rwxr-xr-x 1 john john 199960 2007-06-05 18:42 cmd.exe
-rw-r--r-- 1 john john  56736 2007-06-05 18:42 comctl32.dll
-rw-r--r-- 1 john john 377240 2007-06-05 18:42 comdlg32.dll
-rwxr-xr-x 1 john john   1032 2007-06-05 18:42 control.exe
-rw-r--r-- 1 john john  31488 2007-06-05 18:42 crypt32.dll
-rw-r--r-- 1 john john   2456 2007-06-05 18:42 d3d8.dll
-rw-r--r-- 1 john john   2456 2007-06-05 18:42 d3d9.dll
-rw-r--r-- 1 john john   1032 2007-06-05 18:42 dbghelp.dll
-rwxr-xr-x 1 john john   1032 2007-06-05 18:42 ddhelp.exe
-rw-r--r-- 1 john john   2504 2007-06-05 18:42 ddraw.dll
drwxr-xr-x 2 john john   4096 2007-06-05 18:42 drivers
-rw-r--r-- 1 john john   2512 2007-06-05 18:42 dsound.dll
-rw-r--r-- 1 john john   1032 2007-06-05 18:42 dsound.vxd
-rwxr-xr-x 1 john john   1032 2007-06-05 18:42 explorer.exe
-rw-r--r-- 1 john john   2432 2007-06-05 18:42 gdi32.dll
-rw-r--r-- 1 john john  10648 2007-06-05 18:42 hhctrl.ocx
-rw-r--r-- 1 john john   1032 2007-06-05 18:42 imaadp32.acm
-rw-r--r-- 1 john john   1032 2007-06-05 18:42 imagehlp.dll
-rw-r--r-- 1 john john 427852 2007-06-05 18:42 kernel32.dll
-rw-r--r-- 1 john john   1032 2007-06-05 18:42 msadp32.acm
-rw-r--r-- 1 john john   1032 2007-06-05 18:42 msg711.acm
-rw-r--r-- 1 john john  18616 2007-06-05 18:42 msi.dll
-rwxr-xr-x 1 john john   3408 2007-06-05 18:42 msiexec.exe
-rw-r--r-- 1 john john   2456 2007-06-05 18:42 msvcrt.dll
-rwxr-xr-x 1 john john  87752 2007-06-05 18:42 notepad.exe
-rw-r--r-- 1 john john   2468 2007-06-05 18:42 ntdll.dll
-rw-r--r-- 1 john john   4224 2007-06-05 18:42 ole32.dll
-rw-r--r-- 1 john john   4588 2007-06-05 18:42 oleaut32.dll
-rw-r--r-- 1 john john   2508 2007-06-05 18:42 olepro32.dll
-rw-r--r-- 1 john john   2472 2007-06-05 18:42 opengl32.dll
-rwxr-xr-x 1 john john 100620 2007-06-05 18:42 progman.exe
-rw-r--r-- 1 john john   2496 2007-06-05 18:42 quartz.dll
-rwxr-xr-x 1 john john   2464 2007-06-05 18:42 regsvr32.exe
-rw-r--r-- 1 john john   2488 2007-06-05 18:42 riched20.dll
-rw-r--r-- 1 john john   2496 2007-06-05 18:42 riched32.dll
-rw-r--r-- 1 john john   2472 2007-06-05 18:42 rpcrt4.dll
-rw-r--r-- 1 john john   8660 2007-06-05 18:42 setupapi.dll
-rw-r--r-- 1 john john  36708 2007-06-05 18:42 shdocvw.dll
-rw-r--r-- 1 john john 393336 2007-06-05 18:42 shell32.dll
-rw-r--r-- 1 john john   2556 2007-06-05 18:42 shfolder.dll
-rw-r--r-- 1 john john  10160 2007-06-05 18:42 shlwapi.dll
-rw-r--r-- 1 john john  23388 2007-06-05 18:42 urlmon.dll
-rw-r--r-- 1 john john  56664 2007-06-05 18:42 user32.dll
-rw-r--r-- 1 john john   2484 2007-06-05 18:42 version.dll
-rw-r--r-- 1 john john  17140 2007-06-05 18:42 wininet.dll
-rw-r--r-- 1 john john 284056 2007-06-05 18:42 winmm.dll
-rw-r--r-- 1 john john   9524 2007-06-05 18:42 winspool.drv
-rwxr-xr-x 1 john john   1032 2007-06-05 18:42 winver.exe
-rw-r--r-- 1 john john   2444 2007-06-05 18:42 ws2_32.dll
-rw-r--r-- 1 john john   2444 2007-06-05 18:42 wsock32.dll
john@JHT40UUU:~$ 

And XP FireFox 2.9.9.7 works on the other computer, which has the same library.

So I'm a little bit stumped. I can try grabbing "mfc42u.dll" from an XP system and put it in "wine/drive_c/windows/system32", but then that will be a pure XP not a new wine layer dll, so will it work? I don't know. Maybe the code within "mfc42u.dll" will call dll's which are in the wine layer..

There are plenty other traditional windows dlls that are missing, too.

Seems to me that the old XP "system32" library should be concatenated behind "wine/drive_c/windows/system32" to catch any calls that fall thru the wine dll library, so they can , in turn, call code in the "wine/drive_c/windows/system32".

Hmmmmm. Maybe I'll try that.

here's the full list of missing traditional XP dlls, so far;

MFC42u.DLL
MSVCIRT.dll 

I must have missed something. I bet I didn't copy alll the stuff that the app install put on my XP HDD. I'll go check.

Pay no attention to the dummy in this corner. For now.

---

### Post by cogadh on 2007-09-27
As I said, if you want to use a windows native DLL, just copy it into the .wine/drive_c/windows/system32 directory and set a Library override in winecfg. It doesn't matter if Wine didn't originally have the DLL, this is one of those cases where a Windows native DLL is definitely required. I've run into it with mfc42.dll and msvcirt.dll myself before.

---

### Post by bliffle on 2007-09-27
I figured what I ought to do is run the 'wine setup.exe' for the TotalMedia app, because that worked for the firefox install I had done with wine on the other computer. Then, perhaps, wine would route any installed dlls to the right place. But that effort stalled in the DirectX install, so I forced past by declining to install the directX in the 'setup.exe' since I have DirectX libraries on the XP HDD when I need to copy them.

Even so, the TotalMedia 'setup.exe' stopped in the middle of something and wouldn't budge.

---

### Post by cogadh on 2007-09-27
Never, *ever* install DirectX in Wine. Wine already has its own DirectX library implementation and trying to install the actual DirectX will often break it. 

Also, unless an application provides its own DLLs, it won't put anything in the system32 directory (sometimes DLLs will be installed in the application's directory). Usually apps that require a particular MS DLL will expect the correct DLL to already be there, if it isn't, then an error will be produced that can tell you what DLL you might need to copy from Windows into the Wine directory.

Basically, you should:
[LIST=1]
[*]Try to install the application - "wine setup.exe"
[*]If the install fails, check the terminal for any informative errors
[*]If those errors indicate a fault in a particular DLL or a missing DLL, try copying that DLL from Windows system32 directory into the Wine system32 directory
[*]Set a library override for the DLL in winecfg
[*]Re-run the install again
[*]Rinse and repeat as necessary
[/LIST]

You might have to do some interpretation of the errors to determine what DLL is actually required. For example, when I encountered the problem where I needed to copy msvcirt.dll into Wine, the error didn't actually say that msvcirt.dll was at fault, but it actually indicated that a different existing DLL needed something from msvcirt.dll that it couldn't find.

When your last attempt to install failed, were there any error messages produced in the terminal?

---

### Post by bliffle on 2007-09-27
Yes, I got the following in terminal, as well as a frozen screen:

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:process:IsWow64Process (0xffffffff 0x33df08) stub!

---

### Post by cogadh on 2007-09-27
It looks like the app was trying to install a Windows driver. If that is the case, it will never work, since Windows drivers can't be used in Wine.

---

### Post by bliffle on 2007-10-04
> **cogadh said:**
> It looks like the app was trying to install a Windows driver. If that is the case, it will never work, since Windows drivers can't be used in Wine.

Can windows drivers be used in VMware or VirtualBox?

Is this related in any way to the use of "ndiswrapper" for modem drivers?

---

