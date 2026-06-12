---
title: "Civ3 on Wine"
date: 2006-11-15
forum: Wine
---

### Post by turkenator on 2006-11-15
Hi has anyone succesfully run civ3 on ubuntu with wine 
i didnt have much luck
any one know of a how to/guide for installing civ3?

---

### Post by Technophobia on 2006-11-15
More details please. Does it install, or are there any errors?

---

### Post by turkenator on 2006-11-15
it starts installing then it gives me a error mesage when its at 1%

the popup error message reads:
Unhandled Exception
Error Number: 0x80040706
Description: Object reference not set

Setup will now terminate.

The konsole output is as follows

```
turkenator@turkenator-desktop:~$ wine /mnt/iso/Setup.exe
fixme:ole:ITypeInfo_fnRelease destroy child objects
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ole:ITypeInfo_fnRelease destroy child objects
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ole:ITypeInfo_fnRelease destroy child objects
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9e970,0x7fb9e974), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb9f314,0x7fb9f318), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0xb6c2e6e4,0xb6c2e6e8), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0xb6c2e6e0,0xb6c2e6e4), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb8f58c,0x7fb8f590), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb8f454,0x7fb8f458), stub!
fixme:win:SetWindowTextA setting text "InstallShield Wizard" of other process window (nil) should not use SendMessage
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb8efc0,0x7fb8efc4), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb8ee88,0x7fb8ee8c), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb8efbc,0x7fb8efc0), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb8ee84,0x7fb8ee88), stub!
fixme:shell:BrsFolderDlgProc Set selection "c:\\Program Files\\Infogrames Interactive\\Civilization III"
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb8ef9c,0x7fb8efa0), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb8ee64,0x7fb8ee68), stub!
fixme:ole:VARIANT_UserFree handle unknown complex type
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb8ef9c,0x7fb8efa0), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fb8ee64,0x7fb8ee68), stub!
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002 
```

sorry for the long post thanks in advance

---

### Post by edemark on 2006-11-15
Hi according to winehq s app database version 1.00 (which i do not really know how to get as my game installs as 1.07f) gets gold label. Fortunately the latest patched version 1.29f also gets gold label. So you might get lucky after patching to the latest version.

I am going to try it actually as i had to reinstall cedega 4.3-1 (befor i used to use 5.0.2 but in this version it just did not work) to be able to play as this is one of my favorite games. (The other game is Earth 2150 that actually does not work in cedega 4 series but only from 5.0 onward)

good luck

---

### Post by turkenator on 2006-11-16
bump

---

### Post by 11hjpphty76lkjj on 2008-01-10
You have any luck with this?  Curious if I should try.. :)

Thanks

---

### Post by empty pockets on 2008-06-03
I'm also having a problem with Civ3, except I was able to get it to install.  I'm running 1.29f and this is what i got when i went to run the game 

 ```
wine Civilization3.exe
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:font:CreateScalableFontResourceW (0,L"LSANS.fot",L"C:\\Program_Files\\Firaxis_Games\\Civilization_3\\LSANS.TTF",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"LSANS.fot",L"C:\\Program_Files\\Firaxis_Games\\Civilization_3\\LSANS.TTF",(null)): stub
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  1863
  Current serial number in output stream:  1863
wine: Unhandled page fault on read access to 0x00000200 at address 0xb7fbabad (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000200 in 32-bit code (0xb7fbabad).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7fbabad ESP:012fac40 EBP:012fac68 EFLAGS:00210292(   - 00      -RISA1)
 EAX:b7fc2ce0 EBX:b7fc2ff4 ECX:b7fb55b9 EDX:b7cf16ac
 ESI:00000000 EDI:00000000
Stack dump:
0x012fac40:  b7fa7dfc b7fc2ff4 012fac90 7c0356d4
0x012fac50:  012facc4 b7fb1059 7c038964 b7cf4ff4
0x012fac60:  00000000 7c003140 012fac78 b7cf2cb4
0x012fac70:  00000000 b7fc2ff4 012fad58 b7fb55d6
0x012fac80:  00000000 00000000 00000000 00000000
0x012fac90:  7c003148 7c003150 7c00314c b7cf16ac
Backtrace:
=>1 0xb7fbabad in ld-linux.so.2 (+0x12bad) (0x012fac68)
  2 0xb7cf2cb4 GLIBC_2+0xcb4() in libdl.so.2 (0x012fac78)
  3 0xb7fb55d6 in ld-linux.so.2 (+0xd5d6) (0x012fad58)
  4 0xb7cf32bc in libdl.so.2 (+0x12bc) (0x012fad78)
  5 0xb7cf2cea GLIBC_2+0xcea() in libdl.so.2 (0x012fad88)
  6 0x7ec937bd in libgl.so.1 (+0x477bd) (0x012fada8)
  7 0x7ec7384a in libgl.so.1 (+0x2784a) (0x012fadc8)
  8 0x7ec75924 in libgl.so.1 (+0x29924) (0x012fadf8)
  9 0x7ec6eba4 in libgl.so.1 (+0x22ba4) (0x012fae08)
  10 0x7ecb19bc glIsRenderbufferEXT+0x16c() in libgl.so.1 (0x012fae18)
  11 0xb7fb5fdf in ld-linux.so.2 (+0xdfdf) (0x012fafa8)
  12 0xb7d24084 exit+0xd4() in libc.so.6 (0x012fafc8)
  13 0x7ecfe63e in libx11.so.6 (+0x3863e) (0x012ff048)
  14 0x7e4da962 in winex11 (+0x5a962) (0x012ff078)
  15 0x7ecfe73e _XError+0xfe() in libx11.so.6 (0x012ff118)
  16 0x7ed062f1 _XReply+0x231() in libx11.so.6 (0x012ff158)
  17 0x7ec757ce in libgl.so.1 (+0x297ce) (0x012ff188)
  18 0x7ec75d40 glXMakeContextCurrent+0x210() in libgl.so.1 (0x012ff208)
  19 0x7ec76099 glXMakeCurrent+0x29() in libgl.so.1 (0x012ff228)
  20 0x7e4c786f X11DRV_wglMakeCurrent+0xdf() in winex11 (0x012ff298)
  21 0x7eaa4827 wglMakeCurrent+0x67() in gdi32 (0x012ff2c8)
  22 0x0058a308 in civilization3 (+0x18a308) (0x012ff31c)
0xb7fbabad: testb	$0x8,0x200(%edi)
Modules:
Module	Address			Debug info	Name (136 modules)
PE	  400000- 10f1000	Export          civilization3
PE	 1ce0000- 1d9d000	Deferred        sound
PE	10000000-10063000	Deferred        jgl
PE	21100000-2115d000	Deferred        mss32
PE	22100000-22114000	Deferred        mssa3d.m3d
PE	22200000-22215000	Deferred        mssa3d2.m3d
PE	22300000-22311000	Deferred        mssds3ds.m3d
PE	22400000-22414000	Deferred        mssds3dh.m3d
PE	22500000-22514000	Deferred        msseax.m3d
PE	22600000-22616000	Deferred        mssfast.m3d
PE	22700000-22716000	Deferred        mssdolby.m3d
PE	22900000-22912000	Deferred        mssdx7sl.m3d
PE	22a00000-22a12000	Deferred        mssdx7sh.m3d
PE	22b00000-22b13000	Deferred        mssdx7sn.m3d
PE	22c00000-22c18000	Deferred        msseax2.m3d
PE	22d00000-22d62000	Deferred        mssrsx.m3d
PE	24100000-2410d000	Deferred        lowpass.flt
PE	24200000-2420d000	Deferred        highpass.flt
PE	24300000-2430d000	Deferred        bandpass.flt
PE	24400000-2440d000	Deferred        reverb1.flt
PE	24500000-24510000	Deferred        reverb2.flt
PE	24600000-24611000	Deferred        reverb3.flt
PE	24700000-2470d000	Deferred        reson.flt
PE	24800000-24810000	Deferred        phaser.flt
PE	24900000-2490d000	Deferred        parmeq.flt
PE	24a00000-24a0d000	Deferred        mdelay.flt
PE	24b00000-24b0d000	Deferred        sdelay.flt
PE	24c00000-24c0d000	Deferred        ringmod.flt
PE	24d00000-24d0d000	Deferred        flange.flt
PE	24e00000-24e0d000	Deferred        chorus.flt
PE	24f00000-24f10000	Deferred        shelfeq.flt
PE	25100000-2510d000	Deferred        compress.flt
PE	25200000-2520d000	Deferred        autopan.flt
PE	25300000-2530e000	Deferred        laginter.flt
PE	25400000-2540b000	Deferred        capture.flt
PE	26400000-2642c000	Deferred        mssv29.asi
PE	26500000-26525000	Deferred        mssv24.asi
PE	26600000-26627000	Deferred        mssv12.asi
PE	26f00000-26f2a000	Deferred        mp3dec.asi
PE	30000000-3006d000	Deferred        binkw32
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c168000-7c1b2000	Deferred        dsound<elf>
  \-PE	7c170000-7c1b2000	\               dsound
ELF	7def1000-7def5000	Deferred        libgpg-error.so.0
ELF	7def5000-7df42000	Deferred        libgcrypt.so.11
ELF	7df42000-7df52000	Deferred        libtasn1.so.3
ELF	7df52000-7df5a000	Deferred        libkrb5support.so.0
ELF	7df5a000-7df8c000	Deferred        libcrypt.so.1
ELF	7df8c000-7e002000	Deferred        libgnutls.so.13
ELF	7e002000-7e025000	Deferred        libk5crypto.so.3
ELF	7e025000-7e0b2000	Deferred        libkrb5.so.3
ELF	7e0b2000-7e0db000	Deferred        libgssapi_krb5.so.2
ELF	7e0db000-7e10e000	Deferred        libcups.so.2
ELF	7e132000-7e145000	Deferred        libresolv.so.2
ELF	7e157000-7e175000	Deferred        iphlpapi<elf>
  \-PE	7e160000-7e175000	\               iphlpapi
ELF	7e175000-7e1d6000	Deferred        rpcrt4<elf>
  \-PE	7e180000-7e1d6000	\               rpcrt4
ELF	7e1d6000-7e27a000	Deferred        ole32<elf>
  \-PE	7e1e0000-7e27a000	\               ole32
ELF	7e2a2000-7e2d5000	Deferred        uxtheme<elf>
  \-PE	7e2b0000-7e2d5000	\               uxtheme
ELF	7e2d5000-7e2e9000	Deferred        midimap<elf>
  \-PE	7e2e0000-7e2e9000	\               midimap
ELF	7e2e9000-7e30f000	Deferred        msacm32<elf>
  \-PE	7e2f0000-7e30f000	\               msacm32
ELF	7e30f000-7e326000	Deferred        msacm32<elf>
  \-PE	7e310000-7e326000	\               msacm32
ELF	7e326000-7e3e9000	Deferred        libasound.so.2
ELF	7e3e9000-7e41f000	Deferred        winealsa<elf>
  \-PE	7e3f0000-7e41f000	\               winealsa
ELF	7e41f000-7e428000	Deferred        libxcursor.so.1
ELF	7e428000-7e42d000	Deferred        libxfixes.so.3
ELF	7e42d000-7e430000	Deferred        libxcomposite.so.1
ELF	7e430000-7e436000	Deferred        libxrandr.so.2
ELF	7e436000-7e43e000	Deferred        libxrender.so.1
ELF	7e43e000-7e441000	Deferred        libxinerama.so.1
ELF	7e442000-7e445000	Deferred        libkeyutils.so.1
ELF	7e450000-7e453000	Deferred        libcom_err.so.2
ELF	7e453000-7e473000	Deferred        imm32<elf>
  \-PE	7e460000-7e473000	\               imm32
ELF	7e473000-7e50a000	Export          winex11<elf>
  \-PE	7e480000-7e50a000	\               winex11
ELF	7e544000-7e565000	Deferred        libexpat.so.1
ELF	7e565000-7e58f000	Deferred        libfontconfig.so.1
ELF	7e5a1000-7e5b6000	Deferred        libz.so.1
ELF	7e5b6000-7e626000	Deferred        libfreetype.so.6
ELF	7e626000-7e63a000	Deferred        lz32<elf>
  \-PE	7e630000-7e63a000	\               lz32
ELF	7e63a000-7e653000	Deferred        version<elf>
  \-PE	7e640000-7e653000	\               version
ELF	7e653000-7e689000	Deferred        winspool<elf>
  \-PE	7e660000-7e689000	\               winspool
ELF	7e689000-7e748000	Deferred        comctl32<elf>
  \-PE	7e690000-7e748000	\               comctl32
ELF	7e748000-7e7a1000	Deferred        shlwapi<elf>
  \-PE	7e760000-7e7a1000	\               shlwapi
ELF	7e7a1000-7e8b1000	Deferred        shell32<elf>
  \-PE	7e7b0000-7e8b1000	\               shell32
ELF	7e8b1000-7e95c000	Deferred        comdlg32<elf>
  \-PE	7e8c0000-7e95c000	\               comdlg32
ELF	7e95c000-7e9ee000	Deferred        winmm<elf>
  \-PE	7e970000-7e9ee000	\               winmm
ELF	7e9ee000-7ea40000	Deferred        advapi32<elf>
  \-PE	7ea00000-7ea40000	\               advapi32
ELF	7ea40000-7eadb000	Export          gdi32<elf>
  \-PE	7ea50000-7eadb000	\               gdi32
ELF	7eadb000-7ec22000	Deferred        user32<elf>
  \-PE	7eb00000-7ec22000	\               user32
ELF	7ec22000-7ec27000	Deferred        libxdmcp.so.6
ELF	7ec27000-7ec32000	Deferred        libgcc_s.so.1
ELF	7ec32000-7ec4a000	Deferred        libxcb.so.1
ELF	7ec4a000-7ec4c000	Deferred        libxcb-xlib.so.0
ELF	7ec4c000-7ecc6000	Export          libgl.so.1
ELF	7ecc6000-7edad000	Export          libx11.so.6
ELF	7edad000-7edbb000	Deferred        libxext.so.6
ELF	7edbb000-7edc0000	Deferred        libxxf86vm.so.1
ELF	7edc0000-7edd8000	Deferred        libice.so.6
ELF	7edd8000-7ede0000	Deferred        libsm.so.6
ELF	7edf2000-7ee73000	Deferred        opengl32<elf>
  \-PE	7ee10000-7ee73000	\               opengl32
ELF	7ef93000-7ef9e000	Deferred        libnss_files.so.2
ELF	7ef9e000-7efa8000	Deferred        libnss_nis.so.2
ELF	7efa8000-7efc0000	Deferred        libnsl.so.1
ELF	7efc0000-7efc9000	Deferred        libnss_compat.so.2
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	7efef000-7eff2000	Deferred        libxau.so.6
ELF	b7cf2000-b7cf6000	Export          libdl.so.2
ELF	b7cf6000-b7e45000	Export          libc.so.6
ELF	b7e46000-b7e5e000	Deferred        libpthread.so.0
ELF	b7e70000-b7fa6000	Deferred        libwine.so.1
ELF	b7fa8000-b7fc4000	Export          ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program_Files\Firaxis_Games\Civilization_3\Civilization3.exe
	00000034    0
	00000033   15
	00000009    0 <==
0000000c 
	00000016    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>1 0xb7fbabad in ld-linux.so.2 (+0x12bad) (0x012fac68)
  2 0xb7cf2cb4 GLIBC_2+0xcb4() in libdl.so.2 (0x012fac78)
  3 0xb7fb55d6 in ld-linux.so.2 (+0xd5d6) (0x012fad58)
  4 0xb7cf32bc in libdl.so.2 (+0x12bc) (0x012fad78)
  5 0xb7cf2cea GLIBC_2+0xcea() in libdl.so.2 (0x012fad88)
  6 0x7ec937bd in libgl.so.1 (+0x477bd) (0x012fada8)
  7 0x7ec7384a in libgl.so.1 (+0x2784a) (0x012fadc8)
  8 0x7ec75924 in libgl.so.1 (+0x29924) (0x012fadf8)
  9 0x7ec6eba4 in libgl.so.1 (+0x22ba4) (0x012fae08)
  10 0x7ecb19bc glIsRenderbufferEXT+0x16c() in libgl.so.1 (0x012fae18)
  11 0xb7fb5fdf in ld-linux.so.2 (+0xdfdf) (0x012fafa8)
  12 0xb7d24084 exit+0xd4() in libc.so.6 (0x012fafc8)
  13 0x7ecfe63e in libx11.so.6 (+0x3863e) (0x012ff048)
  14 0x7e4da962 in winex11 (+0x5a962) (0x012ff078)
  15 0x7ecfe73e _XError+0xfe() in libx11.so.6 (0x012ff118)
  16 0x7ed062f1 _XReply+0x231() in libx11.so.6 (0x012ff158)
  17 0x7ec757ce in libgl.so.1 (+0x297ce) (0x012ff188)
  18 0x7ec75d40 glXMakeContextCurrent+0x210() in libgl.so.1 (0x012ff208)
  19 0x7ec76099 glXMakeCurrent+0x29() in libgl.so.1 (0x012ff228)
  20 0x7e4c786f X11DRV_wglMakeCurrent+0xdf() in winex11 (0x012ff298)
  21 0x7eaa4827 wglMakeCurrent+0x67() in gdi32 (0x012ff2c8)
  22 0x0058a308 in civilization3 (+0x18a308) (0x012ff31c)
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7ec4a767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0x7ec4a81e]
#2 /usr/lib/libX11.so.6 [0x7ed05518]
#3 /usr/lib/libX11.so.6(XFindContext+0x2a) [0x7ecdb20a]
#4 /usr/bin/../lib/wine/winex11.drv.so [0x7e4ca273]
#5 /usr/bin/../lib/wine/winex11.drv.so(X11DRV_PALETTE_ToPhysical+0x4a) [0x7e4cc52a]
#6 /usr/bin/../lib/wine/winex11.drv.so(X11DRV_SelectPen+0xc6) [0x7e4cd1f6]
#7 /usr/bin/../lib/wine/gdi32.dll.so [0x7eaaee21]
#8 /usr/bin/../lib/wine/gdi32.dll.so(SelectObject+0xa8) [0x7ea9a868]
#9 /usr/bin/../lib/wine/gdi32.dll.so(DeleteDC+0x2a2) [0x7ea732d2]
#10 /usr/bin/../lib/wine/comctl32.dll.so(ImageList_Destroy+0x63) [0x7e6ba1c3]
#11 /usr/bin/../lib/wine/shell32.dll.so(SIC_Destroy+0x79) [0x7e7d4709]
#12 /usr/bin/../lib/wine/shell32.dll.so [0x7e7ddc72]
#13 /usr/bin/../lib/wine/shell32.dll.so [0x7e81ad1e]
#14 /usr/bin/../lib/wine/ntdll.dll.so [0x7bc44275]
#15 /usr/bin/../lib/wine/ntdll.dll.so [0x7bc462d3]
#16 /usr/bin/../lib/wine/ntdll.dll.so [0x7bc466b8]
#17 /usr/bin/../lib/wine/kernel32.dll.so(ExitProcess+0x1f) [0x7b873f9f]
#18 [0x595594]
#19 /usr/bin/../lib/wine/kernel32.dll.so [0x7b8773a7]
darren@darren-laptop:~/.wine/drive_c/Program_Files/Firaxis_Games/Civilization_3$ 
darren@darren-laptop:~/.wine/drive_c/Program_Files/Firaxis_Games/Civilization_3$ 
```

---

### Post by ram4nd on 2008-09-22
The complete version of Civ 3 installed fine for me, but when I try to run the game then I get some weird font error(error code 13).

```
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:font:CreateScalableFontResourceW (0,L"LSANS.fot",L"C:\\C3\\Conquests\\LSANS.TTF",(null)): stub
fixme:dsound:DllCanUnloadNow (void): stub

```

---

### Post by lindanux on 2008-12-14
I've almost done it, but my x-server crashes.
The game installed ok. Then I run 
~wine civilization3.exe 
and it started ok, with intro movie ok, but fot the first menu, the screen started to move from left to right again and again.... I get no luck in resolving this problem, because I always had to restart my computer after this...

---

### Post by ales on 2009-04-19
> **ram4nd said:**
> The complete version of Civ 3 installed fine for me, but when I try to run the game then I get some weird font error(error code 13).

```
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:font:CreateScalableFontResourceW (0,L"LSANS.fot",L"C:\\C3\\Conquests\\LSANS.TTF",(null)): stub
fixme:dsound:DllCanUnloadNow (void): stub

```



Well same problem here. It seems that it is more problem with the switching the resolution for the game. I have also the complete version on one DVD. Installation works 100%, no errors. After first run Error 13, which also deletes the file Lsans.fot from the .../Conquests  directory. I copied it back and used in that folder:

sudo chown root lsans.fot

After it I started conquest again. Now there is no error 13, but Error 28 with the following decription in terminal:

fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:font:CreateScalableFontResourceW (0,L"LSANS.fot",L"C:\\Program Files\\CIV3\\Conquests\\LSANS.TTF",(null)): stub
fixme:dsound:DllCanUnloadNow (void): stub
[email]dreamwalker@dreamwalker-desktop:~/.wine[/email]/drive_c/Program Files/CIV3/Conquests$ 

Changing something in xorg.conf is not for me as I am not capable of fully understanding of it. Tried, but without result.

ANy idea?

---

### Post by NightMKoder on 2009-04-19
There is a (nasty) workaround near the bottom of the bug report: [http://bugs.winehq.org/show_bug.cgi?id=3498](http://bugs.winehq.org/show_bug.cgi?id=3498)

---

### Post by Ascendaeus on 2009-07-25
i downloaded civ 4, put it in the fake c; drive and clicked on it, it's all bad no response. halo glitches out but it installed, fallout three installed but won't play, civ 4on the other hand doesn't work at all. morrowind gives me error 256 when i try to play, but it installed.

---

