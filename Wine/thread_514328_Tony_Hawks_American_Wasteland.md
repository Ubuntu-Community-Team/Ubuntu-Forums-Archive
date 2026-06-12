---
title: "Tony Hawks American Wasteland"
date: 2007-07-31
forum: Wine
---

### Post by cmmike1 on 2007-07-31
I just got Tony Hawks American Wasteland to install and i'm trying to run it through the terminal. It starts the game fine but once the intro is done the loading screen doesn't load and it crashes. I think i'm getting some sort of error and i've never installed a game in wine before so i'm not exactly sure as to what i'm doing. Here is the output of my terminal.```
mike@mike:~$ cd $HOME/.wine/drive_c/Program\ Files/Aspyr\ Media,\ Inc/THAW/Game
mike@mike:~/.wine/drive_c/Program Files/Aspyr Media, Inc/THAW/Game$ wine THAW.exe
err:module:import_dll Library d3d8thk.dll (which is needed by L"C:\\windows\\system32\\d3d9.dll") not found
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:dsalsa:SetFormat Your alsa dmix period size is 1024, try decreasing it to 512 if possible
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1bad98) : stub, simulating 64MB for now, returning 64MB left
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet

```
And it just repeats that one line for a long time and then at the end i get this.
```
err:seh:setup_exception stack overflow 16 bytes in thread 000d eip 7e94e87d esp 7ca86ff0 stack 0x7ca87000-0x7cc97000
err:ntdll:RtlpWaitForCriticalSection section 0x7e9c6e90 "d3d9_main.c: d3d9_cs" wait timed out in thread 0009, blocked by 000d, retrying (60 sec)
wine: Critical section 7e9c6e90 wait failed at address 0x7bc30870 (thread 0009), starting debugger...
Unhandled exception: wait failed on critical section 0x7e9c6e90 d3d9_cs
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc30870
mike@mike:~/.wine/drive_c/Program Files/Aspyr Media, Inc/THAW/Game$ Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0



```
I realise that probably nobody has tried to install this game but i know that there are a lot of people who know somethings about wine and could possibly tell me if this game will be able to work or not. Thanks for reading.

PS. Here's a screen of the game frozen...
[[IMG]http://img71.imageshack.us/img71/9994/screenshothc5.th.png[/IMG]](http://img71.imageshack.us/my.php?image=screenshothc5.png)

---

### Post by cmmike1 on 2007-08-01
I also tried to install it in cedega 6.0 but it wouldn't work at all. it wouldn't even install. is there still hope in wine?

---

### Post by cmmike1 on 2007-08-03
i guess no one knows about this?

---

### Post by hikaricore on 2007-08-03
Sorry but it may not be possible to play at this time.  :/

IF you make any progress using WINE, please consider adding your info to the [WINE Application Database]("http://appdb.winehq.org") so that other Ubuntu/Linux users know the status of the game's playablilty.

They can also later add info and work arounds to the page as the playability increases over time with progress of the WINE project.  ^_^

---

### Post by cmmike1 on 2007-08-04
i was thinking about doing that but i'm going to read up about wine for a while and learn about it some more. then i'll give it a few more goes. I guess it could always be fixed with a wine upgrade in the future so i'll keep trying.

---

### Post by YouSmeg118 on 2008-08-23
I know this is a really old topic, but i was wondering if anyone had got it running?

---

