---
title: "Trouble with Language Software"
date: 2008-06-24
forum: Wine
---

### Post by LavianoTS386 on 2008-06-24
Can any one decipher what this terminal output is saying?

```
 env WINEPREFIX="/home/anthony/.wine" wine "C:\Program Files\Transparent\Power Chinese\ToolBook\tb85run.exe" PWCHN1_1.TBK
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on Brooktree Bt878, disabling mixer
fixme:hook:SetWindowsHookEx16 System-global hooks (7) broken in Win16
wine: Unhandled page fault on read access to 0x000013a8 at address 0x130f:0x00000862 (thread 0021), starting debugger...
Unhandled exception: page fault on read access to 0x000013a8 in 16-bit code (130f:0862).
fixme:dbghelp:addr_to_linear Failed to linearize address 7810:00001f04 (mode 0)
In 16 bit mode.
Register dump:
 CS:130f SS:21bf DS:13ef ES:13ef FS:0063 GS:006b
 IP:0862 SP:6d24 BP:6d28 FLAGS:0206(   - 00      - RIP1)
 AX:1faf BX:000b CX:0000 DX:0000 SI:10c4 DI:10c4
Stack dump:
0x21bf:0x6d24:  07c3 13ef 6d35 04a5 130f 0000 13ee 13ef
0x21bf:0x6d34:  6d65 0468 101f 9678 7e60 0000 0000 0001
0x21bf:0x6d44:  0000 0000 0000 21bf 11d7 0063 006b 0b0c
027d: sel=13ef base=003e00c0 limit=00001e5f 16-bit rw-
Backtrace:
=>1 0x130f:0x0862 (0x21bf:0x6d28)
  2 0x130f:0x04a5 (0x21bf:0x6d34)
  3 0x7810:0x1f04 (0x21bf:0x6d64)
  4 0x7b8a2793 K32WOWCallback16Ex+0xc3() in kernel32 (0x7e6089b8)
  5 0x7b86dd94 NE_InitializeDLLs+0x194() in kernel32 (0x7e608ce8)
  6 0x7b86ddcd NE_InitializeDLLs+0x1cd() in kernel32 (0x7e609018)
  7 0x7b86ddcd NE_InitializeDLLs+0x1cd() in kernel32 (0x7e609348)
  8 0x7b89315e InitTask16+0xae() in kernel32 (0x7e609378)
  9 0x7b82f078 in kernel32 (+0xf078) (0x7e609388)
  10 0x7b8a3692 in kernel32 (+0x83692) (0x7e609698)
  11 0x205f:0x02a6 (0x21bf:0x0000)
0x130f:0x0862: lcall	*0x0(%di)
Modules:
Module	Address			Debug info	Name (91 modules)
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7dd4f000-7ddf1000	Deferred        oleaut32<elf>
  \-PE	7dd60000-7ddf1000	\               oleaut32
ELF	7ddf1000-7de3e000	Deferred        libgcrypt.so.11
ELF	7de3e000-7de4e000	Deferred        libtasn1.so.3
ELF	7de4e000-7de80000	Deferred        libcrypt.so.1
ELF	7de80000-7def5000	Deferred        libgnutls.so.13
ELF	7def5000-7df18000	Deferred        libk5crypto.so.3
ELF	7df18000-7dfa5000	Deferred        libkrb5.so.3
ELF	7dfa5000-7dfce000	Deferred        libgssapi_krb5.so.2
ELF	7dfce000-7e001000	Deferred        libcups.so.2
ELF	7e03f000-7e052000	Deferred        libresolv.so.2
ELF	7e057000-7e05b000	Deferred        libgpg-error.so.0
ELF	7e05b000-7e063000	Deferred        libkrb5support.so.0
ELF	7e06c000-7e08a000	Deferred        iphlpapi<elf>
  \-PE	7e070000-7e08a000	\               iphlpapi
ELF	7e08a000-7e0eb000	Deferred        rpcrt4<elf>
  \-PE	7e0a0000-7e0eb000	\               rpcrt4
ELF	7e0eb000-7e18f000	Deferred        ole32<elf>
  \-PE	7e100000-7e18f000	\               ole32
ELF	7e190000-7e193000	Deferred        libkeyutils.so.1
ELF	7e1bb000-7e1ee000	Deferred        uxtheme<elf>
  \-PE	7e1c0000-7e1ee000	\               uxtheme
ELF	7e1ee000-7e224000	Deferred        winspool<elf>
  \-PE	7e200000-7e224000	\               winspool
ELF	7e224000-7e2e3000	Deferred        comctl32<elf>
  \-PE	7e230000-7e2e3000	\               comctl32
ELF	7e2e3000-7e33c000	Deferred        shlwapi<elf>
  \-PE	7e2f0000-7e33c000	\               shlwapi
ELF	7e33c000-7e44f000	Deferred        shell32<elf>
  \-PE	7e350000-7e44f000	\               shell32
ELF	7e44f000-7e4fa000	Deferred        comdlg32<elf>
  \-PE	7e460000-7e4fa000	\               comdlg32
ELF	7e60b000-7e61f000	Deferred        midimap<elf>
  \-PE	7e610000-7e61f000	\               midimap
ELF	7e61f000-7e645000	Deferred        msacm32<elf>
  \-PE	7e630000-7e645000	\               msacm32
ELF	7e645000-7e64e000	Deferred        librt.so.1
ELF	7e64e000-7e70e000	Deferred        libasound.so.2
ELF	7e70e000-7e744000	Deferred        winealsa<elf>
  \-PE	7e720000-7e744000	\               winealsa
ELF	7e744000-7e7d6000	Deferred        winmm<elf>
  \-PE	7e750000-7e7d6000	\               winmm
ELF	7e7d6000-7e836000	Deferred        winedos<elf>
  \-PE	7e7e0000-7e836000	\               winedos
ELF	7e836000-7e83f000	Deferred        libxcursor.so.1
ELF	7e83f000-7e844000	Deferred        libxfixes.so.3
ELF	7e844000-7e847000	Deferred        libxcomposite.so.1
ELF	7e847000-7e84d000	Deferred        libxrandr.so.2
ELF	7e84d000-7e855000	Deferred        libxrender.so.1
ELF	7e855000-7e858000	Deferred        libxinerama.so.1
ELF	7e858000-7e878000	Deferred        imm32<elf>
  \-PE	7e860000-7e878000	\               imm32
ELF	7e878000-7e87d000	Deferred        libxdmcp.so.6
ELF	7e87d000-7e895000	Deferred        libxcb.so.1
ELF	7e895000-7e898000	Deferred        libxau.so.6
ELF	7e898000-7e97f000	Deferred        libx11.so.6
ELF	7e97f000-7e98d000	Deferred        libxext.so.6
ELF	7e98d000-7e992000	Deferred        libxxf86vm.so.1
ELF	7e992000-7e9a9000	Deferred        msacm32<elf>
  \-PE	7e9a0000-7e9a9000	\               msacm32
ELF	7e9a9000-7e9ac000	Deferred        libcom_err.so.2
ELF	7e9ac000-7ea43000	Deferred        winex11<elf>
  \-PE	7e9c0000-7ea43000	\               winex11
ELF	7ea85000-7eaa6000	Deferred        libexpat.so.1
ELF	7eaa6000-7ead0000	Deferred        libfontconfig.so.1
ELF	7ead0000-7eae5000	Deferred        libz.so.1
ELF	7eae5000-7eb55000	Deferred        libfreetype.so.6
ELF	7eb6f000-7ebc1000	Deferred        advapi32<elf>
  \-PE	7eb80000-7ebc1000	\               advapi32
ELF	7ebc1000-7ec5c000	Deferred        gdi32<elf>
  \-PE	7ebd0000-7ec5c000	\               gdi32
ELF	7ec5c000-7eda3000	Deferred        user32<elf>
  \-PE	7ec80000-7eda3000	\               user32
ELF	7eda3000-7edae000	Deferred        libnss_files.so.2
ELF	7edae000-7edb7000	Deferred        libnss_compat.so.2
ELF	7edbc000-7edd1000	Deferred        winevdm<elf>
  \-PE	7edc0000-7edd1000	\               winevdm
ELF	7efc1000-7efe6000	Deferred        libm.so.6
ELF	7efe6000-7efe8000	Deferred        libxcb-xlib.so.0
ELF	7efe8000-7f000000	Deferred        libnsl.so.1
ELF	f7cd1000-f7cdb000	Deferred        libnss_nis.so.2
ELF	f7cdc000-f7ce0000	Deferred        libdl.so.2
ELF	f7ce0000-f7e2f000	Deferred        libc.so.6
ELF	f7e30000-f7e48000	Deferred        libpthread.so.0
ELF	f7e62000-f7f98000	Deferred        libwine.so.1
ELF	f7f9a000-f7fb9000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
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
00000018 
	00000019    0
0000001d 
	0000001e    0
0000001f (D) c:\windows\system32\winevdm.exe
	00000021    0 <==
	00000020    0
Backtrace:
=>1 0x130f:0x0862 (0x21bf:0x6d28)
  2 0x130f:0x04a5 (0x21bf:0x6d34)
  3 0x7810:0x1f04 (0x21bf:0x6d64)
  4 0x7b8a2793 K32WOWCallback16Ex+0xc3() in kernel32 (0x7e6089b8)
  5 0x7b86dd94 NE_InitializeDLLs+0x194() in kernel32 (0x7e608ce8)
  6 0x7b86ddcd NE_InitializeDLLs+0x1cd() in kernel32 (0x7e609018)
  7 0x7b86ddcd NE_InitializeDLLs+0x1cd() in kernel32 (0x7e609348)
  8 0x7b89315e InitTask16+0xae() in kernel32 (0x7e609378)
  9 0x7b82f078 in kernel32 (+0xf078) (0x7e609388)
  10 0x7b8a3692 in kernel32 (+0x83692) (0x7e609698)
  11 0x205f:0x02a6 (0x21bf:0x0000)
err:ntdll:RtlpWaitForCriticalSection section 0x7b92b280 "syslevel.c: Win16Mutex" wait timed out in thread 0020, blocked by 0021, retrying (60 sec)
```

---

