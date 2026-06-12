---
title: "Is there something fishy in this WINE output?"
date: 2012-05-11
forum: Wine
---

### Post by layers on 2012-05-11
So, when I try running Altium Designer under WINE, if I try looking through the footprint images, it hangs and freezes. But I don't know why. I ran it through terminal, does anyone see anything funny in it?except the smilies?> ibo@ibo-VPCF130FD:~$ wine '/home/ibo/.wine/drive_c/Program Files/Altium/AD 10/DXP.EXE' 
fixme:win:DisableProcessWindowsGhosting : stub
fixme:keyboard:RegisterHotKey ((nil),1,0x00000003,2D): stub
fixme:advapi:LsaOpenPolicy ((null),0x32fd50,0x00000001,0x32fd6c) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
err:ole:CoGetClassObject class {1a960ece-0e57-4a68-b694-8373114f1ff4} not registered
err:ole:create_server class {1a960ece-0e57-4a68-b694-8373114f1ff4} not registered
err:ole:CoGetClassObject no class object {1a960ece-0e57-4a68-b694-8373114f1ff4} could be created for context 0x5
err:ole:CoGetClassObject class {82c5ab54-c92c-4d52-aac5-27e25e22604c} not registered
err:ole:create_server class {82c5ab54-c92c-4d52-aac5-27e25e22604c} not registered
err:ole:CoGetClassObject no class object {82c5ab54-c92c-4d52-aac5-27e25e22604c} could be created for context 0x5
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2bc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f280,0x00000000), stub!
could not find the resource:a148e300-5740-11d1-a904-080036aaa103.Location
fixme:imm:ImmReleaseContext (0x204fe, 0x15dde0): stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:InternetAttemptConnect Stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:ntdll:server_ioctl_file Unsupported ioctl 9c040 (device=9 access=3 func=10 method=0)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:advapi:LsaOpenPolicy ((null),0x32f9e0,0x00000001,0x32f9fc) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:InternetAttemptConnect Stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f730,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:advapi:LsaOpenPolicy ((null),0x32f95c,0x00000001,0x32f978) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0x32f9e0,0x00000001,0x32f9fc) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
could not find the resource:a148e300-5740-11d1-a904-080036aaa103.Location
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:INET_QueryOption Stub for 43
fixme:wininet:INET_QueryOption Stub for 44
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:WINNLSEnableIME hUnknown1 0x180544 bUnknown2 0: stub!
fixme:win:WINNLSEnableIME hUnknown1 0x180544 bUnknown2 -1: stub!
Terminated
ibo@ibo-VPCF130FD:~$ 


---

### Post by oldos2er on 2012-05-11
Moved to Wine.

---

### Post by forrestcupp on 2012-05-11
I don't know what version of anything you're running, but for one version, Wine's appdb says you should install these things in winetricks:

> You need to install the following with winetricks:
dx9 for the DirectX accelerated graphics (helps with ghosting of PCB lines)
dcom98 tahoma corefonts mdac28 mdac27 mfc42 dotnet20

---

### Post by cogadh on 2012-05-11
You can ignore all those "fixme" errors, they are just developer notes about functions still not implemented in Wine (you can't fix them unless you are going to code and submit patches to Wine). The "err" errors are the real problems and most of those look like they would be addressed by installing the dcom, mdac, mfc and dotnet packages with winetricks that forrestcupp mentioned.

---

### Post by arune on 2012-09-19
I'm also running Altium with wine under Ubuntu 12.04 and have done so for about a year. As I'm working with Altium I have also documented (at company wiki) how to set up and run it, in case any colleague needs to do the same.
With this post I'm now subscribing to this thread, just ask if there is any issue.

I installed wine1.5 with this [PPA]("https://launchpad.net/~ubuntu-wine/+archive/ppa").
sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.5 winetricks tahoma corefonts mdac28 mdac27 mfc42 ie6 dotnet20 msxml4 ie8

To get rid of most warnings I run Altium with this command:
WINEDEBUG=fixme-all,err-all,warn+cursor,-all wine "/home/arune/.wine/drive_c/Program Files/Altium/AD 10/DXP.EXE"
That also makes Altium run faster.

Could be a good idea to disable compiz in Ubuntu if you are having problems with computer freezes.

I also needed to change Repository location under Account preferences -> Installation Manager to [http://installation.altium.com](http://installation.altium.com)

---

