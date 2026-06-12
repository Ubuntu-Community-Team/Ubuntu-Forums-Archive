---
title: "having trouble running Kingpin (quake2 engine) [grey screen]"
date: 2008-06-14
forum: Wine
---

### Post by venom4911 on 2008-06-14
game installed fine but when i try to run it with wine all i get is a grey screen and nothing happens...have to control alt del and log out of ubuntu to be able to do anything...sometimes it will even lock up the entire pc and i have to manually reset it...most of the time its just a grey screen though

ive tried disabling compiz, reinstalling nvidia drivers, different wine compatibility modes/graphics tab settings and none made any difference...

im running ubuntu 8.04 and have a nv 6800gt (169.12 drivers)...running wine 1.0rc5

all linux games/3d apps run great; mupen64, sauerbraten/cube2, world of padman, tremulous, planeshift...all work fine

so any ideas? im sorta new to linux and dunno what else to try...something to do with opengl maybe?

oh and i also tried that kingpin linux installer but couldnt get the game running....kept giving me some kingpin path error when id try to load it so i figured i would try it out with wine...

---

### Post by Sleaka J on 2008-06-14
Try the Loki Linux installer and run it native instead of through Wine.

[http://www.liflg.org/?catid=6&gameid=2](http://www.liflg.org/?catid=6&gameid=2)

---

### Post by venom4911 on 2008-06-14
i tried that already...read the last part of my post...

i ran the linux installer, installed game, manually copied over the rest of the data files, then ran the kingpin file and it gives me some kingpin path not set error...plus you need to have the cd in the drive to play and i rather not do that...at least with wine i can use a nocd crack

---

### Post by venom4911 on 2008-06-14
heres what i copied from running it in terminal:

```
venom4911@ubuntu:~/.wine/drive_c/Program Files/Kingpin$ wine kingpin.exe
fixme:keyboard:RegisterHotKey ((nil),0,0x00000001,9): stub
err:dsalsa:DSDB_CreateMMAP Can't map sound device for direct access: File descriptor in bad state
fixme:dsalsa:CheckXRUN Unhandled state: 0
wine: Unhandled page fault on write access to 0x7e76a000 at address 0xb7d254e7 (thread 0018), starting debugger...
Unhandled exception: page fault on write access to 0x7e76a000 in 32-bit code (0xb7d254e7).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d254e7 ESP:7d2108d8 EBP:7d2109c8 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:7d35fa28 ECX:3ffffffe EDX:00000003
 ESI:10140028 EDI:7e76a000
Stack dump:
0x7d2108d8:  0014c360 7d34301b 7e76a000 00000000
0x7d2108e8:  fffffffb 7d2109a4 7d2109ac 00000000
0x7d2108f8:  fffffffb 00000000 00000000 7c96f087
0x7d210908:  00000012 b7cb5cbc b7cb5c8c 00000000
0x7d210918:  00000002 7d2f7b10 7d280000 00000001
0x7d210928:  b7d1dd91 7d357a53 0014c63c 000002ae
Backtrace:
=>1 0xb7d254e7 memset+0x37() in libc.so.6 (0x7d2109c8)
  2 0x7ee2a9e5 in winmm (+0x2a9e5) (0x7d210a38)
  3 0x7bc6aeae call_thread_entry_point+0xe() in ntdll (0x7d210a48)
  4 0x7bc6b542 in ntdll (+0x5b542) (0x7d210ae8)
  5 0x7bc6b772 in ntdll (+0x5b772) (0x7d2113d8)
  6 0xb7e074fb start_thread+0xcb() in libpthread.so.0 (0x7d2114c8)
0xb7d254e7 memset+0x37 in libc.so.6: repe stosl	%es:(%edi)
Modules:
Module	Address			Debug info	Name (77 modules)
PE	  400000- 1469000	Deferred        kingpin
PE	10000000-10133000	Deferred        ref_gl
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d212000-7d273000	Deferred        rpcrt4<elf>
  \-PE	7d220000-7d273000	\               rpcrt4
ELF	7d273000-7d317000	Deferred        ole32<elf>
  \-PE	7d280000-7d317000	\               ole32
ELF	7d317000-7d361000	Deferred        dsound<elf>
  \-PE	7d320000-7d361000	\               dsound
ELF	7da1b000-7e530000	Deferred        libglcore.so.1
ELF	7e530000-7e5d4000	Deferred        libgl.so.1
ELF	7e5d4000-7e655000	Deferred        opengl32<elf>
  \-PE	7e5f0000-7e655000	\               opengl32
ELF	7e655000-7e669000	Deferred        midimap<elf>
  \-PE	7e660000-7e669000	\               midimap
ELF	7e669000-7e68f000	Deferred        msacm32<elf>
  \-PE	7e670000-7e68f000	\               msacm32
ELF	7e68f000-7e6a6000	Deferred        msacm32<elf>
  \-PE	7e690000-7e6a6000	\               msacm32
ELF	7e6a6000-7e769000	Deferred        libasound.so.2
ELF	7e77b000-7e7b1000	Deferred        winealsa<elf>
  \-PE	7e780000-7e7b1000	\               winealsa
ELF	7e7b1000-7e7ba000	Deferred        libxcursor.so.1
ELF	7e7ba000-7e7bf000	Deferred        libxfixes.so.3
ELF	7e7bf000-7e7c2000	Deferred        libxcomposite.so.1
ELF	7e7c2000-7e7c8000	Deferred        libxrandr.so.2
ELF	7e7c8000-7e7d0000	Deferred        libxrender.so.1
ELF	7e7d0000-7e7d3000	Deferred        libxinerama.so.1
ELF	7e7d3000-7e7f3000	Deferred        imm32<elf>
  \-PE	7e7e0000-7e7f3000	\               imm32
ELF	7e7f3000-7e7f8000	Deferred        libxdmcp.so.6
ELF	7e7f8000-7e810000	Deferred        libxcb.so.1
ELF	7e810000-7e812000	Deferred        libxcb-xlib.so.0
ELF	7e812000-7e815000	Deferred        libxau.so.6
ELF	7e815000-7e8fc000	Deferred        libx11.so.6
ELF	7e8fc000-7e90a000	Deferred        libxext.so.6
ELF	7e90a000-7e90f000	Deferred        libxxf86vm.so.1
ELF	7e90f000-7e927000	Deferred        libice.so.6
ELF	7e927000-7e92f000	Deferred        libsm.so.6
ELF	7e93d000-7e93f000	Deferred        libnvidia-tls.so.1
ELF	7e941000-7e9d8000	Deferred        winex11<elf>
  \-PE	7e950000-7e9d8000	\               winex11
ELF	7e9fd000-7ea1e000	Deferred        libexpat.so.1
ELF	7ea1e000-7ea48000	Deferred        libfontconfig.so.1
ELF	7ea48000-7ea5d000	Deferred        libz.so.1
ELF	7ea5d000-7eacd000	Deferred        libfreetype.so.6
ELF	7eacd000-7eb37000	Deferred        msvcrt<elf>
  \-PE	7eae0000-7eb37000	\               msvcrt
ELF	7eb37000-7eb4a000	Deferred        libresolv.so.2
ELF	7eb5c000-7eb7a000	Deferred        iphlpapi<elf>
  \-PE	7eb60000-7eb7a000	\               iphlpapi
ELF	7eb7a000-7eba6000	Deferred        ws2_32<elf>
  \-PE	7eb80000-7eba6000	\               ws2_32
ELF	7eba6000-7ebc0000	Deferred        wsock32<elf>
  \-PE	7ebb0000-7ebc0000	\               wsock32
ELF	7ebc0000-7ec12000	Deferred        advapi32<elf>
  \-PE	7ebd0000-7ec12000	\               advapi32
ELF	7ec12000-7ecad000	Deferred        gdi32<elf>
  \-PE	7ec20000-7ecad000	\               gdi32
ELF	7ecad000-7edf4000	Deferred        user32<elf>
  \-PE	7ecd0000-7edf4000	\               user32
ELF	7edf4000-7ee86000	Export          winmm<elf>
  \-PE	7ee00000-7ee86000	\               winmm
ELF	7efa6000-7efb1000	Deferred        libnss_files.so.2
ELF	7efb1000-7efc9000	Deferred        libnsl.so.1
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7ca4000-b7cad000	Deferred        libnss_compat.so.2
ELF	b7cae000-b7cb2000	Deferred        libdl.so.2
ELF	b7cb2000-b7e01000	Export          libc.so.6
ELF	b7e02000-b7e1a000	Export          libpthread.so.0
ELF	b7e2c000-b7f62000	Deferred        libwine.so.1
ELF	b7f64000-b7f80000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Kingpin\kingpin.exe
	00000018   15 <==
	00000009    0
0000000c 
	00000013    0
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
Backtrace:
=>1 0xb7d254e7 memset+0x37() in libc.so.6 (0x7d2109c8)
  2 0x7ee2a9e5 in winmm (+0x2a9e5) (0x7d210a38)
  3 0x7bc6aeae call_thread_entry_point+0xe() in ntdll (0x7d210a48)
  4 0x7bc6b542 in ntdll (+0x5b542) (0x7d210ae8)
  5 0x7bc6b772 in ntdll (+0x5b772) (0x7d2113d8)
  6 0xb7e074fb start_thread+0xcb() in libpthread.so.0 (0x7d2114c8)
```

any ideas?

---

### Post by venom4911 on 2008-06-15
fixed it! i changed the wine audio driver to OSS...for some reason ALSA doesnt work

game runs great now

/happy

---

