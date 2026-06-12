---
title: "Game -Wine"
date: 2007-09-09
forum: Wine
---

### Post by DougieFresh4U on 2007-09-09
I have installed a game using wine. A few months back it worked great. I have had to redo it because of a fresh install. When I click it to open , it comes up and stays for a few seconds then disappears. What may be causing this to happen/
Thanks

---

### Post by noerrorsfound on 2007-09-09
Did you... take a picture of your monitor?

Alt | Print Screen didn't work for you?

---

### Post by kostkon on 2007-09-09
Try to run it from the terminal and see what error messages you get. 

I assume that now you are trying to run the game with a newer version of *Wine* and maybe it does not work with it. Sometimes this happens with *Wine*. A newer version of it breaks some games that worked with the previous version. It's rare, but it happens.

---

### Post by Ferrat on 2007-09-09
could you start the game in a terminal window then write the output you get? =)

Edti: Damn kostkon, took you 5min to send that in? wasn't there before ^^

---

### Post by DougieFresh4U on 2007-09-09
> **Ferrat said:**
> could you start the game in a terminal window then write the output you get? =)

Edti: Damn kostkon, took you 5min to send that in? wasn't there before ^^

Because game uses 'wine', what would I type in terminal, Sorry for sounding like a "dummy":confused:

---

### Post by Urilockz on 2007-09-09
You should type...

> wine game

---

### Post by cogadh on 2007-09-09
Just to be a little more specific, the proper usage of Wine is like this:
```
cd .wine/drive_c/Program\ Files/game/directory/
wine game.exe
```
Change the "game/directory" and "game.exe" to match your actual game. If you run the game like this, any error messages produced by Wine will be output to the terminal, which you can then copy/paste here. Please make sure you use the forum "[code]" tags when you post the output, it will make it much more readable.

---

### Post by DougieFresh4U on 2008-08-02
> **cogadh said:**
> Just to be a little more specific, the proper usage of Wine is like this:
```
cd .wine/drive_c/Program\ Files/game/directory/
wine game.exe
```
Change the "game/directory" and "game.exe" to match your actual game. If you run the game like this, any error messages produced by Wine will be output to the terminal, which you can then copy/paste here. Please make sure you use the forum "[code]" tags when you post the output, it will make it much more readable.

Ok, so the name of the game is  Mah Jong Medley
So what would the _exact_ code in terminal be for this to attempt opening? It's in the c/ folder in wine

---

### Post by DougieFresh4U on 2008-08-03
dougie@DougiesLeanMachine:~$ wine mah jong medley.exe
fixme:atl:AtlModuleInit SEMI-STUB (0x4042c8 0x404578 0x400000)
fixme:ole:CoInitializeSecurity (0x12ae80,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"Viewpoint Manager Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x7e2f3984,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
wine: could not load L"C:\\windows\\system32\\mah.exe": Module not found
dougie@DougiesLeanMachine:~$ fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot

---

### Post by stinger30au on 2008-08-03
> **DougieFresh4U said:**
> dougie@DougiesLeanMachine:~$ wine mah jong medley.exe

you can *NOT* have spaces in your file names at the shell prompt or linux will have a spit.

if oyur file names have spaces in them, one way round this is to shove the files inside qoutes. your command should look like this instead

wine "mah jong medley.exe"

copy and paste everything above and it should  go fine

---

### Post by DougieFresh4U on 2008-08-03
> **stinger30au said:**
> you can *NOT* have spaces in your file names at the shell prompt or linux will have a spit.

if oyur file names have spaces in them, one way round this is to shove the files inside qoutes. your command should look like this instead

wine "mah jong medley.exe"

copy and paste everything above and it should  go fine

The code provided worked, thanks.
But, now I am back to the origanal post and screenshot provided. It starts to load then disappears

---

### Post by ouman63 on 2008-08-03
Hello all, 
I installed Doom 3 with wine and it worked great for a few days, then stopped working.  When I try to run the executable in wine, a dialog pops up with the following message:

DOOM 1.3.1302 win-x86 May 12 2005 10:40:52
2001 MHz Intel CPU with MMX & SSE & SSE2 & SSE3
3040 MB System Memory
64 MB Video Memory
Winsock Initialized
Found interface: eth0 eth0 - 192.168.0.13/255.255.255.0
Found interface: wlan0 wlan0 - /
Sys_InitNetworking: adding loopback interface
doom using MMX & SSE & SSE2 & SSE3 for SIMD processing
enabled Flush-To-Zero mode
enabled Denormals-Are-Zero mode
------ Initializing File System ------
Current search path:
Z:\home\clay/base
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Shutting down OpenGL subsystem
...shutting down QGL
Couldn't load default.cfg

This is what I get in the terminal:

clay@OUmachine2:~$ wine DOOM3.exe
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:create_server class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x15

Have any ideas?  I'm fairly new to linux, but I'm getting more comfortable with it everyday.  Any help would be greatly appreciated.

---

