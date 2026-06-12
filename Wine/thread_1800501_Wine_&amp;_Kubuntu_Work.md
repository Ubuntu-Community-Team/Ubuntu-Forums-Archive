---
title: "Wine &amp; Kubuntu Work?"
date: 2011-07-09
forum: Wine
---

### Post by TurtleKing on 2011-07-09
Tried wine 1.3 and tried to install NFSMW (video game)and it gave me the response:
> missing DirectX9 or higher.
Tried stable version 1.2 and the CD installation wizard will not let me get pass the "insert 2nd CD/DVD into D:" pop-up. I tried without success, what worked previously in Ubuntu which was to go through winecfg & and configure it for NFSMW_DISC2 folder after the 1st one installed. In addition, tried using the regular CD method and as expected did not work.

Anybody been successful or know what might be wrong with my wine install on Kubuntu (64bit)?

---

### Post by bobwyajnr on 2011-07-09
@**TurtleKing**

RE: output from Wine 1.3.23 (don't bother with 1.2.xx - it may be 'stable' but the code was frozen months ago - with no further updates being backported):
> missing DirectX9 or higher.
Is that in a GUI - I presume?

Any chance of some console output? Have you installed the proprietary video drivers for your graphics card?

Shouldn't be any additional problems running DirectX Windows games, using Wine, in Kubuntu. In fact I've found KVM to be far more stable than the current bleeding edge Compiz 0.9.4 (using 11.04).:popcorn:

Bob

---

### Post by TurtleKing on 2011-07-11
Yeah the feedback about missing DirectX9 was a GUI.By "proprietary video drivers for your graphic card" Are you referring to additional drivers thing? I have Nvidia X server settings under my system menu, and I can use desktop effects. So I would assume they are installed. Weird thing is that it list the recommended settings as activate but not currently in use.

Also, tried removing wine1.2 from scratch and installing wine1.3 (which installed pretty fast so I am guessing it's not working).

Now when I type "winecfg &" in konsole I get the reply:

```
name@computer:~$ wine cfg &
[1] 1840
name@computer:~$ wine: created the configuration directory '/home/username/.wine'
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:iphlpapi:NotifyAddrChange (Handle 0x8ede90c, overlapped 0x8ede8f0): stub
wine: configuration in '/home/hades/.wine' has been updated.
wine: cannot find L"C:\\windows\\system32\\cfg.exe"
```
And previously when I tried installing CD games and got this feedback they didn't work, so I will assume it is probably going to happen again.:(

---

### Post by TurtleKing on 2011-07-12
Got an update today for wine1.3. The winecfg & worked this time, so I decided to go ahead and try the install. Unfortunately, it gave me the same GUI response about missing directx9 or higher:
> Installation cannot continue because this game requires Directx 9.0c or higher to be installed on your system. You can download the latest version of DirectX here:
(link)

Here is what the terminal reported after running the "wine AutoRun.exe" command:
```
username@computer:~/.wine/dosdevices/d:$ wine AutoRun.exe
username@computer:~/.wine/dosdevices/d:$ fixme:win:EnumDisplayDevicesW ((null),0,0x33a494,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33a3a4,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a760-90c8-11d0-bd43-00a0c911ce86} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a761-90c8-11d0-bd43-00a0c911ce86} not found
err:alsa:ALSA_CheckSetVolume Could not find '{PCM,Line} Playback Volume' element
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
```
Any idea what might be going wrong?

---

### Post by bobwyajnr on 2011-07-15
```
wine cfg&
```
is the same as:
```
wine cfg.exe&
```
Hence the error:
```
wine: cannot find L"C:\\windows\\system32\\cfg.exe"
```

Remember Wine is just a compatibility layer. It will report to the Windows applications what it 'sees' available in the underlying Linux system. So you could have a Geforce 580 card in there and your Windows application still won't able to use DirectX acceleration unless you have the proprietary Nvidia driver installed and working with the Linux kernel.

Try
```
sudo lshw -C video
```
(install **lshw** if you haven't got it already...)
That will show you what driver module the kernel has loaded for your graphics card and some nice technical details about it :D Perhaps you could post the output here?

If you are rolling with the open source **nouveau** driver - it will do desktop effects but 3D support is very limited at present. This is the default Nvidia driver for newer Kubuntu/Ubuntu releases. Nvidia isn't supporting development - so progress is slow.

Check this first - then the next step! :popcorn:

Bob

---

### Post by TurtleKing on 2011-07-16
Here is the output from that command:

```
username@computer:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: G84 [GeForce 8600 GTS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb01ffff
username@computer:~$
```

---

### Post by TurtleKing on 2011-07-21
bump

---

### Post by TurtleKing on 2011-07-24
2nd bump.

---

### Post by TurtleKing on 2011-07-27
x3 bump.

---

### Post by TurtleKing on 2011-08-24
4x bump.

Bob you still around buddy?

---

### Post by VOT Productions on 2011-08-25
Have you tried installing DirectX9? The simplest way is to install winetricks and do it from there.

---

