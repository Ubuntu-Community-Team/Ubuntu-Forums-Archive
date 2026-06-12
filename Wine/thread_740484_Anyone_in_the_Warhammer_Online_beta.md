---
title: "Anyone in the Warhammer Online beta?"
date: 2008-03-30
forum: Wine
---

### Post by mivo on 2008-03-30
The closed Warhammer Online beta has been running for some time. I'm curious if any of you are/were in it and if you tried to run it under Linux/Wine? :)

---

### Post by antzen on 2008-06-05
I'd like an answer to this as well. Not much info while googling it... My OS of choice is Ubuntu and I'm planning to kill my WoW account and go into WAR.. but I'm a bit hesitant since I don't know whether it'll run on my box or not..

---

### Post by ajackson on 2008-06-05
I tried to get in the closed beta but never heard anything back, hopefully they will have an open beta as well so linux users can try it out then.

---

### Post by pedro_orange on 2008-06-05
I heard on the grapevine this game will use directx10.....

---

### Post by MemoryDump on 2008-06-05
I put my name on the list for an invite.. never got one .. yet :(
anybody care to share? ;)

---

### Post by ajackson on 2008-06-05
> **pedro_orange said:**
> I heard on the grapevine this game will use directx10.....
No game manufacturer is dumb enough to go entirely directx10 as that would rule out XP users, there maybe directx10 enhancements like Lord of the Rings Online and Age of Conan are supposed to have. But there will be a directx9 version of Warhammer or it really will be the biggest flop in history.

---

### Post by MemoryDump on 2008-06-05
> **ajackson said:**
> No game manufacturer is dumb enough to go entirely directx10 as that would rule out XP users
MS might be.. :lolflag:

---

### Post by dpw2atox on 2008-06-06
I have a friend who is in WAR beta and he said he was able to launch WAR in Wine 1.0 RC3 without issues and log in as well. He said he had a few performance issues though and some other graphical issues where characters wouldn't display, etc. From what he said though it sounds promising.

---

### Post by Viter on 2008-06-20
I would like more answers too :)

---

### Post by soaro77 on 2008-08-20
> **ajackson said:**
> No game manufacturer is dumb enough to go entirely directx10 as that would rule out XP users, there maybe directx10 enhancements like Lord of the Rings Online and Age of Conan are supposed to have. But there will be a directx9 version of Warhammer or it really will be the biggest flop in history.

Ummm apparently this game manufacturer is that dumb then. I just downloaded the beta game and tried to run it under Wine and got a message that I need to download the newer version of DirectX from Microsoft. I run WoW under Wine perfectly and I believe it uses DirectX 9 so Warhammer must use DirectX 10.

Here is the exact message:

"Warhammer requires later DirectX components than are installed. Warhammer Installer will now exit.

Don't panic, you will be brought to Microsoft's Direct X page for a Web Install of the latest DirectX.
Please rerun the Warhammer Installer after DirectX Installation."

---

### Post by Muffinabus on 2008-08-20
It doesn't use DirectX 10 >_<

---

### Post by ajackson on 2008-08-20
> **soaro77 said:**
> Ummm apparently this game manufacturer is that dumb then. I just downloaded the beta game and tried to run it under Wine and got a message that I need to download the newer version of DirectX from Microsoft. I run WoW under Wine perfectly and I believe it uses DirectX 9 so Warhammer must use DirectX 10.
Well directx 10 is not available for XP and there are plenty of people using XP in the beta.

The problem is more likely to be that wine's version of directx 9 isn't up fully with the version this game needs (the last Microsoft release was June 2008 ).

---

### Post by fepple on 2008-08-30
It is DX9

It runs under Wine, and plays fine except for it doesnt draw Charcters/Mobs properly instead shows them as a pile on their side in the ground.  There is a bug with shadows that is common to other games but thats minor.

The patcher stopped working for some users.  Though we've only heard of this happening on ubuntu and are looking into why

The WineHQ page has more details on it:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13139&iTestingId=29100](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13139&iTestingId=29100)

---

### Post by SBFC on 2008-08-30
And if any of you actually want to be able to play the game in Wine I strongly recommend signing up at Wine's Bugzilla site and voting for the bug that prevents characters from rendering. There are over 30 votes and the game hasn't even come out yet.

Not only that, but considering the game runs fine aside from the character model issue speaks volumes about Wine's progress. 

[Bug #14608 <http://bugs.winehq.org/show_bug.cgi?id=14608>]("http://bugs.winehq.org/show_bug.cgi?id=14608")

I played during the closed beta and IMO it is a very fun game. Anxious for it to come out. Just a heads up that Destruction outnumbers Order by 1.5 to 2.

---

### Post by andyvy on 2008-09-04
Ran WAR last weekend for 3 day trial beta. Startup video is slugish, almost annoying, but after it passes the game runs fine. If they add an option to bypass video then I'll have zero issues.

I'll post some screenshots this Sunday when open beta starts.

(Didn't see any characters not displaying problems but I did experience slight terrain Clipping issues where the ground under me would turn black for a split second. In some areas it flickers like that but usually passes in seconds.)


WAAAAGH!!

---

### Post by FrozenFOXX on 2008-09-17
Anyone that's able to run it would you list what steps you used to get it to run?  Apparently I and many others running Ubuntu are having it hang on a PersistStorage error.

I'm running Kubuntu 8.04 64-bit, Wine 1.1.4, edited my patch.cfg to replace the FQDN with the IP, and it just hangs at PersistStorage_Init, will not display the window or anything.  Reportedly this is just happening with Ubuntu.

---

### Post by eggplant37 on 2008-09-17
> **FrozenFOXX said:**
> Anyone that's able to run it would you list what steps you used to get it to run?  Apparently I and many others running Ubuntu are having it hang on a PersistStorage error.

I'm running Kubuntu 8.04 64-bit, Wine 1.1.4, edited my patch.cfg to replace the FQDN with the IP, and it just hangs at PersistStorage_Init, will not display the window or anything.  Reportedly this is just happening with Ubuntu.

I got the final version by UPS today. It comes with 2 DVDs to install. I followed the instructions at [http://howto.landure.fr/gnu-linux/install-directx-9-0c-on-linux-using-wine](http://howto.landure.fr/gnu-linux/install-directx-9-0c-on-linux-using-wine) to get DirectX 10 installed after first installing 9.0c. I, too, am using Hardy 64-bit with all latest updates via update-manager installed and running wine 1.1.4.

The installer will run but appears to crap out with the following errors before opening up a dialog for the user to select which directory he'd like to install to:

```
eggplant@nheeghee:~$ wine /media/cdrom/setup.exe 
fixme:service:ChangeServiceConfig2W STUB: 0x110b80 2 0x33fe00
eggplant@nheeghee:~$ fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,14,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,28,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,42,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,56,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,70,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,85,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,99,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,113,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,127,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,141,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,155,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,170,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,184,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,198,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,212,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,226,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,240,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,255,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,255,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,233,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,212,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,191,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,170,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,148,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,127,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,106,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,85,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,63,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,42,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00ffffff,21,2): stub!
err:ole:CoGetClassObject class {03c036f1-a186-11d0-824a-00aa005b4383} not registered
err:ole:CoGetClassObject no class object {03c036f1-a186-11d0-824a-00aa005b4383} could be created for context 0x1
wine: Unhandled page fault on read access to 0x00000000 at address 0x2ad70cb (thread 0027), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x02ad70cb).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:02ad70cb ESP:0033d548 EBP:0033d5d0 EFLAGS:00010282(   - 00      - RIS1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:00000071
 ESI:0033e3fc EDI:0033e31c
Stack dump:
0x0033d548:  88fbac09 0033d5a0 0033e3fc 0033d5d0
0x0033d558:  0033e31c 00000000 00000000 0033d5c4
0x0033d568:  02b2ce75 ffffffff 0033d5c4 02b28568
0x0033d578:  00000000 02ada33d 88fbac95 00010056
0x0033d588:  00000000 7ee1c64c 00000000 3f800000
0x0033d598:  00000000 3f800000 00000000 3f800000
Backtrace:
=>1 0x02ad70cb in nsisdirselect (+0x170cb) (0x0033d5d0)
  2 0x02afb95f in nsisdirselect (+0x3b95f) (0x0033d604)
  3 0x7edfabb8 in user32 (+0xaabb8) (0x0033d644)
  4 0x7edfe133 in user32 (+0xae133) (0x0033d684)
  5 0x7ed857d7 DefDlgProcA+0x87() in user32 (0x0033d6b4)
  6 0x7edf8dba WINPROC_wrapper+0x1a() in user32 (0x0033d6e4)
  7 0x7edf949e WINPROC_wrapper+0x6fe() in user32 (0x0033d724)
  8 0x7edfe262 CallWindowProcA+0x52() in user32 (0x0033d764)
  9 0x02afded8 in nsisdirselect (+0x3ded8) (0x0033d784)
  10 0x02affa7e in nsisdirselect (+0x3fa7e) (0x0033d840)
  11 0x02afdfd1 in nsisdirselect (+0x3dfd1) (0x0033d860)
  12 0x02b001a1 in nsisdirselect (+0x401a1) (0x0033d8c8)
  13 0x02b0022e in nsisdirselect (+0x4022e) (0x0033d8e8)
  14 0x7edf8dba WINPROC_wrapper+0x1a() in user32 (0x0033d918)
  15 0x7edf949e WINPROC_wrapper+0x6fe() in user32 (0x0033d958)
  16 0x7edfeca5 in user32 (+0xaeca5) (0x0033de28)
  17 0x7edff89a in user32 (+0xaf89a) (0x0033de68)
  18 0x7edc0d71 in user32 (+0x70d71) (0x0033dec8)
  19 0x7edc402d in user32 (+0x7402d) (0x0033df28)
  20 0x7edc449a SendMessageW+0x4a() in user32 (0x0033df68)
  21 0x7ed8afec in user32 (+0x3afec) (0x0033e138)
  22 0x7ed8c216 CreateDialogIndirectParamAorW+0x36() in user32 (0x0033e158)
  23 0x7ed8c341 CreateDialogIndirectParamA+0x41() in user32 (0x0033e188)
  24 0x02afc041 in nsisdirselect (+0x3c041) (0x0033e1fc)
  25 0x02afc2d5 in nsisdirselect (+0x3c2d5) (0x0033e2c4)
  26 0x02acf5c4 in nsisdirselect (+0xf5c4) (0x00000010)
  27 0x00000000 (0x00000000)
0x02ad70cb: movl	0x0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (112 modules)
PE	  400000-  444000	Deferred        setup
PE	 2ac0000- 2b6f000	Export          nsisdirselect
PE	10000000-10006000	Deferred        system
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7db89000-7dbab000	Deferred        mpr<elf>
  \-PE	7db90000-7dbab000	\               mpr
ELF	7dbab000-7dbfa000	Deferred        wininet<elf>
  \-PE	7dbb0000-7dbfa000	\               wininet
ELF	7dbfa000-7dc39000	Deferred        urlmon<elf>
  \-PE	7dc00000-7dc39000	\               urlmon
ELF	7dc39000-7dc6d000	Deferred        libxslt.so.1
ELF	7dc6d000-7dd8c000	Deferred        libxml2.so.2
ELF	7dd8c000-7de5e000	Deferred        oleaut32<elf>
  \-PE	7dda0000-7de5e000	\               oleaut32
ELF	7de5e000-7de62000	Deferred        libgpg-error.so.0
ELF	7de62000-7deaf000	Deferred        libgcrypt.so.11
ELF	7deaf000-7debf000	Deferred        libtasn1.so.3
ELF	7debf000-7dec7000	Deferred        libkrb5support.so.0
ELF	7dec7000-7def9000	Deferred        libcrypt.so.1
ELF	7def9000-7df6e000	Deferred        libgnutls.so.13
ELF	7df6e000-7df91000	Deferred        libk5crypto.so.3
ELF	7df91000-7e01e000	Deferred        libkrb5.so.3
ELF	7e01e000-7e047000	Deferred        libgssapi_krb5.so.2
ELF	7e047000-7e07a000	Deferred        libcups.so.2
ELF	7e0a5000-7e0f1000	Deferred        msxml3<elf>
  \-PE	7e0b0000-7e0f1000	\               msxml3
ELF	7e0f1000-7e126000	Deferred        winspool<elf>
  \-PE	7e100000-7e126000	\               winspool
ELF	7e126000-7e131000	Deferred        libgcc_s.so.1
ELF	7e245000-7e248000	Deferred        libkeyutils.so.1
ELF	7e248000-7e25b000	Deferred        msimg32<elf>
  \-PE	7e250000-7e25b000	\               msimg32
ELF	7e26d000-7e281000	Deferred        userenv<elf>
  \-PE	7e270000-7e281000	\               userenv
ELF	7e281000-7e295000	Deferred        oleacc<elf>
  \-PE	7e290000-7e295000	\               oleacc
ELF	7e295000-7e2eb000	Deferred        riched20<elf>
  \-PE	7e2a0000-7e2eb000	\               riched20
ELF	7e2eb000-7e2ff000	Deferred        midimap<elf>
  \-PE	7e2f0000-7e2ff000	\               midimap
ELF	7e2ff000-7e326000	Deferred        msacm32<elf>
  \-PE	7e310000-7e326000	\               msacm32
ELF	7e326000-7e3e9000	Deferred        libasound.so.2
ELF	7e3ea000-7e401000	Deferred        msacm32<elf>
  \-PE	7e3f0000-7e401000	\               msacm32
ELF	7e401000-7e436000	Deferred        winealsa<elf>
  \-PE	7e410000-7e436000	\               winealsa
ELF	7e436000-7e4c8000	Deferred        winmm<elf>
  \-PE	7e440000-7e4c8000	\               winmm
ELF	7e4c8000-7e4db000	Deferred        shfolder<elf>
  \-PE	7e4d0000-7e4db000	\               shfolder
ELF	7e509000-7e50c000	Deferred        libcom_err.so.2
ELF	7e51f000-7e552000	Deferred        uxtheme<elf>
  \-PE	7e530000-7e552000	\               uxtheme
ELF	7e552000-7e55b000	Deferred        libxcursor.so.1
ELF	7e55b000-7e560000	Deferred        libxfixes.so.3
ELF	7e560000-7e563000	Deferred        libxcomposite.so.1
ELF	7e563000-7e569000	Deferred        libxrandr.so.2
ELF	7e569000-7e571000	Deferred        libxrender.so.1
ELF	7e571000-7e576000	Deferred        libxxf86vm.so.1
ELF	7e576000-7e579000	Deferred        libxinerama.so.1
ELF	7e579000-7e599000	Deferred        imm32<elf>
  \-PE	7e580000-7e599000	\               imm32
ELF	7e599000-7e59e000	Deferred        libxdmcp.so.6
ELF	7e59e000-7e5b6000	Deferred        libxcb.so.1
ELF	7e5b6000-7e5b8000	Deferred        libxcb-xlib.so.0
ELF	7e5b8000-7e69f000	Deferred        libx11.so.6
ELF	7e69f000-7e6ad000	Deferred        libxext.so.6
ELF	7e6c5000-7e75d000	Deferred        winex11<elf>
  \-PE	7e6d0000-7e75d000	\               winex11
ELF	7e780000-7e7a1000	Deferred        libexpat.so.1
ELF	7e7a1000-7e7cb000	Deferred        libfontconfig.so.1
ELF	7e7cb000-7e7e0000	Deferred        libz.so.1
ELF	7e7e0000-7e850000	Deferred        libfreetype.so.6
ELF	7e850000-7e853000	Deferred        libxau.so.6
ELF	7e868000-7e881000	Deferred        version<elf>
  \-PE	7e870000-7e881000	\               version
ELF	7e881000-7e894000	Deferred        libresolv.so.2
ELF	7e894000-7e8b3000	Deferred        iphlpapi<elf>
  \-PE	7e8a0000-7e8b3000	\               iphlpapi
ELF	7e8b3000-7e917000	Deferred        rpcrt4<elf>
  \-PE	7e8c0000-7e917000	\               rpcrt4
ELF	7e917000-7ea09000	Deferred        ole32<elf>
  \-PE	7e930000-7ea09000	\               ole32
ELF	7ea09000-7eaca000	Deferred        comctl32<elf>
  \-PE	7ea10000-7eaca000	\               comctl32
ELF	7eaca000-7eb24000	Deferred        shlwapi<elf>
  \-PE	7eae0000-7eb24000	\               shlwapi
ELF	7eb24000-7ec3e000	Deferred        shell32<elf>
  \-PE	7eb30000-7ec3e000	\               shell32
ELF	7ec3e000-7ec90000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec90000	\               advapi32
ELF	7ec90000-7ed2e000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed2e000	\               gdi32
ELF	7ed2e000-7ee77000	Export          user32<elf>
  \-PE	7ed50000-7ee77000	\               user32
ELF	7ee77000-7ee82000	Deferred        libnss_files.so.2
ELF	7ee82000-7ee8b000	Deferred        libnss_compat.so.2
ELF	7ee8f000-7eea3000	Deferred        lz32<elf>
  \-PE	7ee90000-7eea3000	\               lz32
ELF	7efc3000-7efe8000	Deferred        libm.so.6
ELF	7efe8000-7f000000	Deferred        libnsl.so.1
ELF	f7cf6000-f7cfa000	Deferred        libdl.so.2
ELF	f7cfa000-f7e49000	Deferred        libc.so.6
ELF	f7e4a000-f7e62000	Deferred        libpthread.so.0
ELF	f7e66000-f7e70000	Deferred        libnss_nis.so.2
ELF	f7e7a000-f7fb0000	Deferred        libwine.so.1
ELF	f7fb2000-f7fd1000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	0000001b    0
	00000015    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000014    0
	00000011    0
	00000010    0
00000018 
	0000001d    0
	0000001c    0
	0000001a    0
	00000019    0
00000024 
	00000025    0
00000026 (D) C:\windows\temp\setup.exe
	00000029   15
	00000027    0 <==
Backtrace:
=>1 0x02ad70cb in nsisdirselect (+0x170cb) (0x0033d5d0)
  2 0x02afb95f in nsisdirselect (+0x3b95f) (0x0033d604)
  3 0x7edfabb8 in user32 (+0xaabb8) (0x0033d644)
  4 0x7edfe133 in user32 (+0xae133) (0x0033d684)
  5 0x7ed857d7 DefDlgProcA+0x87() in user32 (0x0033d6b4)
  6 0x7edf8dba WINPROC_wrapper+0x1a() in user32 (0x0033d6e4)
  7 0x7edf949e WINPROC_wrapper+0x6fe() in user32 (0x0033d724)
  8 0x7edfe262 CallWindowProcA+0x52() in user32 (0x0033d764)
  9 0x02afded8 in nsisdirselect (+0x3ded8) (0x0033d784)
  10 0x02affa7e in nsisdirselect (+0x3fa7e) (0x0033d840)
  11 0x02afdfd1 in nsisdirselect (+0x3dfd1) (0x0033d860)
  12 0x02b001a1 in nsisdirselect (+0x401a1) (0x0033d8c8)
  13 0x02b0022e in nsisdirselect (+0x4022e) (0x0033d8e8)
  14 0x7edf8dba WINPROC_wrapper+0x1a() in user32 (0x0033d918)
  15 0x7edf949e WINPROC_wrapper+0x6fe() in user32 (0x0033d958)
  16 0x7edfeca5 in user32 (+0xaeca5) (0x0033de28)
  17 0x7edff89a in user32 (+0xaf89a) (0x0033de68)
  18 0x7edc0d71 in user32 (+0x70d71) (0x0033dec8)
  19 0x7edc402d in user32 (+0x7402d) (0x0033df28)
  20 0x7edc449a SendMessageW+0x4a() in user32 (0x0033df68)
  21 0x7ed8afec in user32 (+0x3afec) (0x0033e138)
  22 0x7ed8c216 CreateDialogIndirectParamAorW+0x36() in user32 (0x0033e158)
  23 0x7ed8c341 CreateDialogIndirectParamA+0x41() in user32 (0x0033e188)
  24 0x02afc041 in nsisdirselect (+0x3c041) (0x0033e1fc)
  25 0x02afc2d5 in nsisdirselect (+0x3c2d5) (0x0033e2c4)
  26 0x02acf5c4 in nsisdirselect (+0xf5c4) (0x00000010)
  27 0x00000000 (0x00000000)
```


I have no idea what the problem could be.

---

### Post by oedipuss on 2008-09-17
> Anyone that's able to run it would you list what steps you used to get it to run? Apparently I and many others running Ubuntu are having it hang on a PersistStorage error.
Same here. Nothing could make it get past that, except closing wine's virtual desktop, at which point the patcher appears (with some easily bypassed errors). It's no solution, however, it will terminate after 20 seconds, since I suspect wine thinks it's an unresponsive app that didn't shut down when you told it to. 
I think the PersistStorage message is unrelated and just happens to be the last thing displayed.

---

### Post by FrozenFOXX on 2008-09-17
From what we can tell, the PersistStorage error has to do with the HTTP request for the patcher.  You HAVE to run the game from the patcher, either .exe or .bin we don't know yet since people seem to have success with either depending on their setups.

I can get to the patcher login but unfortunately no matter how fast I am with entering my info it tanks without message.  As a special note, apparently you shouldn't need to run the Setup.exe since all it does is create shortcuts, the warpatcher.exe/bin does everything else you need.

Still attempting to get it to run, considering winetricks but I don't want to completely bork something.

---

### Post by oedipuss on 2008-09-18
> **FrozenFOXX said:**
> 
Still attempting to get it to run, considering winetricks but I don't want to completely bork something.

Just create another wine prefix with wineprefixcreate -p /wherever/winewar
and install directx or whatever in it. I think you have to edit the winetricks script to alter its wineprefix, but it's easy to find. 
You can run anything from that prefix by exporting WINEPREFIX=/wherever/winewar, or just by typing "WINEPREFIX=/wherever/winewar wine myprog.exe" .

I tried changing the server address to its IP in patch.cfg , but the patcher still didn't start normally, and when it did (by closing the window) it couldn't connect at all. 

PS: check out the manpages for wineprefixcreate and WINEPREFIX just to be sure you know what you're doing .. I don't think there's a way to uninstall directx or other non-recommended components in case you install them in the wrong prefix.

---

### Post by FrozenFOXX on 2008-09-19
> **oedipuss said:**
> Just create another wine prefix with wineprefixcreate -p /wherever/winewar
and install directx or whatever in it. I think you have to edit the winetricks script to alter its wineprefix, but it's easy to find. 
You can run anything from that prefix by exporting WINEPREFIX=/wherever/winewar, or just by typing "WINEPREFIX=/wherever/winewar wine myprog.exe" .

I tried changing the server address to its IP in patch.cfg , but the patcher still didn't start normally, and when it did (by closing the window) it couldn't connect at all. 

PS: check out the manpages for wineprefixcreate and WINEPREFIX just to be sure you know what you're doing .. I don't think there's a way to uninstall directx or other non-recommended components in case you install them in the wrong prefix.

Tried it, used winetricks to install directx 9.0c and gecko, still no worky.  Absolutely zero change.  :(

Mikee on the appdb page recommends recompiling wine with this guide:  [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit).  Unfortunately there's no knowing if that'll work yet as he's the only one who got it to work that way.

Wouldn't mind getting CrossOver Games for this but unfortunately it doesn't look like that does it either.

---

### Post by oedipuss on 2008-09-20
Yeah I know, I meant that as a way to safely try things with wine, without messing up your original .wine dir. 

Just tried compiling wine 1.1.5, doesn't work either, same stuff.

---

### Post by Maelgwyn on 2008-09-24
I haven't been able to get Warhammer Online to run *at all* in WINE -_-'
When I get home I'll edit this post and stick in the command-line garble in the vain hope somebody can understand it!

---

### Post by buntunub on 2008-09-26
> Getting Game to run.
by Mikee on Sunday July 27th 2008, 10:43
Copy winhttp.dll to the system32 directory.
wine warpatch.exe

Seems this hack gets the game running...

---

### Post by Maelgwyn on 2008-09-27
> **buntunub said:**
> Seems this hack gets the game running...

Awesome thanks for that, I'll give it a go!

---

### Post by Maelgwyn on 2008-09-27
err, where do I find winhttp.dll? :P

*edit* found it!

However it still doesn't run :(
```
nik@taonga:~/.wine/drive_c/Program Files/Warhammer Online$ wine warpatch.exe 
fixme:shdocvw:PersistStorage_InitNew (0x135e18)->(0xd953d0)
nik@taonga:~/.wine/drive_c/Program Files/Warhammer Online$
```

It just hangs on that fixme: for a little while, then nothing further happens and it goes back to command prompt =/

---

### Post by king0929 on 2008-09-28
We strive to provide cheapest gold and professional powerleveling service for MMORPG like WARHAMMER.We have done in this industry for long, and have built its reputation on competitive price,speedy delivery and reliable customer service.Register now as our member you may enjoy the discount for purchasing all our productions. 
 For example 40 Gold(warhammer Online EU): Market price:$46.97 Preferential price:$32.03Membership Price: $31.38  Package for Powerleveling 1-20 ( 2 days ): Market Price:$ 47.25 Member Price:$ 46.31.Any question please contact our 24/7 online Live support. Of course, you can also contact us by telephone or email .Our email is [email]agamegold@gmail.com[/email],and our phone number is 1-703-879-8815.We will try our best to serve you, If you want to know further ,please go to [www.agamegold.com](www.agamegold.com) or [www.wow4s.com](www.wow4s.com). 
We are waiting for you!
Do not hesitate!

---

