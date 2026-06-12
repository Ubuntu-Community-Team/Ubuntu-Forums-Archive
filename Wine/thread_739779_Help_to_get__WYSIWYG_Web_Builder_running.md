---
title: "Help to get  WYSIWYG Web Builder running"
date: 2008-03-30
forum: Wine
---

### Post by bigtel on 2008-03-30
I am trying to run WYSIWYG Web Builder using 'wine' but I am having little success. I have installed it ok onto the C: drive and when I click to run I can see a tab saying 'Starting Web Builder' but after about 5 seconds it disappears and then nothing.

I have tried right clicking and using the 'open with wine' option and I get the same.

I do not know how to use the terminal window to run this - perhaps someone can tell me?

I am using version 0.9.58 of wine.

---

### Post by bigtel on 2008-03-30
Right....

I have taught myself how to use the terminal and this is the output I get from running the program..

err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\WYSIWYG Web Builder 5\\WebBuilder.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\WYSIWYG Web Builder 5\\WebBuilder.exe" failed, status c0000135

Can anyone help?

---

### Post by bigtel on 2008-03-30
Hello me again.
I have downloaded the DLL file and put it into the windows/system32 directory

The program now initiates but I get the following text from the terminal window - this time I really will need some help..!!

Here is a copy of the text..

fixme:mixer:ALSA_MixerInit No master control found on VIA 82XX modem, disabling mixer
wine: Unhandled page fault on read access to 0x00003434 at address 0x4a8f80 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00003434 in 32-bit code (0x004a8f80).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:004a8f80 ESP:0034e554 EBP:00163610 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:001ed8c8 EDX:6c24008c
 ESI:00000000 EDI:00000000
Stack dump:
0x0034e554:  001edbc8 00746524 00163610 00000001
0x0034e564:  0134e554 001b5bd8 6c203172 00163610
0x0034e574:  00146088 6c171264 00146088 0034e5c4
0x0034e584:  0069f8e8 ffffffff 004a8e84 00000000
0x0034e594:  00162398 007610c8 001654a0 00163610
0x0034e5a4:  01163610 001b5bd8 001e8848 001ed8c8
Backtrace:
=>1 0x004a8f80 in webbuilder (+0xa8f80) (0x00163610)
  2 0x00000001 (0x006c60b4)
  3 0x00448390 in webbuilder (+0x48390) (0x00653610)
0x004a8f80: cmpl        %edi,0x3434(%ebx)
Modules:
Module  Address                 Debug info      Name (111 modules)
PE        400000-  847000       Export          webbuilder
PE      6c170000-6c262000       Deferred        mfc42
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ddb7000-7ddca000       Deferred        shfolder<elf>
  \-PE  7ddc0000-7ddca000       \               shfolder
ELF     7ddca000-7dddd000       Deferred        riched32<elf>
  \-PE  7ddd0000-7dddd000       \               riched32
ELF     7dddd000-7de10000       Deferred        gdiplus<elf>
  \-PE  7ddf0000-7de10000       \               gdiplus
ELF     7de10000-7de23000       Deferred        msimg32<elf>
  \-PE  7de20000-7de23000       \               msimg32
ELF     7de23000-7de74000       Deferred        libgcrypt.so.11
ELF     7de74000-7de78000       Deferred        libgpg-error.so.0
ELF     7de78000-7de88000       Deferred        libtasn1.so.3
ELF     7de88000-7de8a000       Deferred        libkeyutils.so.1
ELF     7de8a000-7deb8000       Deferred        libcrypt.so.1
ELF     7deb8000-7df28000       Deferred        libgnutls.so.13
ELF     7df28000-7df4d000       Deferred        libk5crypto.so.3
ELF     7df4d000-7dfd5000       Deferred        libkrb5.so.3
ELF     7dfd5000-7dffe000       Deferred        libgssapi_krb5.so.2
ELF     7dffe000-7e033000       Deferred        libcups.so.2
ELF     7e033000-7e047000       Deferred        midimap<elf>
  \-PE  7e040000-7e047000       \               midimap
ELF     7e047000-7e06d000       Deferred        msacm32<elf>
  \-PE  7e050000-7e06d000       \               msacm32
ELF     7e06d000-7e084000       Deferred        msacm32<elf>
  \-PE  7e070000-7e084000       \               msacm32
ELF     7e084000-7e14a000       Deferred        libasound.so.2
ELF     7e15c000-7e191000       Deferred        winealsa<elf>
  \-PE  7e170000-7e191000       \               winealsa
ELF     7e1c9000-7e1fb000       Deferred        uxtheme<elf>
  \-PE  7e1d0000-7e1fb000       \               uxtheme
ELF     7e1fb000-7e239000       Deferred        urlmon<elf>
  \-PE  7e200000-7e239000       \               urlmon
ELF     7e239000-7e242000       Deferred        libxcursor.so.1
ELF     7e242000-7e247000       Deferred        libxfixes.so.3
ELF     7e247000-7e24a000       Deferred        libxcomposite.so.1
ELF     7e24a000-7e250000       Deferred        libxrandr.so.2
ELF     7e250000-7e258000       Deferred        libxrender.so.1
ELF     7e258000-7e25d000       Deferred        libxdmcp.so.6
ELF     7e25d000-7e260000       Deferred        libxau.so.6
ELF     7e260000-7e351000       Deferred        libx11.so.6
ELF     7e351000-7e35f000       Deferred        libxext.so.6
ELF     7e35f000-7e364000       Deferred        libxxf86vm.so.1
ELF     7e364000-7e37c000       Deferred        libice.so.6
ELF     7e37c000-7e384000       Deferred        libsm.so.6
ELF     7e384000-7e38c000       Deferred        libkrb5support.so.0
ELF     7e391000-7e394000       Deferred        libcom_err.so.2
ELF     7e396000-7e424000       Deferred        winex11<elf>
  \-PE  7e3a0000-7e424000       \               winex11
ELF     7e4a5000-7e4c5000       Deferred        libexpat.so.1
ELF     7e4c5000-7e4f0000       Deferred        libfontconfig.so.1
ELF     7e4f0000-7e505000       Deferred        libz.so.1
ELF     7e505000-7e575000       Deferred        libfreetype.so.6
ELF     7e575000-7e616000       Deferred        oleaut32<elf>
  \-PE  7e580000-7e616000       \               oleaut32
ELF     7e616000-7e629000       Deferred        olepro32<elf>
  \-PE  7e620000-7e629000       \               olepro32
ELF     7e629000-7e65e000       Deferred        winspool<elf>
  \-PE  7e630000-7e65e000       \               winspool
ELF     7e65e000-7e6fe000       Deferred        comdlg32<elf>
  \-PE  7e660000-7e6fe000       \               comdlg32
ELF     7e6fe000-7e763000       Deferred        msvcrt<elf>
  \-PE  7e710000-7e763000       \               msvcrt
ELF     7e782000-7e79f000       Deferred        imm32<elf>
  \-PE  7e790000-7e79f000       \               imm32
ELF     7e79f000-7e7b2000       Deferred        libresolv.so.2
ELF     7e7c4000-7e7e2000       Deferred        iphlpapi<elf>
  \-PE  7e7d0000-7e7e2000       \               iphlpapi
ELF     7e7e2000-7e840000       Deferred        rpcrt4<elf>
  \-PE  7e7f0000-7e840000       \               rpcrt4
ELF     7e840000-7e8e0000       Deferred        ole32<elf>
  \-PE  7e850000-7e8e0000       \               ole32
ELF     7e8e0000-7e928000       Deferred        riched20<elf>
  \-PE  7e8f0000-7e928000       \               riched20
ELF     7e928000-7e9b4000       Deferred        winmm<elf>
  \-PE  7e930000-7e9b4000       \               winmm
ELF     7e9b4000-7ea73000       Deferred        comctl32<elf>
  \-PE  7e9c0000-7ea73000       \               comctl32
ELF     7ea73000-7eb79000       Deferred        shell32<elf>
  \-PE  7ea80000-7eb79000       \               shell32
ELF     7eb79000-7ebcf000       Deferred        shlwapi<elf>
  \-PE  7eb90000-7ebcf000       \               shlwapi
ELF     7ebcf000-7ec19000       Deferred        advapi32<elf>
  \-PE  7ebe0000-7ec19000       \               advapi32
ELF     7ec19000-7ecb1000       Deferred        gdi32<elf>
  \-PE  7ec30000-7ecb1000       \               gdi32
ELF     7ecb1000-7eded000       Deferred        user32<elf>
  \-PE  7ecd0000-7eded000       \               user32
ELF     7eded000-7ee0e000       Deferred        mpr<elf>
  \-PE  7edf0000-7ee0e000       \               mpr
ELF     7ee0e000-7ee5a000       Deferred        wininet<elf>
  \-PE  7ee20000-7ee5a000       \               wininet
ELF     7ee5a000-7ee6e000       Deferred        lz32<elf>
  \-PE  7ee60000-7ee6e000       \               lz32
ELF     7ee6e000-7ee87000       Deferred        version<elf>
  \-PE  7ee70000-7ee87000       \               version
ELF     7efa6000-7efb1000       Deferred        libnss_files.so.2
ELF     7efb1000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7efee000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cb2000-b7cbb000       Deferred        libnss_compat.so.2
ELF     b7cbc000-b7cc0000       Deferred        libdl.so.2
ELF     b7cc0000-b7e0a000       Deferred        libc.so.6
ELF     b7e0a000-b7e22000       Deferred        libpthread.so.0
ELF     b7e34000-b7f48000       Deferred        libwine.so.1
ELF     b7f4a000-b7f66000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\WYSIWYG Web Builder 5\WebBuilder.exe
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
=>1 0x004a8f80 in webbuilder (+0xa8f80) (0x00163610)
  2 0x00000001 (0x006c60b4)
  3 0x00448390 in webbuilder (+0x48390) (0x00653610)



[COLOR="Red"]**help me please...!!!**[/COLOR]

---

### Post by happyhamster on 2008-03-30
> **bigtel said:**
> fixme:mixer:ALSA_MixerInit No master control found on VIA 82XX modem, disabling mixer
Looks like wine doesn't like the sound card or perhaps (one of) the sound modules loaded. Do you have proper sound outside of wine?

---

### Post by bigtel on 2008-03-30
My sound seems OK outside of wine. I have just tried adjusting the settings within wine and I get the same results.

I changed the graphics to 'emulate a virtual desktop' and I now get a start window when I start the program up. It tells me that I have 30 days left of the trial and asked me to continue. I click on continue and the window shuts down...and then nothing.

So I seem to have got a little further into solving this one, but I have to say my knowledge on this is zero really..!

---

### Post by Rodrigo C on 2008-06-26
i have the same problem here :(

---

### Post by bigtel on 2008-06-27
> **Rodrigo C said:**
> i have the same problem here :(

Hey Rodrigo, I am now using Virtualbox to run a version of XP and I run WYSIWYG through that. It works great. I gave up on the wine emulator for this one as I just could not get the support and i did not have a clue..!!

Good lUCK:)

---

