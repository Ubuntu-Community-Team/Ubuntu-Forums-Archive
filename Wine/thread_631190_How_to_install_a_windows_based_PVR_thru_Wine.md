---
title: "How to install a windows based PVR thru Wine?"
date: 2007-12-04
forum: Wine
---

### Post by manuthomas on 2007-12-04
hi,
i am only a 'new bie' and is trying to install my PVR in ubuntu linux 7.04
as i was unsuccessful with installing it as a native linux program(because my tv tuner card provider is not giving a linux based setup! and i don't know how to get around it!), i tried installing it thru wine(when i failed to run the already installed program in windowsXP). but is getting the following errors.

> 
root@doriz:~# wine /home/manu/EasyTV/EasyTV\ MPEG.exe
err:module:import_dll Library ksuser.dll (which is needed by L"Z:\\home\\manu\\EasyTV\\ksproxy.ax") not found
err:module:import_dll Library ksproxy.ax (which is needed by L"Z:\\home\\manu\\EasyTV\\EasyTV MPEG.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\manu\\EasyTV\\EasyTV MPEG.exe" failed, status c0000135


1. Is there a possibility of running the windows PVR software in linux like this?
2. How do i tell wine to check up the mentioned DLLs at the right location?
3. Is there a better way to run my PVR in linux?

by using the command "lspci"i the details of my TV tuner card is shown as

> 05:05.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

this would be of great help as i am longing to see my TV in linux!
...thanx in advance
...manu

---

### Post by Brynster on 2007-12-04
To be honest you will probably struggle to install/run any windows based PVR.

You might do better looking at a dedicated Linux based pvr such as MythTV or MythBuntu

This are a sometimes tricky to install/ set up but will work 100% better than what your trying to achieve. Muythbuntui has a wonderful PDF document explaining the set up and install really well.

---

### Post by cogadh on 2007-12-04
While I think you would be much better off trying a native solution as Brynster suggested, there are a couple of things you are doing incorrectly that if fixed may solve your issue.

EDIT - Ack, I really need to get my coffee before I post here. I posted a bunch of junk that would have made sense if you actually had the app installed. I missed the part where you are getting errors during the install. What you probably need to do is copy those two missing DLL files from an existing Windows installation or download them from the internet and place them in the .wine/drive_c/windows/system32 directory. You may need to also apply a library override for them in winecfg. After you have done that, try re-running the install.

---

