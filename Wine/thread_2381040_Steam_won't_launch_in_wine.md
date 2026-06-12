---
title: "Steam won't launch in wine"
date: 2017-12-26
forum: Wine
---

### Post by foffle111 on 2017-12-26
Hi all, couldn't find a solved version of this problem, so thought I'd try my luck posting. 

I downloaded steam for windows to run in wine, and although it seemed to install fine with no errors, it does not start. there are no error messages and it doesn't even reach the updating screen. When I click on the short cut, the cursor turns into a loading icon for a few seconds, but after that nothing happens. 

I tried running it in terminal using this:
wine "c:\program files (x86)\Steam\Steam.exe"

 and got this error:

fixme:ver:GetCurrentPackageId (0x33e470 (nil)): stub
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented DisconnectEx
net.cpp (263) : Fatal Assertion Failed: PlatformSocketsInit failed, error [no name available] (10045)
net.cpp (263) : Fatal assert failed: net.cpp, line 263.  Application exiting.

Assert( Fatal Assertion Failed: PlatformSocketsInit failed, error [no name available] (10045) ):net.cpp:263

fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f006bd0, 0x3f043cf0, 0x3f043ce8
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f006bd0, 0x3f043d28, 0x3f043d20
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f006bd0, 0x3f043dd0, 0x3f043dc8
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f006bd0, 0x3f043d60, 0x3f043d58
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f006bd0, 0x3f043d98, 0x3f043d90
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:ver:GetCurrentPackageId (0x8ddf2c (nil)): stub
_ExitOnFatalAssert
soz@Soz:~$ fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub

Any advice?

---

### Post by steamedwine on 2018-01-06
I'm having the very same problem, down to the same terminal error message. My Wine version of Steam used to work just fine until not too long ago. The only solution I could find online was to remove the *ClientRegististry.blob* file from  Steam's root folder, but I noticed it doesn't exist there. I created this account just to share this problem on this thread.

Solving this would be really useful, since I'm running out of disk memory and I need to uninstall some Wine-based Steam games, but I'm afraid of uninstalling them outside of Steam because I'm not sure I can do a clean uninstall. Any advice would be appreciated.

---

### Post by steamedwine on 2018-01-06
I also forgot to mention that Wine works just fine with other non-Steam programs. Just anything that requires the Wine version of Steam won't launch.

---

### Post by sebastian1978 on 2018-01-24
Hi All!

Steam runs fine in Wine. Just install Winetricks and type in terminal:
> winetricks steam

Winetricks will install all needed libs. Also add in shortcut command "-no-cef-sandbox" wihout quotes. 

For example my string in Steam shortcut:
> env WINEPREFIX="/home/igor/.wine" /opt/wine-staging/bin/wine C:\\windows\\command\\start.exe /Unix /home/igor/.wine/dosdevices/c:/users/Public/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081;\ &#1089;&#1090;&#1086;&#1083;/Steam.lnk -no-cef-sandbox


All info about Steam in Wine [https://developer.valvesoftware.com/wiki/Steam_under_Linux#Step_2:_installing_steam](https://developer.valvesoftware.com/wiki/Steam_under_Linux#Step_2:_installing_steam)

---

### Post by steamedwine on 2018-02-04
Hi sebastion, thank you for the long-awaited response. I followed both your steps, but while installing winetricks, I got this message in the terminal:
```

[2018-01-28 14:27:52] Download complete.
[2018-01-28 14:27:52] uninstalled manifest found in C:\Program Files (x86)\Steam (WINE)\package\steam_client_win32 (1).
[2018-01-28 14:27:52] Found pending update
[2018-01-28 14:27:52] Installing update...
[2018-01-28 14:27:53] Extracting package...
[2018-01-28 14:28:03] Installing update...
[2018-01-28 14:28:09] Failed to clean up after update, continuing...
[2018-01-28 14:28:09] Cleaning up...
[2018-01-28 14:28:09] Update complete, launching Steam...
[2018-01-28 14:28:09] Shutdown
fixme:ver:GetCurrentPackageId (0x33e470 (nil)): stub
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented DisconnectEx
net.cpp (263) : Fatal Assertion Failed: PlatformSocketsInit failed, error [no name available] (10045)
net.cpp (263) : Fatal assert failed: net.cpp, line 263.  Application exiting.

Assert( Fatal Assertion Failed: PlatformSocketsInit failed, error [no name available] (10045) ):net.cpp:263

fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f006bd0, 0x3f043cf0, 0x3f043ce8
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f006bd0, 0x3f043d28, 0x3f043d20
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f006bd0, 0x3f043dd0, 0x3f043dc8
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f006bd0, 0x3f043d60, 0x3f043d58
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f006bd0, 0x3f043d98, 0x3f043d90
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:ver:GetCurrentPackageId (0x8ddf2c (nil)): stub
_ExitOnFatalAssert
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub

```

I've tried running both the old and new desktop shortcuts of the Wine version of Steam, no results. :(

---

