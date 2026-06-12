---
title: "Wine Onenote 2013"
date: 2017-07-05
forum: Wine
---

### Post by kasydo on 2017-07-05
HI I'm new with wine in Ubuntu.
I want to use onenote 2013 with Ubuntu and I cannot install it .
Here is the errors:

Cannot find file
And 
These One:
```
Unhandled exception: unimplemented function api-ms-win-crt-locale-l1-1-0.dl.__initialize_lconv_for_unsigned_char called in 64-bit code (0x000000007b44f037).
Register dump:
 rip:000000007b44f037 rsp:000000000023fa30 rbp:000000000023fba0 eflags:00000206 (   - --  I   - -P- )
 rax:000000000023fa50 rbx:000000000023fbd0 rcx:000000000023fa50 rdx:000000000023fa70
 rsi:000000000023fbe0 rdi:000000000023fa80  r8:0000000000000002  r9:000000000023fbd0 r10:fffffffffffff8aa
 r11:0000000000000246 r12:0000000000000000 r13:000000014025c350 r14:000000007b47c510 r15:00007fffff7e8000
Stack dump:
0x000000000023fa30:  000000000023fa50 0000000000000000
0x000000000023fa40:  0000000000000000 0000000000000000
0x000000000023fa50:  0000000180000100 0000000000000000
0x000000000023fa60:  000000007b44f037 0000000000000002
0x000000000023fa70:  00007f0f36edab65 00007f0f36edab86
0x000000000023fa80:  000000000023fb70 00007f0f3852bcb6
0x000000000023fa90:  000000007b496e20 0000000000000000
0x000000000023faa0:  000000014025c350 000000007b47c510
0x000000000023fab0:  000000000023fbd0 0000000000000000
0x000000000023fac0:  0000000000000000 2020202020202020
0x000000000023fad0:  2020202020202020 702074656a626f27
0x000000000023fae0:  3aa9c36761747261 89159159cf684200
Backtrace:
=>0 0x000000007b44f037 in kernel32 (+0x2f037) (0x000000000023fba0)
  1 0x00007f0f36edab54 in api-ms-win-crt-locale-l1-1-0 (+0xab53) (0x000000000023fd00)
  2 0x00007f0f36eda927 in api-ms-win-crt-locale-l1-1-0 (+0xa926) (0x000000000023fd00)
  3 0x00007f0f3852032c _initterm_e+0x8b() in ucrtbase (0x000000000023fd00)
  4 0x00000001401f37f4 in officeclicktorun (+0x1f37f3) (0x000000000023fe40)
  5 0x000000007b47c5cf in kernel32 (+0x5c5ce) (0x000000000023fe40)
  6 0x000000007bc99a83 call_thread_func+0xd2() in ntdll (0x00007fff425543f0)
  7 0x000000007bc92742 RtlRaiseException+0x7d() in ntdll (0x00007fff425543f0)
  8 0x000000007bc5ed30 in ntdll (+0x3ed2f) (0x00007fff425543f0)
  9 0x00007f0f3ca8af83 wine_call_on_stack+0x12() in libwine.so.1 (0x00007fff425543f0)
  10 0x00007f0f3ca8b0e9 wine_switch_to_stack+0x8() in libwine.so.1 (0x00007fff42554540)
  11 0x000000007bc6545c LdrInitializeThunk+0x31b() in ntdll (0x00007fff42554540)
  12 0x000000007b483993 __wine_kernel_init+0xb02() in kernel32 (0x00007fff425557c0)
  13 0x000000007bc66558 __wine_process_init+0x177() in ntdll (0x00007fff42555800)
  14 0x00007f0f3ca897b2 wine_init+0x2c1() in libwine.so.1 (0x00007fff42555900)
  15 0x000000007c000b42 main+0x81() in <wine-loader> (0x00007fff42555e08)
  16 0x00007f0f3c49c830 __libc_start_main+0xef() in libc.so.6 (0x000000007c000d10)
  17 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  18 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  19 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  20 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  21 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  22 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  23 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  24 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  25 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  26 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  27 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  28 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  29 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  30 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  31 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  32 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  33 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  34 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  35 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  36 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)


ET Caetera
ET Caetera


  199 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
  200 0x000000007c000c39 _start+0x28() in <wine-loader> (0x0000000000000000)
0x000000007b44f037: movq	0x00000000000000b8(%rsp),%rax
Modules:
Module	Address					Debug info	Name (90 modules)
ELF	        7b400000-        7b811000	Dwarf           kernel32<elf>
  \-PE	        7b420000-        7b811000	\               kernel32
ELF	        7bc00000-        7bd1d000	Dwarf           ntdll<elf>
  \-PE	        7bc20000-        7bd1d000	\               ntdll
ELF	        7c000000-        7c004000	Dwarf           <wine-loader>
PE	       140000000-       140436000	Export          officeclicktorun
PE	       180000000-       180076000	Deferred        apiclient
PE	    7f0f3557c000-    7f0f35790000	Deferred        api-ms-win-core-localization-l1-
PE	    7f0f35580000-    7f0f35790000	Deferred        api-ms-win-core-localization-l1-C:\windows\system32\api-ms-win-core-localization-l1-2-1.dll
ELF	    7f0f35790000-    7f0f359a3000	Deferred        api-ms-win-core-fibers-l1-1-1<el
PE	    7f0f357a0000-    7f0f359a3000	Deferred        api-ms-win-core-fibers-l1-1-1
ELF	    7f0f359a3000-    7f0f35bb7000	Deferred        api-ms-win-core-synch-l1-2-0<elf
PE	    7f0f359b0000-    7f0f35bb7000	Deferred        api-ms-win-core-synch-l1-2-0
ELF	    7f0f35bb7000-    7f0f35ec0000	Deferred        msvcr120<elf>
  \-PE	    7f0f35be0000-    7f0f35ec0000	\               msvcr120
ELF	    7f0f35ec0000-    7f0f360e1000	Deferred        concrt140<elf>
  \-PE	    7f0f35ed0000-    7f0f360e1000	\               concrt140
ELF	    7f0f360e1000-    7f0f36309000	Deferred        imm32<elf>
  \-PE	    7f0f360f0000-    7f0f36309000	\               imm32
ELF	    7f0f3635d000-    7f0f36586000	Deferred        libexpat.so.1
ELF	    7f0f36586000-    7f0f367c9000	Deferred        libfontconfig.so.1
ELF	    7f0f367c9000-    7f0f369ee000	Deferred        libpng12.so.0
ELF	    7f0f369ee000-    7f0f36c98000	Deferred        libfreetype.so.6
ELF	    7f0f36cb5000-    7f0f36ec9000	Deferred        rstrtmgr<elf>
  \-PE	    7f0f36cc0000-    7f0f36ec9000	\               rstrtmgr
ELF	    7f0f36ec9000-    7f0f370dc000	Dwarf           api-ms-win-crt-locale-l1-1-0<elf
PE	    7f0f36ed0000-    7f0f370dc000	DIA             api-ms-win-crt-locale-l1-1-0
ELF	    7f0f370dc000-    7f0f372f5000	Deferred        api-ms-win-crt-math-l1-1-0<elf>
  \-PE	    7f0f370e0000-    7f0f372f5000	\               api-ms-win-crt-math-l1-1-0
PE	    7f0f372f5000-    7f0f37509000	Deferred        api-ms-win-crt-filesystem-l1-1-0
PE	    7f0f37300000-    7f0f37509000	Deferred        api-ms-win-crt-filesystem-l1-1-0C:\windows\system32\api-ms-win-crt-filesystem-l1-1-0.dll
ELF	    7f0f37509000-    7f0f3771d000	Deferred        api-ms-win-crt-utility-l1-1-0<el
PE	    7f0f37510000-    7f0f3771d000	Deferred        api-ms-win-crt-utility-l1-1-0
ELF	    7f0f3771d000-    7f0f37932000	Deferred        api-ms-win-crt-convert-l1-1-0<el
PE	    7f0f37720000-    7f0f37932000	Deferred        api-ms-win-crt-convert-l1-1-0
ELF	    7f0f37932000-    7f0f37b48000	Deferred        api-ms-win-crt-string-l1-1-0<elf
PE	    7f0f37940000-    7f0f37b48000	Deferred        api-ms-win-crt-string-l1-1-0
ELF	    7f0f37b48000-    7f0f37d5d000	Deferred        api-ms-win-crt-stdio-l1-1-0<elf>
  \-PE	    7f0f37b50000-    7f0f37d5d000	\               api-ms-win-crt-stdio-l1-1-0
ELF	    7f0f37d5d000-    7f0f37f71000	Deferred        api-ms-win-crt-heap-l1-1-0<elf>
  \-PE	    7f0f37d60000-    7f0f37f71000	\               api-ms-win-crt-heap-l1-1-0
ELF	    7f0f37f71000-    7f0f38186000	Deferred        api-ms-win-crt-runtime-l1-1-0<el
PE	    7f0f37f80000-    7f0f38186000	Deferred        api-ms-win-crt-runtime-l1-1-0
ELF	    7f0f38186000-    7f0f384d1000	Deferred        msvcp140<elf>
  \-PE	    7f0f381c0000-    7f0f384d1000	\               msvcp140
ELF	    7f0f384d1000-    7f0f387eb000	Dwarf           ucrtbase<elf>
  \-PE	    7f0f38500000-    7f0f387eb000	\               ucrtbase
ELF	    7f0f387eb000-    7f0f38a01000	Deferred        vcruntime140<elf>
  \-PE	    7f0f387f0000-    7f0f38a01000	\               vcruntime140
ELF	    7f0f38a27000-    7f0f38ca7000	Deferred        setupapi<elf>
  \-PE	    7f0f38a40000-    7f0f38ca7000	\               setupapi
ELF	    7f0f38ca7000-    7f0f38ec0000	Deferred        wtsapi32<elf>
  \-PE	    7f0f38cb0000-    7f0f38ec0000	\               wtsapi32
ELF	    7f0f38ec0000-    7f0f391ac000	Deferred        crypt32<elf>
  \-PE	    7f0f38ed0000-    7f0f391ac000	\               crypt32
ELF	    7f0f391ac000-    7f0f393ea000	Deferred        wintrust<elf>
  \-PE	    7f0f391b0000-    7f0f393ea000	\               wintrust
ELF	    7f0f393ea000-    7f0f39604000	Deferred        libz.so.1
ELF	    7f0f39604000-    7f0f39825000	Deferred        cabinet<elf>
  \-PE	    7f0f39610000-    7f0f39825000	\               cabinet
ELF	    7f0f39825000-    7f0f39a66000	Deferred        ws2_32<elf>
  \-PE	    7f0f39830000-    7f0f39a66000	\               ws2_32
ELF	    7f0f39a66000-    7f0f39df3000	Deferred        oleaut32<elf>
  \-PE	    7f0f39a90000-    7f0f39df3000	\               oleaut32
ELF	    7f0f39df3000-    7f0f3a08d000	Deferred        rpcrt4<elf>
  \-PE	    7f0f39e00000-    7f0f3a08d000	\               rpcrt4
ELF	    7f0f3a08d000-    7f0f3a2a7000	Deferred        version<elf>
  \-PE	    7f0f3a090000-    7f0f3a2a7000	\               version
ELF	    7f0f3a2a7000-    7f0f3a628000	Deferred        gdi32<elf>
  \-PE	    7f0f3a2c0000-    7f0f3a628000	\               gdi32
ELF	    7f0f3a628000-    7f0f3a9e2000	Deferred        user32<elf>
  \-PE	    7f0f3a650000-    7f0f3a9e2000	\               user32
ELF	    7f0f3a9e2000-    7f0f3ad76000	Deferred        ole32<elf>
  \-PE	    7f0f3aa10000-    7f0f3ad76000	\               ole32
ELF	    7f0f3ad76000-    7f0f3afa3000	Deferred        iphlpapi<elf>
  \-PE	    7f0f3ad80000-    7f0f3afa3000	\               iphlpapi
ELF	    7f0f3afa3000-    7f0f3b239000	Deferred        advapi32<elf>
  \-PE	    7f0f3afb0000-    7f0f3b239000	\               advapi32
ELF	    7f0f3b239000-    7f0f3b44b000	Deferred        libnss_files.so.2
ELF	    7f0f3b44b000-    7f0f3b657000	Deferred        libnss_nis.so.2
ELF	    7f0f3b657000-    7f0f3b870000	Deferred        libnsl.so.1
ELF	    7f0f3b870000-    7f0f3ba79000	Deferred        libnss_compat.so.2
ELF	    7f0f3bd56000-    7f0f3bf6c000	Deferred        libgcc_s.so.1
ELF	    7f0f3bf6c000-    7f0f3c275000	Deferred        libm.so.6
ELF	    7f0f3c278000-    7f0f3c47c000	Deferred        libdl.so.2
ELF	    7f0f3c47c000-    7f0f3c846000	Dwarf           libc.so.6
ELF	    7f0f3c847000-    7f0f3ca64000	Deferred        libpthread.so.0
ELF	    7f0f3ca81000-    7f0f3ce27000	Dwarf           libwine.so.1
ELF	    7f0f3ce29000-    7f0f3d051000	Deferred        ld-linux-x86-64.so.2
ELF	    7fff4255c000-    7fff4255d000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000003b    0
	0000001f    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001e    0
	00000019    0
	00000018    0
	00000013    0
0000001c plugplay.exe
	00000022    0
	00000021    0
	0000001d    0
00000023 explorer.exe
	00000028    0
	00000027    0
	00000026    0
	00000025    0
	00000024    0
00000029 setuponenotefreeretail.x86.en-us_.exe
	0000002e    0
	0000002d    0
	0000002c    0
	0000002b    0
	0000002a    0
0000003c (D) C:\Program Files\Common Files\Microsoft Shared\ClickToRun\OfficeClickToRun.exe
	0000003d    0 <==
System information:
    Wine build: wine-2.0.1
    Platform: x86_64
    Version: Windows 7
    Host system: Linux
    Host version: 4.4.0-83-generic

```

---

### Post by deadflowr on 2017-07-05
*Thread moved to **Wine**.*

---

### Post by QIII on 2017-07-05
@kasydo:

Please either use something like [https://paste.ubuntu.com/](https://paste.ubuntu.com/) to publish your text and add a link or place it between code tags within your post.

You may use code tags in one of the following ways:

1.  Click the # sign above the text input box, place your cursor between the code tags that appear and paste your text.

2.  Paste your text, highlight it and click the # sign.

3.  Type [noparse]```
[/noparse] before you type or paste your text and [noparse]
```[/noparse] after you type or paste your text.  The square brackets are required.

Thanks!


Something that might be of interest for you is the [OneNote 2013 entry in Wine's App Database]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=2911").  OneNote 2013 shows a "Garbage" rating.  The results are fairly old.  Things may have improved, but there is at least an indication that your experience with it may not be satisfactory.

---

### Post by T.J. on 2017-07-05
Welcome Kasydo.

You are having a problem where a Windows function is not implemented by Wine.  I'm sorry to say that Wine is not perfect, nor does it implement all of Windows yet.  I would not expect too much, as Microsoft works (unintentionally) to keep it that way, by changing Windows often.  At this point, you have four realistic options if you want to stick with Linux.

1.  You can dual boot the machine so that it uses both Windows and Linux, and then run OneNote 2013 under Windows.
2. You can use the free online version of OneNote in a browser such as Chrome.
3. You can run Windows and Office in a KVM (or VirtualBox) virtual machine.
4. You can switch to something less dependent on Windows, such as Basket or Zim.

I've personally used all 4 options at one point or another.  I prefer the 4th option, as it means I no longer have to pay for expensive software that only works on Windows.  Zim, in particular, is cross-platform.  It's not exactly the same as OneNote, but one can adapt easily enough. Zim's storage format is not proprietary, so you never have to worry about being locked out of your notes - unlike OneNote.

If you need more information, please let me know.

---

### Post by pythagorean1804 on 2018-05-16
I really wanted this to work too but I ended up just using the web version of the app.  It's got fewer features but all of the main useful parts are implemented in the web version.  I still haven't found anything quite as useful as OneNote but I am certainly open to hearing suggestions if you end up trying out other apps that work on both Ubuntu and Mac OS X.  It would be nice to be able to use the same app on my Macbook Air, my iPad and my Ubuntu desktop.  The OneNote web app is really just about the only thing I have found that is both "free" (as in beer) and cross platform in the sense that you can install a mac version on apple devices.

---

### Post by T.J. on 2018-05-20
As a side note, Microsoft recently announced the sunset for OneNote.  It will be dropped from Office and no longer be developed, except for the online versions like the Windows 10 UWP version that uses OneDrive. 

[https://techcommunity.microsoft.com/t5/Office-365-Blog/The-best-version-of-OneNote-on-Windows/ba-p/183974?utm_source=t.co&utm_medium=referral](https://techcommunity.microsoft.com/t5/Office-365-Blog/The-best-version-of-OneNote-on-Windows/ba-p/183974?utm_source=t.co&utm_medium=referral)

I heartily recommend that you abandon OneNote for a replacement as soon as possible if you need local storage and backups.

---

