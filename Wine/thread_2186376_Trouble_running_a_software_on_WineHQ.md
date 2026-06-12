---
title: "Trouble running a software on WineHQ"
date: 2013-11-07
forum: Wine
---

### Post by gowtham-pro on 2013-11-07
Hello guys! I am new to Wine and Linux in general. I am currently planning to permanently migrating to Ubuntu from Windows 8. And I have been fooling around with Ubuntu 12.04 for a while. I'm at the final point of my migration process. I really need this software to run on my Linux destro. It's called WordFlood 2.0. Not a popular software but quintessential for me. 


Anyways installed this software with Wine and installation went without any problem. But when I launch the application I get an error. 


I am submitted the dump here just in case you people need to take look. 


> 
Unhandled exception: page fault on read access to 0x00000160 in 32-bit code (0x0042fe6b).
Register dump:Q
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0042fe6b ESP:0032f1d0 EBP:0032f1d0 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:0000e900 EBX:00000000 ECX:00000114 EDX:00000000
 ESI:00000000 EDI:0073030c
Stack dump:
0x0032f1d0:  0032f1dc 004334fa 0000e900 0032f294
0x0032f1e0:  0040975d 00000000 00000000 004108a1
0x0032f1f0:  0040f226 4ce7894e 007303d5 0073030c
0x0032f200:  00734838 00000000 01599ae8 0073030c
0x0032f210:  00000000 00000001 005d1618 0032f101
0x0032f220:  7bc4bd4a 005cf7f8 00000000 005cbb08
Backtrace:
=>0 0x0042fe6b in wordflood 2.0 (+0x2fe6b) (0x0032f1d0)
  1 0x004334fa in wordflood 2.0 (+0x334f9) (0x0032f1dc)
  2 0x0040975d in wordflood 2.0 (+0x975c) (0x0032f294)
  3 0x0040f7fa in wordflood 2.0 (+0xf7f9) (0x0032f2e0)
  4 0x7eceff8a WINPROC_wrapper+0x19() in user32 (0x0032f310)
  5 0x7ecf06dc in user32 (+0xa06db) (0x0032f360)
  6 0x7ecf2ced in user32 (+0xa2cec) (0x0032f3b0)
  7 0x7ecb2d31 in user32 (+0x62d30) (0x0032f420)
  8 0x7ecb9866 in user32 (+0x69865) (0x0032f4a0)
  9 0x7ecb9cdc SendMessageW+0x4b() in user32 (0x0032f4f0)
  10 0x7ece1e40 SetWindowTextW+0x7f() in user32 (0x0032f530)
  11 0x0042ffe8 in wordflood 2.0 (+0x2ffe7) (0x0032f544)
  12 0x0041e2d2 in wordflood 2.0 (+0x1e2d1) (0x0032f578)
  13 0x00447b55 in wordflood 2.0 (+0x47b54) (0x0032f590)
  14 0x00446968 in wordflood 2.0 (+0x46967) (0x0032f5cc)
  15 0x0045d2e7 in wordflood 2.0 (+0x5d2e6) (0x0032f674)
  16 0x0041c0cf in wordflood 2.0 (+0x1c0ce) (0x0032fdcc)
  17 0x0054f47e in wordflood 2.0 (+0x14f47d) (0x0032fde0)
  18 0x00464a7c in wordflood 2.0 (+0x64a7b) (0x0032fe70)
  19 0x7b859cdc call_process_entry+0xb() in kernel32 (0x0032fe88)
  20 0x7b85af4f in kernel32 (+0x4af4e) (0x0032fec8)
  21 0x7bc71db0 call_thread_func_wrapper+0xb() in ntdll (0x0032fed8)
  22 0x7bc7486d call_thread_func+0x7c() in ntdll (0x0032ffa8)
  23 0x7bc71d8e RtlRaiseException+0x21() in ntdll (0x0032ffc8)
  24 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0032ffe8)
0x0042fe6b: cmpl	$0,0x4c(%ecx)
Modules:
Module	Address			Debug info	Name (94 modules)
PE	  400000-  618000	Export          wordflood 2.0
PE	  940000-  9d3000	Deferred        wwde~11m
ELF	7b800000-7ba15000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba15000	\               kernel32
ELF	7bc00000-7bcc3000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7daac000-7db05000	Deferred        riched20<elf>
  \-PE	7dac0000-7db05000	\               riched20
ELF	7db0a000-7db13000	Deferred        librt.so.1
ELF	7db13000-7db18000	Deferred        libgpg-error.so.0
ELF	7db18000-7db30000	Deferred        libresolv.so.2
ELF	7db30000-7db79000	Deferred        libdbus-1.so.3
ELF	7db79000-7db8b000	Deferred        libp11-kit.so.0
ELF	7db8b000-7dc10000	Deferred        libgcrypt.so.11
ELF	7dc10000-7dc22000	Deferred        libtasn1.so.3
ELF	7dc22000-7dc2b000	Deferred        libkrb5support.so.0
ELF	7dc2b000-7dc30000	Deferred        libcom_err.so.2
ELF	7dc30000-7dc58000	Deferred        libk5crypto.so.3
ELF	7dc58000-7dd27000	Deferred        libkrb5.so.3
ELF	7dd27000-7dd39000	Deferred        libavahi-client.so.3
ELF	7dd39000-7ddfd000	Deferred        libgnutls.so.26
ELF	7ddfd000-7de3b000	Deferred        libgssapi_krb5.so.2
ELF	7de3b000-7de8e000	Deferred        libcups.so.2
ELF	7de8f000-7dea2000	Deferred        gnome-keyring-pkcs11.so
ELF	7ded0000-7df04000	Deferred        uxtheme<elf>
  \-PE	7dee0000-7df04000	\               uxtheme
ELF	7df04000-7df0a000	Deferred        libxfixes.so.3
ELF	7df0a000-7df15000	Deferred        libxcursor.so.1
ELF	7df15000-7df19000	Deferred        libkeyutils.so.1
ELF	7df19000-7df27000	Deferred        libavahi-common.so.3
ELF	7df86000-7dfb0000	Deferred        libexpat.so.1
ELF	7dfb0000-7dfe4000	Deferred        libfontconfig.so.1
ELF	7dfe4000-7dff4000	Deferred        libxi.so.6
ELF	7dff4000-7dff8000	Deferred        libxcomposite.so.1
ELF	7dff8000-7e001000	Deferred        libxrandr.so.2
ELF	7e001000-7e00b000	Deferred        libxrender.so.1
ELF	7e00b000-7e011000	Deferred        libxxf86vm.so.1
ELF	7e011000-7e015000	Deferred        libxinerama.so.1
ELF	7e015000-7e037000	Deferred        imm32<elf>
  \-PE	7e020000-7e037000	\               imm32
ELF	7e037000-7e03e000	Deferred        libxdmcp.so.6
ELF	7e03e000-7e042000	Deferred        libxau.so.6
ELF	7e042000-7e063000	Deferred        libxcb.so.1
ELF	7e063000-7e07d000	Deferred        libice.so.6
ELF	7e07d000-7e1b1000	Deferred        libx11.so.6
ELF	7e1b1000-7e1c3000	Deferred        libxext.so.6
ELF	7e1c3000-7e256000	Deferred        winex11<elf>
  \-PE	7e1d0000-7e256000	\               winex11
ELF	7e256000-7e26c000	Deferred        libz.so.1
ELF	7e26c000-7e306000	Deferred        libfreetype.so.6
ELF	7e31a000-7e342000	Deferred        msacm32<elf>
  \-PE	7e320000-7e342000	\               msacm32
ELF	7e342000-7e3ef000	Deferred        winmm<elf>
  \-PE	7e350000-7e3ef000	\               winmm
ELF	7e3ef000-7e4e1000	Deferred        oleaut32<elf>
  \-PE	7e410000-7e4e1000	\               oleaut32
ELF	7e4e1000-7e556000	Deferred        rpcrt4<elf>
  \-PE	7e4f0000-7e556000	\               rpcrt4
ELF	7e556000-7e65e000	Deferred        ole32<elf>
  \-PE	7e570000-7e65e000	\               ole32
ELF	7e65e000-7e696000	Deferred        oledlg<elf>
  \-PE	7e660000-7e696000	\               oledlg
ELF	7e696000-7e6d0000	Deferred        winspool<elf>
  \-PE	7e6a0000-7e6d0000	\               winspool
ELF	7e6d0000-7e7c8000	Deferred        comctl32<elf>
  \-PE	7e6e0000-7e7c8000	\               comctl32
ELF	7e7c8000-7e832000	Deferred        shlwapi<elf>
  \-PE	7e7e0000-7e832000	\               shlwapi
ELF	7e832000-7ea43000	Deferred        shell32<elf>
  \-PE	7e840000-7ea43000	\               shell32
ELF	7ea43000-7eb22000	Deferred        comdlg32<elf>
  \-PE	7ea50000-7eb22000	\               comdlg32
ELF	7eb22000-7eb82000	Deferred        advapi32<elf>
  \-PE	7eb30000-7eb82000	\               advapi32
ELF	7eb82000-7ec3f000	Deferred        gdi32<elf>
  \-PE	7eb90000-7ec3f000	\               gdi32
ELF	7ec3f000-7ed7f000	Dwarf           user32<elf>
  \-PE	7ec50000-7ed7f000	\               user32
ELF	7ed7f000-7ed98000	Deferred        version<elf>
  \-PE	7ed80000-7ed98000	\               version
ELF	7ef98000-7efa5000	Deferred        libnss_files.so.2
ELF	7efa5000-7efb1000	Deferred        libnss_nis.so.2
ELF	7efb1000-7efcb000	Deferred        libnsl.so.1
ELF	7efcb000-7efd4000	Deferred        libnss_compat.so.2
ELF	7efd4000-7f000000	Deferred        libm.so.6
ELF	b7461000-b7467000	Deferred        libuuid.so.1
ELF	b7468000-b746d000	Deferred        libdl.so.2
ELF	b746d000-b7616000	Deferred        libc.so.6
ELF	b7617000-b7632000	Deferred        libpthread.so.0
ELF	b7635000-b763e000	Deferred        libsm.so.6
ELF	b7646000-b7788000	Dwarf           libwine.so.1
ELF	b778a000-b77ac000	Deferred        ld-linux.so.2
ELF	b77ac000-b77ad000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\WordFlood 2.0\WordFlood 2.0.exe
	00000024    0
	00000009    0 <==
0000000e services.exe
	00000020    0
	0000001f    0
	00000019    0
	00000018    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001b    0
	0000001a    0
	00000014    0
	00000013    0
0000001c plugplay.exe
	00000021    0
	0000001e    0
	0000001d    0
00000022 explorer.exe
	00000023    0
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.8.0-29-generic



If I mount the Windows partition (dual-boot) and run the .exe with Wine I get the following error.


> 
Can't create instance of WWDev3 COM class. Check if WWDevCOM3.dll is registered.



I have no clue what to do. 


FYI: I tried running several other software on Wine and they seem to work.

---

### Post by Bucky Ball on 2013-11-07
You might find something here.

[http://www.winehq.org/search?cx=partner-pub-0971840239976722%3Aw9sqbcsxtyf&cof=FORID%3A10&ie=UTF-8&q=WordFlood&siteurl=appdb.winehq.org%2F&ref=appdb.winehq.org%2F&ss=80j6400j2](http://www.winehq.org/search?cx=partner-pub-0971840239976722%3Aw9sqbcsxtyf&cof=FORID%3A10&ie=UTF-8&q=WordFlood&siteurl=appdb.winehq.org%2F&ref=appdb.winehq.org%2F&ss=80j6400j2)

---

### Post by gowtham-pro on 2013-11-07
Thanks for the link. However, I wasn't able to find anything useful there. One more thing is that the application needs .Net. I installed .Net 2.0 and it still doesn't fix it. I will still look for a solution and post it here if am fortunate enough.

---

### Post by Mark Phelps on 2013-11-07
You can't use Wine to run windows apps installed natively in MS Windows; you have to reinstall the apps in Ubuntu using Wine.

---

### Post by gowtham-pro on 2013-11-07
I tried both ways. The log I have submitted was generated when I tried to run it from the .exe natively installed on Ubuntu.

---

### Post by Bucky Ball on 2013-11-07
> **gowtham-pro said:**
> I tried both ways. The log I have submitted was generated when I tried to run it from the .exe natively installed on Ubuntu.

You mean installed with Wine on Ubuntu? An .exe file won't install natively on Ubuntu.

---

