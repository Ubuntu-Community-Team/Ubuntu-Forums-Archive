---
title: "How to bring Windows mapped drive in linux wine"
date: 2012-12-25
forum: Wine
---

### Post by Carlo Jongen on 2012-12-25
Hi,

I've just started with Linux and I'm having a problem. Hopefully someone can help me with this.

I'm running Ubuntu 12.10 and wine 1.5.19 on a IntelMacPro ( Slave ).
On this Mac ( slave ) I'm running some Windows programs ( Lightwave: lwsn.exe and eyeon fusion: renderslave.exe ).
This seems to work, but these programs need to access some Windows mapped drives ( like x: y: and z: to be precise ) on an other machine ( a Master running Win7 64bit ).
Does anybody know how to get windows mapped drives into wine ( ~/.wine/dosdevices/ )?

So these programs can access the mapped drives.

I'm looking all over the net for answers but I can't seem to get this to work. Anybody know the answer?
But remember I'm a Linux Dummy :-/

Thanks in advance...

With my best regards,
Carlo

---

### Post by Carlo Jongen on 2012-12-26
Hi,

I've just started with Linux and I'm having a problem. I've posted this question also in the network section with no success. Hopefully someone here can help me with this.

I'm running Ubuntu 12.10 and wine 1.5.19 on a IntelMacPro ( Slave ).
On this Mac ( slave ) I'm running some Windows programs ( Lightwave: lwsn.exe and eyeon fusion: renderslave.exe ).
This seems to work, but these programs need to access some Windows mapped drives ( like x: y: and z: to be precise ) on an other machine ( a Master running Win7 64bit ).
Does anybody know how to get windows mapped drives into wine ( ~/.wine/dosdevices/ )?

So these programs can access the mapped drives.

I'm looking all over the net for answers but I can't seem to get this to work. Anybody know the answer?
But remember I'm a Linux Dummy :-/

Thanks in advance...

With my best regards,
Carlo

---

### Post by Carlo Jongen on 2012-12-26
Hi,

I've just started with Linux and I'm having a problem. I've posted this question also in the network and wine section with no success. Hopefully someone here can help me with this.

I'm running Ubuntu 12.10 and wine 1.5.19 on a IntelMacPro ( Slave ).
On this Mac ( slave ) I'm running some Windows programs ( Lightwave: lwsn.exe and eyeon fusion: renderslave.exe ).
This seems to work, but these programs need to access some Windows mapped drives ( like x: y: and z: to be precise ) on an other machine ( a Master running Win7 64bit ).
Does anybody know how to get windows mapped drives into wine ( ~/.wine/dosdevices/ )?

So these programs can access the mapped drives.

I'm looking all over the net for answers but I can't seem to get this to work. Anybody know the answer?
But remember I'm a Linux Dummy :-/

Thanks in advance...

With my best regards,
Carlo

---

### Post by Toz on 2012-12-26
Merging duplicate threads into one thread. Please do not create duplicate threads for the same issue, it dilutes community effort.

---

### Post by Toz on 2012-12-26
Please refer to this wiki for information on mounting cifs shares ([https://wiki.ubuntu.com/ComprehensiveSambaGuide]("https://wiki.ubuntu.com/ComprehensiveSambaGuide")). Once you have them properly mounted, you can run:
```
winecfg
```
...and on the "Drives" tab, set up your wine drive mappings to point to the cifs mappings you created earlier.

---

### Post by Carlo Jongen on 2012-12-27
Sorry for the duplicate threads but I was getting a bit frustrated not being able to figure this one out after so many day's of research.
 

 Many thanks for the hints, when I followed these steps I could manage to set-up these mapped drives in Linux.  And I've managed to do a test render with the Linux machine. I even have the feeling it renders much faster than in Windows.
 

 Aldo there are 3 issues I would like to  address before I call this thread Solved.
 

 Issue 1/
 ---------
 When the machine boots up it makes a connection with all the mapped drives. But doing so all the mapped drives open up ( pop up ) in a window ( explorer ) folder on the desktop.
 Is there a way to mount them in the background without all the windows popping up all over the desktop?
 

 Issue 2/
 ---------
 I have the program RenderSlave.exe in the &#8220;Start-up Applications&#8221; tool. But apparently this program boots before the Network is ready. Therefore it can't find it's license on the Network.
 Is there a way to delay this Start-up or to be able to start this application only after the network is ready?
 

 Issue 3/
 ---------
 Very view times when I booted the machine the next issue occurred:
  
 It didn't pop up the windows folders of the mapped drives like in &#8220;Issue 1&#8221;. So when I went to the Home Folder and then clicked in the Network section on the &#8220;name of the shared map&#8221; I got the next message:
   
 &#8220;Unable to mount &#8220;name of the shared map&#8221; 
 mount: only root can mount//192.168.2.2/&#8221;name of the shared map&#8221; on/media/winshares/&#8221;name of the shared map&#8221;
 

 How come most of the times it works fine  and the next thing you know it can't because of an permission issue?
 

 --------
 

 I believe that if these issues are solved then I'm one step ahead of changing my Windows based render farm into a Linux one. Really appreciate the help I'm getting here in the Ubuntu Forums.
 

 Thanks to you all...

---

### Post by Toz on 2012-12-27
> **Carlo Jongen said:**
> 
 Issue 1/
 ---------
 When the machine boots up it makes a connection with all the mapped drives. But doing so all the mapped drives open up ( pop up ) in a window ( explorer ) folder on the desktop.
 Is there a way to mount them in the background without all the windows popping up all over the desktop? 
How are you mapping the drives? Through fstab? Can you paste  copy of your /etc/fstab file or the commands/script you use to mount the drives?
>  Issue 2/
 ---------
 I have the program RenderSlave.exe in the “Start-up Applications” tool. But apparently this program boots before the Network is ready. Therefore it can't find it's license on the Network.
 Is there a way to delay this Start-up or to be able to start this application only after the network is ready?
You could create a script to execute this file and add the script to the startup files. You could include a delay in this script. Something like:
```

#!/bin/bash
sleep 5s
wine /path/to/RenderSlave.exe
```
...(adjust 5s to taste and make sure the script is set as executable.)
 
> 
 Issue 3/
 ---------
 Very view times when I booted the machine the next issue occurred:
  
 It didn't pop up the windows folders of the mapped drives like in “Issue 1”. So when I went to the Home Folder and then clicked in the Network section on the “name of the shared map” I got the next message:
   
 “Unable to mount “name of the shared map” 
 mount: only root can mount//192.168.2.2/”name of the shared map” on/media/winshares/”name of the shared map”
 

 How come most of the times it works fine  and the next thing you know it can't because of an permission issue?
 

 --------
 
Perhaps a view of the information from issue #1 would help here.

---

### Post by Carlo Jongen on 2012-12-28
This is what'is in the => /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=9b0f4b65-051b-4bf0-b9a6-594fcd71f562 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=878f99f6-6ac5-46a2-a1d2-a510ea4d78e8 none            swap    sw              0       0
//192.168.2.2/fusion     /media/winshares/fusion        cifs   auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw       0       0
//192.168.2.2/lw3dcfg     /media/winshares/lw3dcfg        cifs   auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw       0       0
//192.168.2.2/lw3d_content     /media/winshares/lw3d_content        cifs   auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw       0       0
//192.168.2.2/lw3d_content_guest     /media/winshares/lw3d_content_guest        cifs   auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw       0       0
//192.168.2.2/media_bank     /media/winshares/media_bank        cifs   auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw       0       0
//192.168.2.2/public_exchange     /media/winshares/public_exchange        cifs   auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw       0       0
//192.168.2.2/render     /media/winshares/render        cifs   auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw       0       0
//192.168.2.2/scrncfg     /media/winshares/scrncfg        cifs   auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw       0       0
//192.168.2.2/renderfarm_cfg     /media/winshares/renderfarm_cfg        cifs   auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw       0       0
```

---

### Post by Toz on 2012-12-28
For issue #1, try disabling automount-open. You can change this setting using the **dconf-editor**. The location is at: org.gnome.desktop.media-handling.

For issue #2, does the script with the delay work?

For issue #3, I would guess that the mount from fstab failed (have a look at /var/log/syslog when this happens). Maybe the network wasn't ready yet? How often does this happen?

---

### Post by Carlo Jongen on 2012-12-28
issue #1 SOLVED

issue #2 Almost SOLVED

issue #3:
I think it has to do with the main ( Windows ) machine coming out of sleep. Sometimes ( not always ) this machine puts red crosses over some of the mapped drives. In this case it seems that I can't get any connection. In Windows I need to tap on the red crosses to activate them again or reboot the main Windows machine. Otherwise the connection works fine. Normally I don't put the main machine to sleep so I think that's why it happens so rarely. I'll keep an I on this one.
---------------------------------------------

ISSUE #2 Is partially solved.

* RenderSlave boots after 5 sec and finds it's license on a Windows Machine.
* The point is that the OS of this machine ( running the license service ) needs to be replaced by Ubuntu as well.
So In this case it can't find its license because of a FlexLM Service- or HASP Driver problem.
Until now I've tried the next thing:
- Installed LMTools.exe in wine and setting it up like in Windows.
- In de Wine RegEdit I've made a System Variable like in Windows.
- Installed Hasp Driver, but I think this is the problem.
* What driver do I need ( Linux or Windows in wine )?
* And how can I check if the Dongle is working properly in Ubuntu or in Wine?

ISSUE #4 Is a new issue, but I think it can easily be fixed.

To run the Lightwave RenderNode I follow the next steps:
- I start up the Windows Command ( /home/intelmac01/.wine/drive_c/windows/command/start.exe )
- Next I go to the path ( c:\Program Files\NewTek\LightWave11.02\bin\ )
- I'll execute RENDER_NODE_03_11.02.bat

This works very well, it can render from the drived maps etc...
* But how can I automate this process in Ubuntu?
* Can this be done with a script as well?

The point is that the slaves need to boot and start up these two render slave app without any manual help. But I think we are almost there :-)

---

### Post by Toz on 2012-12-28
Issue #2: Unfortunately, I won't be able to help here as I don't have any experience with this kind of setup. It might be helpful to start a new thread specific to the issue of getting the dongle to work in Ubuntu.

Issue #4:
Try a script like this (make sure to set it executable):
```

#!/bin/bash
cd "/home/intelmac01/.wine/drive_c/Program Files/NewTek/LightWave11.02/bin"
wine RENDER_NODE_03_11.02.bat
```

---

### Post by Carlo Jongen on 2012-12-29
> **Toz said:**
> Issue #2: Unfortunately, I won't be able to help here as I don't have any experience with this kind of setup. It might be helpful to start a new thread specific to the issue of getting the dongle to work in Ubuntu.

Issue #4:
Try a script like this (make sure to set it executable):
```

#!/bin/bash
cd "/home/intelmac01/.wine/drive_c/Program Files/NewTek/LightWave11.02/bin"
wine RENDER_NODE_03_11.02.bat
```

I've tried several different things to start up this .bat but it didn't work. What ever you google there is no command out there that works.
How would you normally run for example an .exe from the terminal? should almost be the same as a .bat no?

Anyway the mapped drive issue is solved... So I'll try the open issues in an other thread.
Thanks for helping me out. You have solved already a great deal of my Linux nightmares ;-)

---

### Post by Toz on 2012-12-29
> I've tried several different things to start up this .bat but it didn't work. What ever you google there is no command out there that works.
How would you normally run for example an .exe from the terminal? should almost be the same as a .bat no?
Try this instead:
```
#!/bin/bash
cd "/home/intelmac01/.wine/drive_c/Program Files/NewTek/LightWave11.02/bin"
wine cmd /c RENDER_NODE_03_11.02.bat

```

---

### Post by Carlo Jongen on 2012-12-30
Strange, it doesn't work either.
Even if I just try the next thing in Ubuntu Terminal:
```

wine cmd /c

```
In the Ubuntu terminal it can't start up the Windows Terminal.
So in the script it goes wrong at the point where you need to start-up the windows terminal ( wine cmd ).
This is what I get in return:
```

intelmac01@intelmac01-MacPro:~$ wine cmd /c
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
wine: cannot find L"C:\\windows\\system32\\hasplms.exe"
fixme:service:scmdatabase_autostart_services Auto-start service L"hasplms" failed to start: 2
intelmac01@intelmac01-MacPro:~$ fixme:wtsapi:WTSQuerySessionInformationA Stub (nil) 0xffffffff 4 0x33e04c 0x33e040

```

---

### Post by Toz on 2012-12-30
How about this one:
```
#!/bin/bash
wine cmd /c "C:\Program Files\NewTek\LightWave11.02\bin\RENDER_NODE_03_11.02.bat"
```
..I tested this with a dummy script to start up explorer from a bat file and it worked.

---

### Post by Carlo Jongen on 2012-12-30
That one didn't work either

I found a way to execute the .bat, I've just put the content of the .bat file inside the script just behind the "wine cmd /c":
```

#!/bin/bash
sleep 2s
echo Start LW3D11.02 RenderNode 02
wine cmd /c "C:\Program Files\NewTek\LightWave11.02\bin\lwsn.exe -2 -dY:\ -cV:\Lightwave11.02\Config\LW11-64.CFG V:\Lightwave11.02\Command\job2 V:\Lightwave11.02\Command\ack2"

```When I double click the script it asked me "Run in Terminal, Display Cancel or Run", when I click "Run in Terminal". It then runs the rendernode inside the Ubuntu terminal ( instead of the windows terminal ). But apparently this works. I just did some test renders and it seems to work fine like this.

I then nested the script into another script ( because it didn't "Run in Terminal at Start-Up ):
```

#!/bin/bash
sleep 2s
echo Start LW3D11.02 RenderNode 02
gnome-terminal -e /home/intelmac01/AutoRunApp/LWRenderNode02.sh

```Now everything Runs automatic when booting the machine. If I find the HASP Dongle problem than all issues are fixed.

Tanks Toz for your input, it has helped me a lot.

---

