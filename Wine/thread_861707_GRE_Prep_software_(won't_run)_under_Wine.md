---
title: "GRE Prep software (won't run) under Wine"
date: 2008-07-16
forum: Wine
---

### Post by atorch on 2008-07-16
Hi,

Here's a link to the program in question:  [http://stanford.edu/~atorch/PPGRE31.exe](http://stanford.edu/~atorch/PPGRE31.exe)

The original, official link to the same file is here:  [http://www.ets.org/portal/site/ets/menuitem.1488512ecfd5b8849a77b13bc3921509/?vgnextoid=e1752d3631df4010VgnVCM10000022f95190RCRD&vgnextchannel=d687e3b5f64f4010VgnVCM10000022f95190RCRD](http://www.ets.org/portal/site/ets/menuitem.1488512ecfd5b8849a77b13bc3921509/?vgnextoid=e1752d3631df4010VgnVCM10000022f95190RCRD&vgnextchannel=d687e3b5f64f4010VgnVCM10000022f95190RCRD)  (You can give them a fake name and email, or just tell them you're not interested in receiving mail.)

Could you please help me run this program under wine?

When I first ran the installer, I got a "16-bit support missing" error. I googled and found this:  [http://ubuntuforums.org/showthread.php?p=4713701](http://ubuntuforums.org/showthread.php?p=4713701)

Then I ran this command:  ```
sudo sysctl -w vm.mmap_min_addr=0
```

Afterwards the installer ran correctly, but running the program itself does nothing (my desktop will resize itself a few times... and that's it.)

```
wine --version
wine-1.0
```

Any help would be appreciated!

---

### Post by atorch on 2008-07-17
Also, if I run winefile and navigate to and double click on ~/drive_c/Program Files/ETS/PPGRE/PPGRE/PPREP.EXE, I get a strange error:

Could not load POWERPREP
Error Code 2
File was not found.

If I cd to ~/drive_c/Program Files/ETS/PPGRE/PPGRE and run "wine PPGRE.EXE," I get a (much more helpful) error message:

Could not load 'MFC250.DLL' required by 'PPGRE', error=2

Is that a .dll that should have come with the program, or is it something that should be part of wine but was omitted?  If I can find & download it, what directory should I place it in?

// Edit:

Google has led me here:  [http://www.winehq.org/pipermail/wine-users/2006-May/021823.html](http://www.winehq.org/pipermail/wine-users/2006-May/021823.html)

I checked my ~/.wine/drive_c/windows/system directory, and, surely enough, it contains MFC250.DLL.  Why, then, is the program unable to find it?  How can I find out where PPGRE.EXE looks for MFC250.DLL?

// Edit:

Found this:  [http://technalink.com/messages/1.html](http://technalink.com/messages/1.html) and downloaded the "16-bit version" of MFC250.dll; I renamed my version MFC250.original.dll and placed the 16-bit version in the same directory.  I still get the "Could not load 'MFC250.DLL' required by 'PPGRE', error=2," unfortunately.

// Edit:

Also found this:  [http://bugs.winehq.org/show_bug.cgi?id=3766](http://bugs.winehq.org/show_bug.cgi?id=3766)

---

### Post by YokoZar on 2008-07-18
The last link shows it to be a bug in Wine, in which case you probably won't be able to work around it.

One last thing you can try is testing the latest development packages for Wine (that is, version 1.1.1) by going here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Michl on 2008-10-01
I am trying to run under wine, too.  The program seems
to install and it is listed under programs, but
when I click on it, the screen goes blank, then
returns  back to normal and stops trying to run 
powerprep.  Any suggestions... I am trying to show
my skeptical daughter that you can do anything in
linux...

---

### Post by asdfoo on 2008-10-01
> **Michl said:**
> I am trying to run under wine, too.  The program seems
to install and it is listed under programs, but
when I click on it, the screen goes blank, then
returns  back to normal and stops trying to run 
powerprep.  Any suggestions... I am trying to show
my skeptical daughter that you can do anything in
linux...

Can you provide the terminal output?

Open a terminal, eg.  gnome-terminal, cd to the install directory (I'm just guessing below) and run the main executable

cd ~/.wine/drive_c/Program\ Files/GRE Powergrep

ls *.exe

wine powergrep.exe

---

### Post by CarpKing on 2008-10-01
> **atorch said:**
> Also, if I run winefile and navigate to and double click on ~/drive_c/Program Files/ETS/PPGRE/PPGRE/PPREP.EXE, I get a strange error:

Could not load POWERPREP
Error Code 2
File was not found.

If I cd to ~/drive_c/Program Files/ETS/PPGRE/PPGRE and run "wine PPGRE.EXE," I get a (much more helpful) error message:

Could not load 'MFC250.DLL' required by 'PPGRE', error=2

Is that a .dll that should have come with the program, or is it something that should be part of wine but was omitted?  If I can find & download it, what directory should I place it in?

// Edit:

Google has led me here:  [http://www.winehq.org/pipermail/wine-users/2006-May/021823.html](http://www.winehq.org/pipermail/wine-users/2006-May/021823.html)

I checked my ~/.wine/drive_c/windows/system directory, and, surely enough, it contains MFC250.DLL.  Why, then, is the program unable to find it?  How can I find out where PPGRE.EXE looks for MFC250.DLL?

I've been trying to get this to work as well.  I found MFC250.DLL on the CD and copied it to the system32 folder.  This got rid of that error, but gave a similar one with a different DLL.  Repeating the process, I eventually moved over the following:
```
MFC250.DLL
PPOSA.DLL
KBDHOOK.DLL
PRINTING.DLL
GSWDLL.DLL
```

At that point the program started, but the menu items appeared to do nothing.  I believe I eventually copied the whole directory the above files were in into system32.  The menu items that are supposed to open PDFs complain about having nothing to launch, and the actual practice test program causes the whole thing to crash without any error.  When I get around to it I'm going to try running as Windows 3.1, as that's about the age the test software looks when run in Windows.

EDIT: Well, I tried with Windows 3.1 and NT 3.5.  When starting the practice test it now puts up a light blue screen with the old hourglass pointer, but nothing happens after that.

---

### Post by Michl on 2008-10-01
Thanks for the reply.  I was able to move
forward a little.  I had to copy and paste
two .dll files from windows/system (MFC250
and MFC0250) into the file where the .exe
file is.  So now I can get to the main
menu and to some of the links, but it
will not run the tests.  I checked on the
web and it seems that many have this
problem, so perhaps this is hopeless.
But I am thinking that maybe there is
a chance.  Any suggestions?


Also (tp carpking).  YOu also need to
change the display to 640 x 480.  ALso,
I just tried running it 'under' 3.1 and
the tests still do not work.

---

### Post by mjumbewu on 2008-11-04
i haven't gotten everything to run, but what i've done so far is:

```
cd ~/.wine/drive_c/Program Files/ETS/PPGRE
mkdir new
cp -R PPGRE/* new
cp -R PPREP/* new
cp ~/.wine/drive_c/windows/system/*.DLL new
cd new
wine ./PPGRE.EXE
```

(of course, replace "~/.wine" with your wine installation directory)

the above does not run the program in 640x480 (run "wine ./PPREP.EXE PPGRE" if you want that), but that's ok.  i can get a lot of the functionality except for the practice questions or anything else that opens the gre test framework.  when i try the practice questions, i get the following output -- any ideas?:

```
fixme:user:EnableHardwareInput16 (0) - stub
fixme:user:EnableHardwareInput16 (1) - stub
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:ole:CoRegisterMessageFilter16 (0xdf7dc6,(nil)),stub!
fixme:hook:SetWindowsHookEx16 System-global hooks (2) broken in Win16
wine: Unhandled page fault on read access to 0xffffffff at address 0x1fe7:0x0000b609 (thread 001d), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 16-bit code (1fe7:b609).
In 16 bit mode.
Register dump:
 CS:1fe7 SS:1ff7 DS:1ff7 ES:0000 FS:0033 GS:003b
 IP:b609 SP:488e BP:48ae FLAGS:0212(   - 00      - RIA1)
 AX:0000 BX:145c CX:0000 DX:1ff7 SI:145c DI:0000
Stack dump:
0x1ff7:0x488e:  0000 0000 6cbb 1fe7 1011 0000 0000 0000
0x1ff7:0x489e:  0000 0000 4910 1ff7 145c 1950 1fdf 48ba
0x1ff7:0x48ae:  4922 a8df 1fe7 4908 1ff7 4914 1ff7 1011
03fe: sel=1ff7 base=00b9a480 limit=00004f5f 16-bit rw-
Backtrace:
=>1 0x1fe7:0xb609 (0x1ff7:0x48ae)
  2 0x1fe7:0xa8df (0x1ff7:0x4922)
  3 0x1fef:0x6ed5 (0x1ff7:0x495c)
  4 0x1fef:0x7721 (0x1ff7:0x499a)
  5 0x1fef:0x89bd (0x1ff7:0x49b8)
  6 0x1fdf:0x246e (0x1ff7:0x4a04)
  7 0x1fdf:0x17a3 (0x1ff7:0x4a58)
  8 0x1fdf:0x18f4 (0x1ff7:0x4a70)
  9 0x101f:0x0468 in kernel32 (+0x85c28) (0x1ff7:0x4aaa)
  10 0x7b8a45f3 K32WOWCallback16Ex+0xc3() in kernel32 (0x7d259938)
  11 0x7edd6cf3 in user32 (+0xb6cf3) (0x7d259c78)
  12 0x7edd18d8 WINPROC_wrapper+0x688() in user32 (0x7d25a118)
  13 0x7edd6aa1 in user32 (+0xb6aa1) (0x7d25a158)
  14 0x7ed96f97 in user32 (+0x76f97) (0x7d25a1b8)
  15 0x7ed98dec in user32 (+0x78dec) (0x7d25a4e8)
  16 0x7ed9aeba PeekMessageW+0xba() in user32 (0x7d25a548)
  17 0x7ed9b0cc GetMessageW+0xec() in user32 (0x7d25a588)
  18 0x7ed9b1fd GetMessageA+0x5d() in user32 (0x7d25a5a8)
  19 0x7eda026c GetMessage32_16+0x6c() in user32 (0x7d25a608)
  20 0x7eda03bd GetMessage16+0x3d() in user32 (0x7d25a628)
  21 0x7ed31c45 in user32 (+0x11c45) (0x7d25a648)
  22 0x7b8a5836 in kernel32 (+0x85836) (0x7d25a678)
  23 0x1fdf:0x429e (0x1ff7:0x4abe)
  24 0x1fdf:0x4349 (0x1ff7:0x4ace)
  25 0x1fdf:0x3254 (0x1ff7:0x4ae6)
  26 0x1fef:0x2635 (0x1ff7:0x4af8)
  27 0x1fef:0x2602 (0x1ff7:0x0000)
0x1fe7:0xb609: lesw	%es:0x0(%di),%bx
Modules:
Module	Address			Debug info	Name (94 modules)
ELF	7b800000-7b93d000	Export          kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d3b3000-7d3b7000	Deferred        libgpg-error.so.0
ELF	7d3b7000-7d420000	Deferred        libgcrypt.so.11
ELF	7d420000-7d432000	Deferred        libtasn1.so.3
ELF	7d432000-7d436000	Deferred        libkeyutils.so.1
ELF	7d436000-7d43f000	Deferred        libkrb5support.so.0
ELF	7d43f000-7d471000	Deferred        libcrypt.so.1
ELF	7d471000-7d50e000	Deferred        libgnutls.so.26
ELF	7d50e000-7d532000	Deferred        libk5crypto.so.3
ELF	7d532000-7d5c4000	Deferred        libkrb5.so.3
ELF	7d5c4000-7d5ee000	Deferred        libgssapi_krb5.so.2
ELF	7d5ee000-7d624000	Deferred        libcups.so.2
ELF	7d648000-7d65c000	Deferred        libresolv.so.2
ELF	7d674000-7d693000	Deferred        iphlpapi<elf>
  \-PE	7d680000-7d693000	\               iphlpapi
ELF	7d693000-7d6f6000	Deferred        rpcrt4<elf>
  \-PE	7d6a0000-7d6f6000	\               rpcrt4
ELF	7d6f6000-7d79c000	Deferred        ole32<elf>
  \-PE	7d700000-7d79c000	\               ole32
ELF	7d7c4000-7d7f7000	Deferred        uxtheme<elf>
  \-PE	7d7d0000-7d7f7000	\               uxtheme
ELF	7d7f7000-7d82e000	Deferred        winspool<elf>
  \-PE	7d800000-7d82e000	\               winspool
ELF	7d82e000-7d8f3000	Deferred        comctl32<elf>
  \-PE	7d840000-7d8f3000	\               comctl32
ELF	7d8f3000-7d94e000	Deferred        shlwapi<elf>
  \-PE	7d900000-7d94e000	\               shlwapi
ELF	7d94e000-7da62000	Deferred        shell32<elf>
  \-PE	7d960000-7da62000	\               shell32
ELF	7e264000-7e312000	Deferred        comdlg32<elf>
  \-PE	7e270000-7e312000	\               comdlg32
ELF	7e423000-7e44b000	Deferred        msacm32<elf>
  \-PE	7e430000-7e44b000	\               msacm32
ELF	7e44b000-7e464000	Deferred        msacm32<elf>
  \-PE	7e450000-7e464000	\               msacm32
ELF	7e464000-7e4b4000	Deferred        libpulse.so.0
ELF	7e4b7000-7e4cc000	Deferred        midimap<elf>
  \-PE	7e4c0000-7e4cc000	\               midimap
ELF	7e4cc000-7e4d5000	Deferred        librt.so.1
ELF	7e4d5000-7e59d000	Deferred        libasound.so.2
ELF	7e59d000-7e5d4000	Deferred        winealsa<elf>
  \-PE	7e5b0000-7e5d4000	\               winealsa
ELF	7e5d4000-7e668000	Deferred        winmm<elf>
  \-PE	7e5e0000-7e668000	\               winmm
ELF	7e668000-7e6cb000	Deferred        winedos<elf>
  \-PE	7e670000-7e6cb000	\               winedos
ELF	7e6cb000-7e6d4000	Deferred        libxcursor.so.1
ELF	7e6d4000-7e6d9000	Deferred        libxfixes.so.3
ELF	7e6d9000-7e6dd000	Deferred        libxcomposite.so.1
ELF	7e6dd000-7e6e4000	Deferred        libxrandr.so.2
ELF	7e6e4000-7e6ee000	Deferred        libxrender.so.1
ELF	7e6ee000-7e6f1000	Deferred        libxinerama.so.1
ELF	7e6f1000-7e712000	Deferred        imm32<elf>
  \-PE	7e700000-7e712000	\               imm32
ELF	7e712000-7e717000	Deferred        libxdmcp.so.6
ELF	7e717000-7e730000	Deferred        libxcb.so.1
ELF	7e730000-7e733000	Deferred        libxcb-xlib.so.0
ELF	7e733000-7e736000	Deferred        libxau.so.6
ELF	7e736000-7e825000	Deferred        libx11.so.6
ELF	7e825000-7e834000	Deferred        libxext.so.6
ELF	7e834000-7e83a000	Deferred        libxxf86vm.so.1
ELF	7e83a000-7e852000	Deferred        libice.so.6
ELF	7e852000-7e85b000	Deferred        libsm.so.6
ELF	7e864000-7e868000	Deferred        libcom_err.so.2
ELF	7e868000-7e86c000	Deferred        libcap.so.1
ELF	7e86c000-7e873000	Deferred        libasound_module_pcm_pulse.so
ELF	7e873000-7e90e000	Deferred        winex11<elf>
  \-PE	7e880000-7e90e000	\               winex11
ELF	7eb1b000-7eb42000	Deferred        libexpat.so.1
ELF	7eb42000-7eb6f000	Deferred        libfontconfig.so.1
ELF	7eb6f000-7eb85000	Deferred        libz.so.1
ELF	7eb85000-7ebfb000	Deferred        libfreetype.so.6
ELF	7ec13000-7ec66000	Deferred        advapi32<elf>
  \-PE	7ec20000-7ec66000	\               advapi32
ELF	7ec66000-7ed05000	Deferred        gdi32<elf>
  \-PE	7ec80000-7ed05000	\               gdi32
ELF	7ed05000-7ee51000	Export          user32<elf>
  \-PE	7ed20000-7ee51000	\               user32
ELF	7ee51000-7ee5d000	Deferred        libnss_files.so.2
ELF	7ee5d000-7ee68000	Deferred        libnss_nis.so.2
ELF	7ee68000-7ee81000	Deferred        libnsl.so.1
ELF	7ee81000-7ee8a000	Deferred        libnss_compat.so.2
ELF	7ee8c000-7eea2000	Deferred        winevdm<elf>
  \-PE	7ee90000-7eea2000	\               winevdm
ELF	7efc2000-7efe8000	Deferred        libm.so.6
ELF	b7cd2000-b7cd6000	Deferred        libdl.so.2
ELF	b7cd6000-b7e34000	Deferred        libc.so.6
ELF	b7e35000-b7e4e000	Deferred        libpthread.so.0
ELF	b7e66000-b7f9d000	Deferred        libwine.so.1
ELF	b7f9f000-b7fbc000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 (D) C:\windows\system32\winevdm.exe
	0000001d    0 <==
	0000001c    0
	00000019    0
	00000018    0
0000001a 
	0000001b    0
Backtrace:
=>1 0x1fe7:0xb609 (0x1ff7:0x48ae)
  2 0x1fe7:0xa8df (0x1ff7:0x4922)
  3 0x1fef:0x6ed5 (0x1ff7:0x495c)
  4 0x1fef:0x7721 (0x1ff7:0x499a)
  5 0x1fef:0x89bd (0x1ff7:0x49b8)
  6 0x1fdf:0x246e (0x1ff7:0x4a04)
  7 0x1fdf:0x17a3 (0x1ff7:0x4a58)
  8 0x1fdf:0x18f4 (0x1ff7:0x4a70)
  9 0x101f:0x0468 in kernel32 (+0x85c28) (0x1ff7:0x4aaa)
  10 0x7b8a45f3 K32WOWCallback16Ex+0xc3() in kernel32 (0x7d259938)
  11 0x7edd6cf3 in user32 (+0xb6cf3) (0x7d259c78)
  12 0x7edd18d8 WINPROC_wrapper+0x688() in user32 (0x7d25a118)
  13 0x7edd6aa1 in user32 (+0xb6aa1) (0x7d25a158)
  14 0x7ed96f97 in user32 (+0x76f97) (0x7d25a1b8)
  15 0x7ed98dec in user32 (+0x78dec) (0x7d25a4e8)
  16 0x7ed9aeba PeekMessageW+0xba() in user32 (0x7d25a548)
  17 0x7ed9b0cc GetMessageW+0xec() in user32 (0x7d25a588)
  18 0x7ed9b1fd GetMessageA+0x5d() in user32 (0x7d25a5a8)
  19 0x7eda026c GetMessage32_16+0x6c() in user32 (0x7d25a608)
  20 0x7eda03bd GetMessage16+0x3d() in user32 (0x7d25a628)
  21 0x7ed31c45 in user32 (+0x11c45) (0x7d25a648)
  22 0x7b8a5836 in kernel32 (+0x85836) (0x7d25a678)
  23 0x1fdf:0x429e (0x1ff7:0x4abe)
  24 0x1fdf:0x4349 (0x1ff7:0x4ace)
  25 0x1fdf:0x3254 (0x1ff7:0x4ae6)
  26 0x1fef:0x2635 (0x1ff7:0x4af8)
  27 0x1fef:0x2602 (0x1ff7:0x0000)
err:ntdll:RtlpWaitForCriticalSection section 0x7b93a6c0 "syslevel.c: Win16Mutex" wait timed out in thread 001c, blocked by 001d, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7b93a6c0 "syslevel.c: Win16Mutex" wait timed out in thread 0019, blocked by 001d, retrying (60 sec)
err:syslevel:_LeaveSysLevel (0x7b93a6c0, level 1): Invalid state: count 0 mutex (nil).
err:syslevel:_LeaveSysLevel (0x7b93a6c0, level 1): Invalid state: count 0 mutex (nil).
err:syslevel:_LeaveSysLevel (0x7b93a6c0, level 1): Invalid state: count 0 mutex (nil).
```

---

