---
title: "Darkfall on Wine"
date: 2013-04-11
forum: Wine
---

### Post by fernetekhd on 2013-04-11
So I can't get Darkfall: Unholy Wars to run on Wine. Although I am able to accomplish the initial install of the client, after that I hit a brick wall.

As soon as I launch the client with Wine I am informed that Wine has crashed, and get this crash log: 

```
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x7e16381a).Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e16381a ESP:00bedd60 EBP:7e19cfb8 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:00beddbc EBX:7e1bbff4 ECX:7e19cfb8 EDX:00beddac
 ESI:00beddbc EDI:0000000a
Stack dump:
0x00bedd60:  00beddac 00beddbc 7e164bcd 7e19cfb8
0x00bedd70:  459e2c08 7e164d29 7e1bbff4 00beddac
0x00bedd80:  00beddbc 7e1bbff4 7e165224 00beddbc
0x00bedd90:  00beddac 7e19cfb8 f0b1f237 a007c8d5
0x00bedda0:  aebcdcd5 2c4f3308 1bcad437 498e8ae1
0x00beddb0:  00000080 00beded8 7e1921f8 ebeae9e8
Backtrace:
=>0 0x7e16381a in libgcrypt.so.11 (+0x2981a) (0x7e19cfb8)
  1 0x7e164bcd in libgcrypt.so.11 (+0x2abcc) (0x7e19cfb8)
  2 0x7e165224 in libgcrypt.so.11 (+0x2b223) (0x7e19cfb8)
  3 0x7e164d7f in libgcrypt.so.11 (+0x2ad7e) (0x00000000)
  4 0x7e1493f7 in libgcrypt.so.11 (+0xf3f6) (0x7e281584)
  5 0x7e13f7c4 gcry_cipher_setkey+0x43() in libgcrypt.so.11 (0x7e281584)
  6 0x7e25c6cb in libgnutls.so.26 (+0x9e6ca) (0x7e281584)
  7 0x7e1de8f9 in libgnutls.so.26 (+0x208f8) (0x7e281584)
  8 0x7e1e9cf8 in libgnutls.so.26 (+0x2bcf7) (0x7bd01be8)
  9 0x7e1ea2b1 in libgnutls.so.26 (+0x2c2b0) (0x00000010)
  10 0x7e1ea9f7 in libgnutls.so.26 (+0x2c9f6) (0x7bd0124c)
  11 0x7e1d31ed in libgnutls.so.26 (+0x151ec) (0x00bee2a4)
  12 0x7e1d65f0 in libgnutls.so.26 (+0x185ef) (0x00bee2a4)
  13 0x7e1d800d gnutls_handshake+0x5c() in libgnutls.so.26 (0x00bee2a4)
  14 0x7d01d233 in secur32 (+0xd232) (0x00bee2a4)
  15 0x7d01ae44 in secur32 (+0xae43) (0x00bee354)
  16 0x7d01bbae in secur32 (+0xbbad) (0x00bee3c4)
  17 0x7d022a3d InitializeSecurityContextA+0x18c() in secur32 (0x00bee444)
0x7e16381a: movq	0x0(%esi),%mm1
Modules:
Module	Address			Debug info	Name (159 modules)
PE	  400000-  8cc000	Export          dfuwlobby
PE	61700000-61777000	Deferred        mozsqlite3
PE	61e40000-61e4c000	Deferred        mozalloc
PE	622c0000-622cd000	Deferred        plds4
PE	62e40000-62e67000	Deferred        smime3
PE	64f40000-64f75000	Deferred        nspr4
PE	68400000-684ea000	Deferred        nss3
PE	68780000-6879a000	Deferred        nssutil3
PE	69c40000-6b009000	Deferred        xul
PE	6c800000-6c832000	Deferred        ssl3
PE	6ce40000-6ce4d000	Deferred        plc4
PE	70180000-704b9000	Deferred        mozjs
ELF	7b800000-7ba29000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba29000	\               kernel32
ELF	7bc00000-7bcc3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c6e1000-7c6ff000	Deferred        libgcc_s.so.1
ELF	7ced5000-7cf00000	Deferred        netapi32<elf>
  \-PE	7cee0000-7cf00000	\               netapi32
ELF	7d000000-7d02c000	Dwarf           secur32<elf>
  \-PE	7d010000-7d02c000	\               secur32
ELF	7d02c000-7d084000	Deferred        riched20<elf>
  \-PE	7d040000-7d084000	\               riched20
ELF	7d084000-7d100000	Deferred        jscript<elf>
  \-PE	7d090000-7d100000	\               jscript
ELF	7d200000-7d215000	Deferred        schannel<elf>
  \-PE	7d210000-7d215000	\               schannel
ELF	7d215000-7d21c000	Deferred        libnss_dns.so.2
ELF	7d21c000-7d231000	Deferred        t2embed<elf>
  \-PE	7d220000-7d231000	\               t2embed
ELF	7d231000-7d24a000	Deferred        msftedit<elf>
  \-PE	7d240000-7d24a000	\               msftedit
ELF	7d24a000-7d283000	Deferred        usp10<elf>
  \-PE	7d250000-7d283000	\               usp10
ELF	7d283000-7d297000	Deferred        msimg32<elf>
  \-PE	7d290000-7d297000	\               msimg32
ELF	7d297000-7d2f5000	Deferred        dbghelp<elf>
  \-PE	7d2a0000-7d2f5000	\               dbghelp
ELF	7d2f5000-7d382000	Deferred        msvcrt<elf>
  \-PE	7d310000-7d382000	\               msvcrt
ELF	7d382000-7d478000	Deferred        mshtml<elf>
  \-PE	7d390000-7d478000	\               mshtml
ELF	7d478000-7d49e000	Deferred        mpr<elf>
  \-PE	7d480000-7d49e000	\               mpr
ELF	7d49e000-7d50d000	Deferred        wininet<elf>
  \-PE	7d4b0000-7d50d000	\               wininet
ELF	7d50d000-7d591000	Deferred        urlmon<elf>
  \-PE	7d520000-7d591000	\               urlmon
ELF	7d5ee000-7d5f2000	Deferred        libnss_mdns4_minimal.so.2
ELF	7d5f2000-7d606000	Deferred        psapi<elf>
  \-PE	7d600000-7d606000	\               psapi
ELF	7d606000-7d669000	Deferred        ieframe<elf>
  \-PE	7d610000-7d669000	\               ieframe
ELF	7d6ad000-7d6c0000	Deferred        gnome-keyring-pkcs11.so
ELF	7d6c0000-7d70a000	Deferred        libdbus-1.so.3
ELF	7d70a000-7d713000	Deferred        libkrb5support.so.0
ELF	7d713000-7d73b000	Deferred        libk5crypto.so.3
ELF	7d73b000-7d809000	Deferred        libkrb5.so.3
ELF	7d809000-7d81b000	Deferred        libavahi-client.so.3
ELF	7d81b000-7d829000	Deferred        libavahi-common.so.3
ELF	7d829000-7d866000	Deferred        libgssapi_krb5.so.2
ELF	7d866000-7d8c5000	Deferred        libcups.so.2
ELF	7d905000-7d939000	Deferred        uxtheme<elf>
  \-PE	7d910000-7d939000	\               uxtheme
ELF	7d939000-7d940000	Deferred        libxfixes.so.3
ELF	7d940000-7d94b000	Deferred        libxcursor.so.1
ELF	7d952000-7d95b000	Deferred        librt.so.1
ELF	7d9d5000-7d9fd000	Deferred        libexpat.so.1
ELF	7d9fd000-7da35000	Deferred        libfontconfig.so.1
ELF	7da35000-7da45000	Deferred        libxi.so.6
ELF	7da45000-7da49000	Deferred        libxcomposite.so.1
ELF	7da49000-7da54000	Deferred        libxrandr.so.2
ELF	7da54000-7da5e000	Deferred        libxrender.so.1
ELF	7da5e000-7da64000	Deferred        libxxf86vm.so.1
ELF	7da64000-7da86000	Deferred        imm32<elf>
  \-PE	7da70000-7da86000	\               imm32
ELF	7da86000-7daa8000	Deferred        libxcb.so.1
ELF	7daa8000-7daae000	Deferred        libuuid.so.1
ELF	7daae000-7dac8000	Deferred        libice.so.6
ELF	7dac8000-7dbfe000	Deferred        libx11.so.6
ELF	7dbfe000-7dc10000	Deferred        libxext.so.6
ELF	7dc10000-7dc19000	Deferred        libsm.so.6
ELF	7dc1c000-7dc20000	Deferred        libkeyutils.so.1
ELF	7dc2b000-7dcbf000	Deferred        winex11<elf>
  \-PE	7dc40000-7dcbf000	\               winex11
ELF	7dcbf000-7dd59000	Deferred        libfreetype.so.6
ELF	7dd59000-7dd81000	Deferred        msacm32<elf>
  \-PE	7dd60000-7dd81000	\               msacm32
ELF	7dd81000-7de2e000	Deferred        winmm<elf>
  \-PE	7dd90000-7de2e000	\               winmm
ELF	7de2e000-7de5f000	Deferred        libcrypt.so.1
ELF	7de5f000-7df0d000	Deferred        libsqlite3.so.0
ELF	7df0d000-7df52000	Deferred        libhx509.so.5
ELF	7df52000-7df61000	Deferred        libheimbase.so.1
ELF	7df61000-7df8a000	Deferred        libwind.so.0
ELF	7df8a000-7df9e000	Deferred        libp11-kit.so.0
ELF	7df9e000-7dfb7000	Deferred        libz.so.1
ELF	7dfb7000-7dfc9000	Deferred        libtasn1.so.3
ELF	7dfc9000-7dfde000	Deferred        libroken.so.18
ELF	7dfde000-7e012000	Deferred        libhcrypto.so.4
ELF	7e012000-7e0b1000	Deferred        libasn1.so.8
ELF	7e0b1000-7e132000	Deferred        libkrb5.so.26
ELF	7e132000-7e13a000	Deferred        libheimntlm.so.0
ELF	7e13a000-7e1be000	Dwarf           libgcrypt.so.11
ELF	7e1be000-7e282000	Dwarf           libgnutls.so.26
ELF	7e282000-7e2be000	Deferred        libgssapi.so.3
ELF	7e2be000-7e2d9000	Deferred        libsasl2.so.2
ELF	7e2d9000-7e2f0000	Deferred        libresolv.so.2
ELF	7e2f0000-7e2ff000	Deferred        liblber-2.4.so.2
ELF	7e2ff000-7e350000	Deferred        libldap_r-2.4.so.2
ELF	7e350000-7e3ad000	Deferred        wldap32<elf>
  \-PE	7e360000-7e3ad000	\               wldap32
ELF	7e3ad000-7e3cf000	Deferred        iphlpapi<elf>
  \-PE	7e3b0000-7e3cf000	\               iphlpapi
ELF	7e3cf000-7e401000	Deferred        ws2_32<elf>
  \-PE	7e3e0000-7e401000	\               ws2_32
ELF	7e401000-7e41c000	Deferred        wsock32<elf>
  \-PE	7e410000-7e41c000	\               wsock32
ELF	7e41c000-7e50e000	Deferred        oleaut32<elf>
  \-PE	7e430000-7e50e000	\               oleaut32
ELF	7e50e000-7e584000	Deferred        rpcrt4<elf>
  \-PE	7e520000-7e584000	\               rpcrt4
ELF	7e584000-7e68b000	Deferred        ole32<elf>
  \-PE	7e5a0000-7e68b000	\               ole32
ELF	7e68b000-7e6c5000	Deferred        winspool<elf>
  \-PE	7e690000-7e6c5000	\               winspool
ELF	7e6c5000-7e7be000	Deferred        comctl32<elf>
  \-PE	7e6d0000-7e7be000	\               comctl32
ELF	7e7be000-7e828000	Deferred        shlwapi<elf>
  \-PE	7e7d0000-7e828000	\               shlwapi
ELF	7e828000-7ea3b000	Deferred        shell32<elf>
  \-PE	7e830000-7ea3b000	\               shell32
ELF	7ea3b000-7eb1a000	Deferred        comdlg32<elf>
  \-PE	7ea40000-7eb1a000	\               comdlg32
ELF	7eb1a000-7eb33000	Deferred        version<elf>
  \-PE	7eb20000-7eb33000	\               version
ELF	7eb33000-7eb95000	Deferred        advapi32<elf>
  \-PE	7eb40000-7eb95000	\               advapi32
ELF	7eb95000-7ec52000	Deferred        gdi32<elf>
  \-PE	7eba0000-7ec52000	\               gdi32
ELF	7ec52000-7ed92000	Deferred        user32<elf>
  \-PE	7ec60000-7ed92000	\               user32
ELF	7ed92000-7ed9f000	Deferred        libnss_files.so.2
ELF	7ed9f000-7edb9000	Deferred        libnsl.so.1
ELF	7edb9000-7edc2000	Deferred        libnss_compat.so.2
ELF	7efc2000-7efee000	Deferred        libm.so.6
ELF	7efee000-7eff2000	Deferred        libxinerama.so.1
ELF	7eff2000-7eff9000	Deferred        libxdmcp.so.6
ELF	b7492000-b7496000	Deferred        libxau.so.6
ELF	b7496000-b749b000	Deferred        libgpg-error.so.0
ELF	b749c000-b74a1000	Deferred        libdl.so.2
ELF	b74a1000-b764b000	Deferred        libc.so.6
ELF	b764c000-b7667000	Deferred        libpthread.so.0
ELF	b7667000-b766c000	Deferred        libcom_err.so.2
ELF	b766c000-b7678000	Deferred        libnss_nis.so.2
ELF	b7679000-b77bb000	Dwarf           libwine.so.1
ELF	b77bd000-b77df000	Deferred        ld-linux.so.2
ELF	b77df000-b77e0000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000032    0
	00000031    0
	0000001e    0
	00000018    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000019    0
	00000014    0
	00000013    0
0000001a plugplay.exe
	00000020    0
	0000001d    0
	0000001b    0
00000021 explorer.exe
	00000022    0
00000023 (D) C:\Program Files\Darkfall Unholy Wars\DFUWLobby.exe
	00000047    0
	00000046    0
	00000045    0
	00000044    0
	00000043    0
	00000042    0
	00000041    0
	00000040    0
	0000003f    0
	0000003e    0
	0000003d    0
	0000003c    0
	0000003b    0
	0000003a    0
	00000039    0
	00000038    0
	00000037    0
	00000036    0
	00000035    0
	00000033    0
	00000030    0
	0000002f    0
	0000002e    0
	0000002d    0
	0000002c    0
	0000002b    0
	0000002a    0
	00000029    0
	00000028    0
	00000027    0
	00000026    0
	00000025    0 <==
	00000024    0
System information:
    Wine build: wine-1.4.1
    Platform: i386
    Host system: Linux
    Host version: 3.5.0-27-generic

```

Sorry about the wall of text but I don't see a spoiler option for the editor.

So, any ideas on what I should do?

---

### Post by Mark Phelps on 2013-04-11
How are you able to run this NOW when it's not even going to be released until the 16th??

---

### Post by fernetekhd on 2013-04-11
...I bought into the beta?

And I'm pretty sure the beta servers are still running.

---

### Post by Mark Phelps on 2013-04-12
Don't know what version you're running -- but the results for the latest version tested with Wine are discouraging:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=9313]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=9313")

---

### Post by fernetekhd on 2013-04-12
A) That's Darkfall 1, different game.

B) That's not really helping.

---

### Post by fernetekhd on 2013-04-22
Still need help with this.

---

### Post by fernetekhd on 2013-04-27
Ok...last bump.

---

### Post by myromance123 on 2013-04-27
Have you tried installing it in PlayOnLinux? This would give you the freedom to try multiple Wine versions with ease. When it comes to Wine gaming, you really have to go through Trial and Error, and see which Wine release does it for you.

The latest Wine is 1.5.28, I'd honestly suggest using that. From that output you gave, it would seem you're using Wine 1.4.1 which is stable but old. Also, have you tried using Winetricks to install DirectX9 into it?

---

### Post by fernetekhd on 2013-04-27
Hadn't even thought of that!

So I'm able to launch the client and everything now; however, now I get an error saying "Error establishing SSL session".

Edit: Should clarify that I mean that the client launches without crashing, but I'm unable to connect to the patching servers as that error appears.

Edit 2: The news stream doesn't appear either. Do I need to open a port for Wine or something?

Edit 3: Here's the debug log from PoL

```
[POL_Wine_SetVersionEnv] Message: Setting wine version path: 1.5.28, x86[POL_Wine_SetVersionEnv] Message: "/home/rob/.PlayOnLinux//wine/linux-x86/1.5.28" exists
[POL_Wine] Message: Running wine-1.5.28 DFUWLobby.exe
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:system:SetProcessDPIAware stub!
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
[POL_Wine] Message: Wine return: 0
```

---

### Post by myromance123 on 2013-04-27
> Error establishing SSL session
Could the servers be down? Since you mentioned it's still in Beta. To clarify though, I've never had to open a port just for Wine. When opening ports, you do it for the game itself. Does Darkfall: Unholy Wars require any ports to be forwarded? If so, then you should forward those in your router.

This may or may not help at all, but back when I was playing Guild Wars 2 in POL, I needed to pass -dx9single in the Arguments section of POL to get the launcher working right. To pass an argument to POL, just click the Configure button and under the General tab there will be an input box labelled arguments. Sorry if this doesn't help you, since I don't have the game myself I can't really stress test it against everything.

---

### Post by fernetekhd on 2013-04-27
Actually it launched since I started this thread and as far as I know the servers should be up.

Looking at the output, it mentions that it can't find winemenubuilder.exe; is this part of a package I need to install? A quick google search reaped me no answers.

Does fixme in the log mean an error? Or what is it? And what is that error about threads talking about; could it have something to do with my CPU (logic threads = processor, right?).

I know I won't be able to get any in-depth help here (though I've gotten more here in an hour than I have in several weeks on the Darkfall forums -_-), but I do appreciate your input.

EDIT: Also I don't even see an argument section, and I remember having to use it as well for GW2.

---

### Post by myromance123 on 2013-04-27
The fixmes are debug output for the Wine developers to work on in the future (at least that's what I understand). 

In PlayOnLinux, you can install Microsoft Visual C++ Redistributables by going into Configure and then into the Install Components tab. I see that the old Darkfall required MSVC 2008, so it's possible this new Darkfall might need MSVC 2008 or 2010. Can you try installing those? They can be found in the Install Components tab.

Are you on Ubuntu 12.04? This might fix your issue with the winemenubuilder.exe. Run this in a Terminal:
```
echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
```

I remember there was some issues in 12.04 and Wine, and the developers over at CrossOver helped me fix it by using this command. Try the MSVC installs first, if that doesn't work, then try this terminal command.

---

### Post by fernetekhd on 2013-04-27
Ok, so I installed msvc100, 80 and 90 (in that order, attempted a run after every install), but they reaped nothing. Those are the right downloads, right?

Using that code outputted a 0 in the terminal and did nothing for the client.

Yes, I am using Ubuntu 12.04

---

### Post by myromance123 on 2013-04-28
> **fernetekhd said:**
> Ok, so I installed msvc100, 80 and 90 (in that order, attempted a run after every install), but they reaped nothing. Those are the right downloads, right?

Using that code outputted a 0 in the terminal and did nothing for the client.

Yes, I am using Ubuntu 12.04

Yep, those are the ones. I'm at a dead end for things to try. Could Darkfall require .NET 4.0?

> EDIT: Also I don't even see an argument section, and I remember having to use it as well for GW2. 
Then you need the latest PlayOnLinux. The latest right now is 4.2.1, and you can get it for free from their website here: [http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html")

Just click the Ubuntu icon one, and download the .deb. Double click the .deb to run it, and click the Install/Upgrade button once it appears in the Ubuntu Software Center.

---

### Post by rek2 on 2013-05-20
Hello Im having the same ssl issue... seens that wine is not compiled with openssl and cant do https calls?
did you got this to ever work?

thanks

---

