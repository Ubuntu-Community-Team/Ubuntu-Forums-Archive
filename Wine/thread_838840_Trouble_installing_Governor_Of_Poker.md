---
title: "Trouble installing Governor Of Poker"
date: 2008-06-23
forum: Wine
---

### Post by anathema415 on 2008-06-23
I'm trying to install the game Governor Of Poker via wine, and I'm running into this:

> err:ole:CoGetClassObject class {56fdf344-fd6d-11d0-958a-006097c9a090} not registered
err:ole:CoGetClassObject no class object {56fdf344-fd6d-11d0-958a-006097c9a090} could be created for context 0x1
wine: Unhandled page fault on read access to 0x00000000 at address 0x41d591 (thread 000b), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0041d591).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0041d591 ESP:0033fd8c EBP:00000007 EFLAGS:00210282(   - 00      - RIS1)
 EAX:80040154 EBX:00000000 ECX:00000000 EDX:00000071
 ESI:004a50a8 EDI:00000000
Stack dump:
0x0033fd8c:  7b866bb0 00000000 0033ff08 7b8b3884
0x0033fd9c:  004a50a8 0033fdb0 0047d1ad 0000000f
0x0033fdac:  0041d5fc 0033fef8 0047d1ce 00000000
0x0033fdbc:  0041e7e5 00400000 00000000 00491310
0x0033fdcc:  ffffffff 7b84389f 0033fe98 00400000
0x0033fddc:  7b8b3884 0033ff08 0046bda7 00400000
Backtrace:
=>1 0x0041d591 in governor (+0x1d591) (0x00000007)
  2 0x00000000 (0x00000000)
0x0041d591: movl	0x0(%edi),%eax
Modules:
Module	Address			Debug info	Name (91 modules)
PE	  400000-  7c0000	Export          governor
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7df49000-7df4d000	Deferred        libgpg-error.so.0
ELF	7df4d000-7df9a000	Deferred        libgcrypt.so.11
ELF	7df9a000-7dfaa000	Deferred        libtasn1.so.3
ELF	7dfaa000-7dfb2000	Deferred        libkrb5support.so.0
ELF	7dfb2000-7dfe4000	Deferred        libcrypt.so.1
ELF	7dfe4000-7e05a000	Deferred        libgnutls.so.13
ELF	7e05a000-7e07d000	Deferred        libk5crypto.so.3
ELF	7e07d000-7e10a000	Deferred        libkrb5.so.3
ELF	7e10a000-7e133000	Deferred        libgssapi_krb5.so.2
ELF	7e133000-7e166000	Deferred        libcups.so.2
ELF	7e1b2000-7e1c6000	Deferred        midimap<elf>
  \-PE	7e1c0000-7e1c6000	\               midimap
ELF	7e1c6000-7e1ec000	Deferred        msacm32<elf>
  \-PE	7e1d0000-7e1ec000	\               msacm32
ELF	7e1ec000-7e203000	Deferred        msacm32<elf>
  \-PE	7e1f0000-7e203000	\               msacm32
ELF	7e203000-7e2c6000	Deferred        libasound.so.2
ELF	7e2d8000-7e30e000	Deferred        winealsa<elf>
  \-PE	7e2e0000-7e30e000	\               winealsa
ELF	7e30e000-7e341000	Deferred        uxtheme<elf>
  \-PE	7e310000-7e341000	\               uxtheme
ELF	7e341000-7e34a000	Deferred        libxcursor.so.1
ELF	7e34a000-7e34f000	Deferred        libxfixes.so.3
ELF	7e34f000-7e352000	Deferred        libxcomposite.so.1
ELF	7e352000-7e358000	Deferred        libxrandr.so.2
ELF	7e358000-7e360000	Deferred        libxrender.so.1
ELF	7e360000-7e363000	Deferred        libxinerama.so.1
ELF	7e363000-7e383000	Deferred        imm32<elf>
  \-PE	7e370000-7e383000	\               imm32
ELF	7e383000-7e388000	Deferred        libxdmcp.so.6
ELF	7e388000-7e3a0000	Deferred        libxcb.so.1
ELF	7e3a0000-7e3a3000	Deferred        libxau.so.6
ELF	7e3a3000-7e48a000	Deferred        libx11.so.6
ELF	7e48a000-7e498000	Deferred        libxext.so.6
ELF	7e498000-7e49d000	Deferred        libxxf86vm.so.1
ELF	7e49d000-7e4b5000	Deferred        libice.so.6
ELF	7e4b5000-7e4bd000	Deferred        libsm.so.6
ELF	7e4bd000-7e4c0000	Deferred        libkeyutils.so.1
ELF	7e4ca000-7e4cd000	Deferred        libcom_err.so.2
ELF	7e4cf000-7e566000	Deferred        winex11<elf>
  \-PE	7e4e0000-7e566000	\               winex11
ELF	7e590000-7e5b1000	Deferred        libexpat.so.1
ELF	7e5b1000-7e5db000	Deferred        libfontconfig.so.1
ELF	7e5db000-7e5f0000	Deferred        libz.so.1
ELF	7e5f0000-7e660000	Deferred        libfreetype.so.6
ELF	7e660000-7e702000	Deferred        oleaut32<elf>
  \-PE	7e670000-7e702000	\               oleaut32
ELF	7e702000-7e738000	Deferred        winspool<elf>
  \-PE	7e710000-7e738000	\               winspool
ELF	7e738000-7e791000	Deferred        shlwapi<elf>
  \-PE	7e750000-7e791000	\               shlwapi
ELF	7e791000-7e8a4000	Deferred        shell32<elf>
  \-PE	7e7a0000-7e8a4000	\               shell32
ELF	7e8a4000-7e94f000	Deferred        comdlg32<elf>
  \-PE	7e8b0000-7e94f000	\               comdlg32
ELF	7e94f000-7e9e1000	Deferred        winmm<elf>
  \-PE	7e960000-7e9e1000	\               winmm
ELF	7e9e1000-7eaa0000	Deferred        comctl32<elf>
  \-PE	7e9f0000-7eaa0000	\               comctl32
ELF	7eaa0000-7eab3000	Deferred        libresolv.so.2
ELF	7eab3000-7eab5000	Deferred        libxcb-xlib.so.0
ELF	7eac5000-7eae3000	Deferred        iphlpapi<elf>
  \-PE	7ead0000-7eae3000	\               iphlpapi
ELF	7eae3000-7eb44000	Deferred        rpcrt4<elf>
  \-PE	7eaf0000-7eb44000	\               rpcrt4
ELF	7eb44000-7ebdf000	Deferred        gdi32<elf>
  \-PE	7eb50000-7ebdf000	\               gdi32
ELF	7ebdf000-7ed26000	Deferred        user32<elf>
  \-PE	7ec00000-7ed26000	\               user32
ELF	7ed26000-7ed78000	Deferred        advapi32<elf>
  \-PE	7ed30000-7ed78000	\               advapi32
ELF	7ed78000-7ee1c000	Deferred        ole32<elf>
  \-PE	7ed90000-7ee1c000	\               ole32
ELF	7ee1c000-7ee73000	Deferred        ddraw<elf>
  \-PE	7ee20000-7ee73000	\               ddraw
ELF	7ef93000-7ef9e000	Deferred        libnss_files.so.2
ELF	7ef9e000-7efa8000	Deferred        libnss_nis.so.2
ELF	7efa8000-7efc0000	Deferred        libnsl.so.1
ELF	7efc0000-7efc9000	Deferred        libnss_compat.so.2
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	b7d04000-b7d08000	Deferred        libdl.so.2
ELF	b7d08000-b7e57000	Deferred        libc.so.6
ELF	b7e58000-b7e70000	Deferred        libpthread.so.0
ELF	b7e82000-b7fb8000	Deferred        libwine.so.1
ELF	b7fba000-b7fd6000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000026    0
	00000025    0
	00000024    0
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
0000001d (D) Z:\home\james\Governor.exe
	0000000b    0 <==
Backtrace:
=>1 0x0041d591 in governor (+0x1d591) (0x00000007)
  2 0x00000000 (0x00000000)


Help please?

---

### Post by anathema415 on 2008-06-25
bump

---

### Post by DoktorSeven on 2008-06-25
Might just not work in Wine at present.  I don't see an entry for it on Wine's appdb, so there's no real way to tell.

---

### Post by austin987 on 2008-06-27
[http://bugs.winehq.org/show_bug.cgi?id=14139](http://bugs.winehq.org/show_bug.cgi?id=14139)

---

### Post by anathema415 on 2008-06-27
Thanks Austin.

I'm new with wine, how do I do the below instructions please?

> Hi, i saw someone was trying to get this app running here
[http://ubuntuforums.org/showthread.php?t=838840](http://ubuntuforums.org/showthread.php?t=838840)

So i gave it a try as well. I got the same crash as that guy. The following
workaround makes the game start and run nicely:
Put following in the registry:
REGEDIT4

[HKEY_CLASSES_ROOT\CLSID\{56FDF344-FD6D-11d0-958A-006097C9A090}]
@="Task Bar Communication"

[HKEY_CLASSES_ROOT\CLSID\{56FDF344-FD6D-11d0-958A-006097C9A090}\InProcServer32]
@="C:\\Windows\\System32\\SHDOCVW.DLL"
"ThreadingModel"="Apartment"

Then run with native shdocvw (and shlwapi).


Apparently ITaskBarList implementation is completely missing from shdocvw,
causing the crash above.


---

### Post by anathema415 on 2008-07-02
Can someone please help me with these instructions?

> Put following in the registry:
REGEDIT4

[HKEY_CLASSES_ROOT\CLSID\{56FDF344-FD6D-11d0-958A-006097C9A090}]
@="Task Bar Communication"

[HKEY_CLASSES_ROOT\CLSID\{56FDF344-FD6D-11d0-958A-006097C9A090}\InProcServer32]
@="C:\\Windows\\System32\\SHDOCVW.DLL"
"ThreadingModel"="Apartment"

Then run with native shdocvw (and shlwapi).


Apparently ITaskBarList implementation is completely missing from shdocvw,
causing the crash above. 

---

### Post by Extak on 2008-07-18
Can anybody help?
I put the values in the registry and set up with winecfg to run with native libraries shdocvw and shlwapi, but i get:

err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"C:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library comdlg32.dll (which is needed by L"C:\\Program Files\\Alawar\\GovernorofPoker\\GovernorofPoker_Alawar_EN.exe") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library SHELL32.dll (which is needed by L"C:\\Program Files\\Alawar\\GovernorofPoker\\GovernorofPoker_Alawar_EN.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Alawar\\GovernorofPoker\\GovernorofPoker_Alawar_EN.exe" failed, status c0000135


Sorry for my english.

---

### Post by lajfi on 2009-02-08
I'm also facing problems getting Governor of Poker installed.
after launching the install exe file, wine fires up, and shows me a window, asking me to pick a folder to install the game.

Here start the troubles....
the browsing of the folders seems to be ok, but picking the folder, does not result in an update of the browse field.

After clicking ok, the job status remains "waiting" and the progress bar doesn't move.

After checking the file system, I can find the "Governer of Poker" folder, which contains a subfolder called "Config data".

I have tried to apply the patch as shown in this thread: [http://bugs.winehq.org/show_bug.cgi?id=14139](http://bugs.winehq.org/show_bug.cgi?id=14139)
But when i try to apply it, it asks me "File to patch". I ran the patch in my .wine folder... 

FYI, I installed wine today by downloading the installer from WineHQ. I am running Ubuntu Intrepid.

As you probably guessed, I'm a noobie , so please be gentle ;)

---

### Post by lajfi on 2009-02-09
ok, i got the game to work!!!

i followed the instructions here
[http://dogbuntu.wordpress.com/2008/05/02/running-flash-exes-in-ubuntu-or-any-other-linux-with-wine/](http://dogbuntu.wordpress.com/2008/05/02/running-flash-exes-in-ubuntu-or-any-other-linux-with-wine/)

and it runs flawlessly now (as far as i could test)

---

### Post by fimman on 2009-03-02
having the problem here [IMG]http://i41.tinypic.com/986cf6.png[/IMG]
can anyone help it doesnt load properly?

---

### Post by g0at78 on 2009-04-29
*bump*

i have the same problem running governor of poker.

---

### Post by Sedoj on 2009-08-23
Hi! Game is started with wine 1.1.27
Ubuntu 9.04 i386

[IMG]("http://images.netbynet.ru/imgs/a4eca50ebfc2fe6151601b918c37e8cd.png")

---

