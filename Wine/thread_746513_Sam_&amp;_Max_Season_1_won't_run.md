---
title: "Sam &amp; Max Season 1 won't run"
date: 2008-04-05
forum: Wine
---

### Post by pormogo on 2008-04-05
So the other day I got the disc collection of Sam and Max Season 1 from my friend. I wanted to try it out so I went ahead and installed it using wine (9.58 from winehq). The installation went pretty well. The progress bar didn't work however the installation did complete and the directories look good to me.

[i]217M    Sam & Max/Sam And Max Episode 3/Pack/data
217M    Sam & Max/Sam And Max Episode 3/Pack
223M    Sam & Max/Sam And Max Episode 3
218M    Sam & Max/Sam And Max Episode 1/Pack/data
218M    Sam & Max/Sam And Max Episode 1/Pack
224M    Sam & Max/Sam And Max Episode 1
237M    Sam & Max/Sam And Max Episode 2/Pack/data
237M    Sam & Max/Sam And Max Episode 2/Pack
242M    Sam & Max/Sam And Max Episode 2
240M    Sam & Max/Sam And Max Episode 6/Pack/data
240M    Sam & Max/Sam And Max Episode 6/Pack
245M    Sam & Max/Sam And Max Episode 6
260M    Sam & Max/Sam And Max Episode 4/Pack/data
260M    Sam & Max/Sam And Max Episode 4/Pack
266M    Sam & Max/Sam And Max Episode 4
204M    Sam & Max/Sam And Max Episode 5/Pack/data
204M    Sam & Max/Sam And Max Episode 5/Pack
209M    Sam & Max/Sam And Max Episode 5
1.4G    Sam & Max/
[/i]

However when I try and run any of the executable I get the below error. 

```
darthbator@Fenrir:~/.wine/drive_c/Program Files/Telltale/Sam & Max/Sam And Max Episode 1$ wine sammax101.exe 
wine: Unhandled page fault on read access to 0x00000010 at address 0x7dc1a6f5 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000010 in 32-bit code (0x7dc1a6f5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7dc1a6f5 ESP:0034e6dc EBP:0034e6e0 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7c0e1560 ECX:7c5bb1c0 EDX:00000005
 ESI:0034e788 EDI:7eb08b9d
Stack dump:
0x0034e6dc:  7eb280ec 0034e9d0 7ea84ac4 7c0e1560
0x0034e6ec:  00008620 7c5bb1c0 7eb08b04 7eb28d0c
0x0034e6fc:  b7e378ac 00000320 00000085 00000001
0x0034e70c:  7dde04c0 b7e36541 7c1074f8 7c0e1560
0x0034e71c:  79800000 0034e750 7dbf5906 7dde04c0
0x0034e72c:  b7e378ac b7e36541 0034e8a8 000003b4
Backtrace:
=>1 0x7dc1a6f5 in i965_dri.so (+0x856f5) (0x0034e6e0)
  2 0x7ea84ac4 IWineD3DImpl_FillGLCaps+0x8594() in wined3d (0x0034e9d0)
  3 0x7ea8de1e InitAdapters+0x1f16() in wined3d (0x0034ee90)
  4 0x7eafd14e WineDirect3DCreate+0x22() in wined3d (0x0034eec0)
  5 0x7eb3de56 Direct3DCreate8+0x84() in d3d8 (0x0034eef0)
  6 0x0054f1cf in sammax101 (+0x14f1cf) (0x00000010)
  7 0x00000000 (0x00000000)
0x7dc1a6f5: movl        0x10(%eax),%eax
Modules:
Module  Address                 Debug info      Name (100 modules)
PE        400000-  b14000       Export          sammax101
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7db95000-7ddec000       Export          i965_dri.so
ELF     7ddec000-7ddf6000       Deferred        libdrm.so.2
ELF     7ddf6000-7ddf9000       Deferred        libxdamage.so.1
ELF     7ddf9000-7de5a000       Deferred        libgl.so.1
ELF     7de5a000-7de77000       Deferred        imm32<elf>
  \-PE  7de60000-7de77000       \               imm32
ELF     7de77000-7dec8000       Deferred        libgcrypt.so.11
ELF     7dec8000-7decc000       Deferred        libgpg-error.so.0
ELF     7decc000-7dedc000       Deferred        libtasn1.so.3
ELF     7dedc000-7dee4000       Deferred        libkrb5support.so.0
ELF     7dee4000-7df12000       Deferred        libcrypt.so.1
ELF     7df12000-7df82000       Deferred        libgnutls.so.13
ELF     7df82000-7dfa7000       Deferred        libk5crypto.so.3
ELF     7dfa7000-7e02f000       Deferred        libkrb5.so.3
ELF     7e02f000-7e058000       Deferred        libgssapi_krb5.so.2
ELF     7e058000-7e08d000       Deferred        libcups.so.2
ELF     7e0b1000-7e0c5000       Deferred        midimap<elf>
  \-PE  7e0c0000-7e0c5000       \               midimap
ELF     7e0c5000-7e0eb000       Deferred        msacm32<elf>
  \-PE  7e0d0000-7e0eb000       \               msacm32
ELF     7e0eb000-7e102000       Deferred        msacm32<elf>
  \-PE  7e0f0000-7e102000       \               msacm32
ELF     7e102000-7e1c8000       Deferred        libasound.so.2
ELF     7e1d9000-7e20e000       Deferred        winealsa<elf>
  \-PE  7e1e0000-7e20e000       \               winealsa
ELF     7e234000-7e266000       Deferred        uxtheme<elf>
  \-PE  7e240000-7e266000       \               uxtheme
ELF     7e266000-7e26f000       Deferred        libxcursor.so.1
ELF     7e26f000-7e274000       Deferred        libxfixes.so.3
ELF     7e274000-7e277000       Deferred        libxcomposite.so.1
ELF     7e277000-7e27d000       Deferred        libxrandr.so.2
ELF     7e27d000-7e285000       Deferred        libxrender.so.1
ELF     7e285000-7e28a000       Deferred        libxdmcp.so.6
ELF     7e28a000-7e28d000       Deferred        libxau.so.6
ELF     7e28d000-7e37e000       Deferred        libx11.so.6
ELF     7e37e000-7e38c000       Deferred        libxext.so.6
ELF     7e38c000-7e391000       Deferred        libxxf86vm.so.1
ELF     7e391000-7e3a9000       Deferred        libice.so.6
ELF     7e3a9000-7e3b1000       Deferred        libsm.so.6
ELF     7e3bb000-7e3bd000       Deferred        libkeyutils.so.1
ELF     7e3bd000-7e3c0000       Deferred        libcom_err.so.2
ELF     7e3c2000-7e450000       Deferred        winex11<elf>
  \-PE  7e3d0000-7e450000       \               winex11
ELF     7e4a4000-7e4c4000       Deferred        libexpat.so.1
ELF     7e4c4000-7e4ef000       Deferred        libfontconfig.so.1
ELF     7e4ef000-7e504000       Deferred        libz.so.1
ELF     7e504000-7e574000       Deferred        libfreetype.so.6
ELF     7e574000-7e615000       Deferred        oleaut32<elf>
  \-PE  7e580000-7e615000       \               oleaut32
ELF     7e615000-7e64a000       Deferred        winspool<elf>
  \-PE  7e620000-7e64a000       \               winspool
ELF     7e64a000-7e750000       Deferred        shell32<elf>
  \-PE  7e660000-7e750000       \               shell32
ELF     7e750000-7e7f0000       Deferred        comdlg32<elf>
  \-PE  7e760000-7e7f0000       \               comdlg32
ELF     7e7f0000-7e804000       Deferred        lz32<elf>
  \-PE  7e800000-7e804000       \               lz32
ELF     7e804000-7e81d000       Deferred        version<elf>
  \-PE  7e810000-7e81d000       \               version
ELF     7e81d000-7e830000       Deferred        libresolv.so.2
ELF     7e841000-7e85f000       Deferred        iphlpapi<elf>
  \-PE  7e850000-7e85f000       \               iphlpapi
ELF     7e85f000-7e8bd000       Deferred        rpcrt4<elf>
  \-PE  7e870000-7e8bd000       \               rpcrt4
ELF     7e8bd000-7e95d000       Deferred        ole32<elf>
  \-PE  7e8d0000-7e95d000       \               ole32
ELF     7e95d000-7e9e9000       Deferred        winmm<elf>
  \-PE  7e970000-7e9e9000       \               winmm
ELF     7e9e9000-7ea33000       Deferred        dsound<elf>
  \-PE  7e9f0000-7ea33000       \               dsound
ELF     7ea33000-7eb2a000       Export          wined3d<elf>
  \-PE  7ea40000-7eb2a000       \               wined3d
ELF     7eb2a000-7eb55000       Export          d3d8<elf>
  \-PE  7eb30000-7eb55000       \               d3d8
ELF     7eb55000-7ec14000       Deferred        comctl32<elf>
  \-PE  7eb60000-7ec14000       \               comctl32
ELF     7ec14000-7ec6a000       Deferred        shlwapi<elf>
  \-PE  7ec20000-7ec6a000       \               shlwapi
ELF     7ec6a000-7ecb4000       Deferred        advapi32<elf>
  \-PE  7ec70000-7ecb4000       \               advapi32
ELF     7ecb4000-7ed4c000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed4c000       \               gdi32
ELF     7ed4c000-7ee88000       Deferred        user32<elf>
  \-PE  7ed60000-7ee88000       \               user32
ELF     7efa7000-7efb2000       Deferred        libnss_files.so.2
ELF     7efb2000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7efef000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cd6000-b7cdf000       Deferred        libnss_compat.so.2
ELF     b7ce0000-b7ce4000       Deferred        libdl.so.2
ELF     b7ce4000-b7e2e000       Deferred        libc.so.6
ELF     b7e2f000-b7e47000       Deferred        libpthread.so.0
ELF     b7e58000-b7f6c000       Deferred        libwine.so.1
ELF     b7f6e000-b7f8a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Telltale\Sam & Max\Sam And Max Episode 1\sammax101.exe
        00000009    0 <==
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000010 
        00000012    0
        00000011    0
Backtrace:
=>1 0x7dc1a6f5 in i965_dri.so (+0x856f5) (0x0034e6e0)
  2 0x7ea84ac4 IWineD3DImpl_FillGLCaps+0x8594() in wined3d (0x0034e9d0)
  3 0x7ea8de1e InitAdapters+0x1f16() in wined3d (0x0034ee90)
  4 0x7eafd14e WineDirect3DCreate+0x22() in wined3d (0x0034eec0)
  5 0x7eb3de56 Direct3DCreate8+0x84() in d3d8 (0x0034eef0)
  6 0x0054f1cf in sammax101 (+0x14f1cf) (0x00000010)
  7 0x00000000 (0x00000000)

```

According to the appdb it should run I'm not quite sure why that happens. Any help would be most appreciated.

---

### Post by cogadh on 2008-04-06
Looks like you have an Intel 965 chipset for a graphics card. The Intel chipsets have historically been difficult with Wine (limitations of the Linux driver). Based on some of the info in that error, it appears that the Intel driver is not able to properly handle the DirectX to OpenGL calls that Wine is making.

---

### Post by pormogo on 2008-04-06
That's unfortunately what I was afraid of. I now wish I had done my homework a little better before I ordered my laptop. My video card is black listed by compiz and has hardly been cooperative with wine so far. Sad too for embedded video the 965 isn't a bad little chip. Oh well, thanks for pointing that out for me.

---

### Post by cogadh on 2008-04-06
Just to give some completely unsolicited and totally biased advice, the next time you are in the market for a new PC or laptop to use Linux on, go for a machine with an Nvidia-based graphics solution. Nvidia's Linux support is excellent and blessedly easy to work with. Their drivers are closed source, however, so if you are trying to go for a completely FOSS machine, it may not be what you want.

---

### Post by pormogo on 2008-04-06
Yeah when I built my frst box to use ubuntu on and it had an ATI video card and fglrx while functional has hardly been the most "current" solution. 

When I ordered my laptop the nvidia chip put this box out of my price range, for some reason, without checking, I figured that of course intel would provide excellent driver support. The forums in my experiance are mostly silent from intel intigrated graphics users. Yeah I feel you on the driver support though.

---

