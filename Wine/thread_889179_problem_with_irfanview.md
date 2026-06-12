---
title: "problem with irfanview"
date: 2008-08-13
forum: Wine
---

### Post by frankophile on 2008-08-13
Using the following thread:

[http://ubuntuforums.org/showthread.php?t=426689&highlight=irfanview+wine](http://ubuntuforums.org/showthread.php?t=426689&highlight=irfanview+wine)

I was able to get Irfanview installed successfully with Wine.  Now that I have in installed though, I can't get it to work.  When I attempt to launch it, my virtual desktop comes up, stays for a second or two and then disappears.  

I am using Irfanview 4.2.  Any help would be greatly appreciated.

---

### Post by AMSlider on 2009-01-14
This is a bit old, but how do you "attempt to launch it"?  Try it on the command line and post the results.  I just installed wine 1.1.12 (tried supported 1.0.1 first) on 64bit via [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb") and Irfanview 4.23.  It failed, so I just copied a Irfanview 3.99 install from a Windows machine and all works great!  Anyways maybe there's an issue on wine 1.0.1/1.1.12 on 64bit via and Irfanview 4.2x?

HTH,
Slider

```

$ wine ~/.wine/drive_c/Program\ Files/IrfanView/i_view32.exe
 
wine: Unhandled page fault on read access to 0x0620000c at address 0x7ebaea13 (thread 0033), starting debugger...
Unhandled exception: page fault on read access to 0x0620000c in 32-bit code (0x7ebaea13).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7ebaea13 ESP:0033e2c0 EBP:0033e2e8 EFLAGS:00010202(   - 00      - -RI1)
 EAX:0013fff0 EBX:7ebd8ff4 ECX:00e6e6e6 EDX:06200004
 ESI:00000000 EDI:00000384
Stack dump:
0x0033e2c0:  00000384 0000ffff 000004cc 00000017
0x0033e2d0:  00000090 0012d040 0012d040 7edf2ff4
0x0033e2e0:  7ec8c080 001421c8 0033e368 7ed75fea
0x0033e2f0:  00000384 00000018 0033e344 00000018
0x0033e300:  00000018 0000045c 00000030 00000060
0x0033e310:  00220326 7edf2ff4 000004b4 001421c8
Backtrace:
=>0 0x7ebaea13 GetObjectW+0x43() in gdi32 (0x0033e2e8)
  1 0x7ed75fea ImageList_AddMasked+0xaa() in comctl32 (0x0033e368)
  2 0x00460997 in i_view32 (+0x60997) (0x00000378)
  3 0x00000000 (0x00000000)
0x7ebaea13 GetObjectW+0x43 in gdi32: movl	0x8(%edx),%edx
Modules:
Module	Address			Debug info	Name (74 modules)
PE	  400000-  542000	Export          i_view32
ELF	7b800000-7b940000	Deferred        kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcad000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e0d4000-7e0d8000	Deferred        libgpg-error.so.0
ELF	7e0d8000-7e141000	Deferred        libgcrypt.so.11
ELF	7e141000-7e153000	Deferred        libtasn1.so.3
ELF	7e153000-7e15c000	Deferred        libkrb5support.so.0
ELF	7e15c000-7e18e000	Deferred        libcrypt.so.1
ELF	7e18e000-7e22b000	Deferred        libgnutls.so.26
ELF	7e22b000-7e24f000	Deferred        libk5crypto.so.3
ELF	7e24f000-7e2e1000	Deferred        libkrb5.so.3
ELF	7e2e1000-7e30b000	Deferred        libgssapi_krb5.so.2
ELF	7e30b000-7e341000	Deferred        libcups.so.2
ELF	7e3a0000-7e3d3000	Deferred        uxtheme<elf>
  \-PE	7e3b0000-7e3d3000	\               uxtheme
ELF	7e3d3000-7e3dc000	Deferred        libxcursor.so.1
ELF	7e3dc000-7e3e1000	Deferred        libxfixes.so.3
ELF	7e3e1000-7e3e5000	Deferred        libxcomposite.so.1
ELF	7e3e5000-7e3ec000	Deferred        libxrandr.so.2
ELF	7e3ec000-7e3f6000	Deferred        libxrender.so.1
ELF	7e3f6000-7e3fc000	Deferred        libxxf86vm.so.1
ELF	7e3fc000-7e3ff000	Deferred        libxinerama.so.1
ELF	7e3ff000-7e420000	Deferred        imm32<elf>
  \-PE	7e410000-7e420000	\               imm32
ELF	7e420000-7e425000	Deferred        libxdmcp.so.6
ELF	7e425000-7e43e000	Deferred        libxcb.so.1
ELF	7e43e000-7e441000	Deferred        libxcb-xlib.so.0
ELF	7e441000-7e444000	Deferred        libxau.so.6
ELF	7e444000-7e533000	Deferred        libx11.so.6
ELF	7e533000-7e542000	Deferred        libxext.so.6
ELF	7e542000-7e546000	Deferred        libkeyutils.so.1
ELF	7e546000-7e54a000	Deferred        libcom_err.so.2
ELF	7e561000-7e5fd000	Deferred        winex11<elf>
  \-PE	7e570000-7e5fd000	\               winex11
ELF	7e658000-7e67f000	Deferred        libexpat.so.1
ELF	7e67f000-7e6ac000	Deferred        libfontconfig.so.1
ELF	7e6ac000-7e6c2000	Deferred        libz.so.1
ELF	7e6c2000-7e738000	Deferred        libfreetype.so.6
ELF	7e738000-7e74c000	Deferred        libresolv.so.2
ELF	7e74c000-7e76c000	Deferred        iphlpapi<elf>
  \-PE	7e750000-7e76c000	\               iphlpapi
ELF	7e76c000-7e7d3000	Deferred        rpcrt4<elf>
  \-PE	7e780000-7e7d3000	\               rpcrt4
ELF	7e7d3000-7e8e4000	Deferred        ole32<elf>
  \-PE	7e7f0000-7e8e4000	\               ole32
ELF	7e8e4000-7e91b000	Deferred        winspool<elf>
  \-PE	7e8f0000-7e91b000	\               winspool
ELF	7e91b000-7e978000	Deferred        shlwapi<elf>
  \-PE	7e930000-7e978000	\               shlwapi
ELF	7e978000-7eaa3000	Deferred        shell32<elf>
  \-PE	7e990000-7eaa3000	\               shell32
ELF	7eaa3000-7eb51000	Deferred        comdlg32<elf>
  \-PE	7eab0000-7eb51000	\               comdlg32
ELF	7eb51000-7ebf2000	Export          gdi32<elf>
  \-PE	7eb60000-7ebf2000	\               gdi32
ELF	7ebf2000-7ed40000	Deferred        user32<elf>
  \-PE	7ec10000-7ed40000	\               user32
ELF	7ed40000-7ee07000	Export          comctl32<elf>
  \-PE	7ed50000-7ee07000	\               comctl32
ELF	7ee07000-7ee5c000	Deferred        advapi32<elf>
  \-PE	7ee10000-7ee5c000	\               advapi32
ELF	7ee5c000-7ee68000	Deferred        libnss_files.so.2
ELF	7ee68000-7ee73000	Deferred        libnss_nis.so.2
ELF	7ee73000-7ee7c000	Deferred        libnss_compat.so.2
ELF	7efbb000-7efe1000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        libnsl.so.1
ELF	f7c96000-f7c9a000	Deferred        libdl.so.2
ELF	f7c9a000-f7df8000	Deferred        libc.so.6
ELF	f7df9000-f7e12000	Deferred        libpthread.so.0
ELF	f7e31000-f7f68000	Deferred        libwine.so.1
ELF	f7f6a000-f7f8a000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
00000032 (D) C:\Program Files\IrfanView\i_view32.exe
	00000033    0 <==
Backtrace:
=>0 0x7ebaea13 GetObjectW+0x43() in gdi32 (0x0033e2e8)
  1 0x7ed75fea ImageList_AddMasked+0xaa() in comctl32 (0x0033e368)
  2 0x00460997 in i_view32 (+0x60997) (0x00000378)
  3 0x00000000 (0x00000000)
err:syslevel:_CheckNotSysLevel Holding lock 0x7ebe10c0 level 3
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed05fa0, level 2): Holding 0x7ebe10c0, level 3. Expect deadlock!

```

---

### Post by alex.rayu on 2009-01-14
Man! I can imagine why somebody would want to run World of Warkraft in Wine, or Photoshop. But Irfanview? It's a perversion!

---

### Post by deutne on 2009-02-03
I am using Hardy Heron on a 32-bit machine and had similar problems trying to run Irfanview 4.22 through wine. Irfanview 4.22 seemed to install fine, but then it wouldn't run via the Desktop icon or the command line. 

I took the suggestion here and tried an older version of Irfanview. Irfanview 4.10 seems to work, but Irfanview 4.20 did not. I am hoping that the Irfanview 4.22 plugins work with Irfanview 4.10.

---

### Post by gari on 2009-02-10
Just a short post to inform those still having some problem to install Irfanview on Ubuntu ...

It is very important to pay attention to the mcf42.dll file to be added to the wine's dll.
Indeed, in my case, the mfc42.dll downloaded from [www.dll-files.com](www.dll-files.com) (or equivalent) was not working and was leading to irfanview simply crashing while starting.
On the other hand, the mfc42.dll file taken directly from my windows XP partition worked perfectly and allowed me to use Irfanview 4.10 on my Ubuntu 8.10!

I hope that this hint will be useful to some of you, as in my case, I have lost quite some time on this issue !

---

### Post by Electric Bill on 2009-02-16
[SIZE=2]I just took the Irfanview.exe v 4.0 from a Windows XP installation's Program Files and installed it in -[/SIZE]
[SIZE=2]/home/bill/.wine/dosdevices/c:/Program Files/Irfanview.[/SIZE]
[SIZE=2]I then added it to the menu and directed it with the command -[/SIZE]
[SIZE=2]env WINEPREFIX="/home/bill/.wine" wine "C:\Program Files\Irfanview\i_view32.exe"[/SIZE]
 
[SIZE=2]The Irfanview icon is a PNG image I created and placed in -[/SIZE]
[SIZE=2]/usr/share/app-install/icons.[/SIZE]
[SIZE=2]I also used the WINE Notebook app and installed WordWeb with WINE.[/SIZE]
[SIZE=2]The WordWeb icon installed in the menu automatically but I had to make my own Notebook icon that I borrowed from Win XP.[/SIZE]
 
[SIZE=2]My IrfanView works nicely and the Slideshow and Thumbnail functions work normally.[/SIZE]
[SIZE=2]The program is able to navigate the Linux file system without any issues.[/SIZE]
[SIZE=2]The Print Screen Save to Clipboard won't Paste into IrfanView but if I reduce the size of the program window so that I can see the desktop I can drag the image from the Save Screenshot window on to the IrfanView window and edit or crop and save as necessary.[/SIZE]
 
[SIZE=2]WordWeb also works well but you have to copy and paste a word into the dialog box instead of just double clicking it. [/SIZE]
 
[SIZE=2][COLOR=darkred]Click on image for full 1360x780 screenshot.[/COLOR] [/SIZE]
[[IMG]http://newportyachtdirectory.com/Ubuntu_Forums/Screenshot_800x452.jpg[/IMG]]("http://newportyachtdirectory.com/Ubuntu_Forums/Screenshot.jpg")
 
[SIZE=2]The AWN panel.[/SIZE]
[IMG]http://newportyachtdirectory.com/Ubuntu_Forums/AWN.jpeg[/IMG]
 
[SIZE=2]This is the Gnome sensors-applet 2.2.1 which is monitoring CPU temp and fan speed.[/SIZE]
[IMG]http://newportyachtdirectory.com/Ubuntu_Forums/CPU_temp-fan.jpg[/IMG]
 
[SIZE=2]Bill[/SIZE]

---

