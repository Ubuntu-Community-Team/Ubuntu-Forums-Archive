---
title: "Heroes V&amp;Warcraft III"
date: 2008-06-23
forum: Wine
---

### Post by Troll_the_Great on 2008-06-23
Hy all

I started to use Ubuntu for about 2 and a half months and I just love it.The only thing I use dual boot is games.So here is my problem.
I am trying to make 2 games work:
Heroes of Might and Magic V and Warcraft III.
I installed Heroes V and when I try to play it, the screen goes black (like the game is starting) and then, after a few secconds, the desktop appears.I started the game for the terminal and I got this:

```
~$ env WINEPREFIX="/home/troll/.wine" wine "Z:\home\troll\Games\Heroes of Might and Magic V\bin\H5_Game.exe"
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,9,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,27,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,36,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,45,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,54,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,63,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,72,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,81,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,90,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,99,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,108,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,117,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,126,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,144,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,153,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,162,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,171,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,180,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,189,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,198,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,207,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,216,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,234,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,243,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,252,2): stub!
ERROR: Failed to open file with type descriptions (types.xml)
wine: Unhandled page fault on read access to 0x0000004c at address 0x941542 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000004c in 32-bit code (0x00941542).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00941542 ESP:01c8fda8 EBP:01c8fdcc EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:00cd636c ECX:01c8fef8 EDX:10025330
 ESI:00000000 EDI:00000000
Stack dump:
0x01c8fda8:  00000000 1019f870 ffffffff 00cd636c
0x01c8fdb8:  01c8fdcc 0099625e 00000002 10339c10
0x01c8fdc8:  00000001 1062ed90 1062eda6 1062eda7
0x01c8fdd8:  00a2be15 00b1d868 10339c10 004092cd
0x01c8fde8:  7b866bb0 00000000 00000000 00000001
0x01c8fdf8:  00cc4e80 01c8fe18 00b43dc3 00111f21
Backtrace:
=>1 0x00941542 in h5_game (+0x541542) (0x01c8fdcc)
  2 0x1062eda6 (0x1062ed90)
  3 0x5f4a424f (0x5f564441)
0x00941542: movl	0x4c(%esi),%ecx
Modules:
Module	Address			Debug info	Name (124 modules)
PE	  240000-  27b000	Deferred        libcurl
PE	  280000-  296000	Deferred        zlibwapi
PE	  2a0000-  336000	Deferred        fmod
PE	  340000-  36c000	Deferred        ubistats
PE	  400000- 1a90000	Export          h5_game
PE	 1c90000- 1ee3000	Deferred        d3dx9_25
PE	10000000-10013000	Deferred        zlib1
PE	50000000-50086000	Deferred        granny2
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7dc63000-7dc67000	Deferred        libgpg-error.so.0
ELF	7dc67000-7dcb4000	Deferred        libgcrypt.so.11
ELF	7dcb4000-7dcc4000	Deferred        libtasn1.so.3
ELF	7dcc4000-7dcc7000	Deferred        libkeyutils.so.1
ELF	7dcc7000-7dccf000	Deferred        libkrb5support.so.0
ELF	7dccf000-7dd01000	Deferred        libcrypt.so.1
ELF	7dd01000-7dd77000	Deferred        libgnutls.so.13
ELF	7dd77000-7dd9a000	Deferred        libk5crypto.so.3
ELF	7dd9a000-7de27000	Deferred        libkrb5.so.3
ELF	7de27000-7de50000	Deferred        libgssapi_krb5.so.2
ELF	7de50000-7de83000	Deferred        libcups.so.2
ELF	7de83000-7de97000	Deferred        midimap<elf>
  \-PE	7de90000-7de97000	\               midimap
ELF	7de97000-7deae000	Deferred        msacm32<elf>
  \-PE	7dea0000-7deae000	\               msacm32
ELF	7deae000-7df71000	Deferred        libasound.so.2
ELF	7df83000-7dfb9000	Deferred        winealsa<elf>
  \-PE	7df90000-7dfb9000	\               winealsa
ELF	7e005000-7e038000	Deferred        uxtheme<elf>
  \-PE	7e010000-7e038000	\               uxtheme
ELF	7e038000-7e041000	Deferred        libxcursor.so.1
ELF	7e041000-7e046000	Deferred        libxfixes.so.3
ELF	7e046000-7e049000	Deferred        libxcomposite.so.1
ELF	7e049000-7e04f000	Deferred        libxrandr.so.2
ELF	7e04f000-7e057000	Deferred        libxrender.so.1
ELF	7e057000-7e05a000	Deferred        libxinerama.so.1
ELF	7e05a000-7e07a000	Deferred        imm32<elf>
  \-PE	7e060000-7e07a000	\               imm32
ELF	7e07a000-7e07f000	Deferred        libxdmcp.so.6
ELF	7e07f000-7e097000	Deferred        libxcb.so.1
ELF	7e097000-7e099000	Deferred        libxcb-xlib.so.0
ELF	7e099000-7e09c000	Deferred        libxau.so.6
ELF	7e09c000-7e183000	Deferred        libx11.so.6
ELF	7e183000-7e191000	Deferred        libxext.so.6
ELF	7e191000-7e196000	Deferred        libxxf86vm.so.1
ELF	7e196000-7e1ae000	Deferred        libice.so.6
ELF	7e1ae000-7e1b6000	Deferred        libsm.so.6
ELF	7e1c3000-7e1c6000	Deferred        libcom_err.so.2
ELF	7e1c8000-7e25f000	Deferred        winex11<elf>
  \-PE	7e1e0000-7e25f000	\               winex11
ELF	7e29d000-7e2be000	Deferred        libexpat.so.1
ELF	7e2be000-7e2e8000	Deferred        libfontconfig.so.1
ELF	7e2e8000-7e2fd000	Deferred        libz.so.1
ELF	7e2fd000-7e36d000	Deferred        libfreetype.so.6
ELF	7e36d000-7e418000	Deferred        comdlg32<elf>
  \-PE	7e370000-7e418000	\               comdlg32
ELF	7e418000-7e44e000	Deferred        winspool<elf>
  \-PE	7e420000-7e44e000	\               winspool
ELF	7e44e000-7e462000	Deferred        oleacc<elf>
  \-PE	7e450000-7e462000	\               oleacc
ELF	7e462000-7e483000	Deferred        mpr<elf>
  \-PE	7e470000-7e483000	\               mpr
ELF	7e483000-7e4d1000	Deferred        wininet<elf>
  \-PE	7e490000-7e4d1000	\               wininet
ELF	7e4d1000-7e4f7000	Deferred        msacm32<elf>
  \-PE	7e4e0000-7e4f7000	\               msacm32
ELF	7e4f7000-7e52e000	Deferred        dinput<elf>
  \-PE	7e500000-7e52e000	\               dinput
ELF	7e52e000-7e546000	Deferred        dinput8<elf>
  \-PE	7e530000-7e546000	\               dinput8
ELF	7e546000-7e560000	Deferred        wsock32<elf>
  \-PE	7e550000-7e560000	\               wsock32
ELF	7e560000-7e579000	Deferred        crtdll<elf>
  \-PE	7e570000-7e579000	\               crtdll
ELF	7e579000-7e60b000	Deferred        winmm<elf>
  \-PE	7e580000-7e60b000	\               winmm
ELF	7e60b000-7e637000	Deferred        ws2_32<elf>
  \-PE	7e610000-7e637000	\               ws2_32
ELF	7e637000-7e6a1000	Deferred        msvcrt<elf>
  \-PE	7e650000-7e6a1000	\               msvcrt
ELF	7e6a1000-7e7a4000	Deferred        wined3d<elf>
  \-PE	7e6b0000-7e7a4000	\               wined3d
ELF	7e7a4000-7e7d4000	Deferred        d3d9<elf>
  \-PE	7e7b0000-7e7d4000	\               d3d9
ELF	7e7d4000-7e7e9000	Deferred        psapi<elf>
  \-PE	7e7e0000-7e7e9000	\               psapi
ELF	7e7e9000-7e833000	Deferred        dbghelp<elf>
  \-PE	7e7f0000-7e833000	\               dbghelp
ELF	7e833000-7e8d5000	Deferred        oleaut32<elf>
  \-PE	7e840000-7e8d5000	\               oleaut32
ELF	7e8d5000-7e8e8000	Deferred        libresolv.so.2
ELF	7e8fa000-7e918000	Deferred        iphlpapi<elf>
  \-PE	7e900000-7e918000	\               iphlpapi
ELF	7e918000-7e979000	Deferred        rpcrt4<elf>
  \-PE	7e920000-7e979000	\               rpcrt4
ELF	7e979000-7ea1d000	Deferred        ole32<elf>
  \-PE	7e990000-7ea1d000	\               ole32
ELF	7ea1d000-7eadc000	Deferred        comctl32<elf>
  \-PE	7ea30000-7eadc000	\               comctl32
ELF	7eadc000-7eb35000	Deferred        shlwapi<elf>
  \-PE	7eaf0000-7eb35000	\               shlwapi
ELF	7eb35000-7ec48000	Deferred        shell32<elf>
  \-PE	7eb50000-7ec48000	\               shell32
ELF	7ec48000-7ec9a000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec9a000	\               advapi32
ELF	7ec9a000-7ed35000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed35000	\               gdi32
ELF	7ed35000-7ee7c000	Deferred        user32<elf>
  \-PE	7ed50000-7ee7c000	\               user32
ELF	7ef9c000-7efa7000	Deferred        libnss_files.so.2
ELF	7efa7000-7efb1000	Deferred        libnss_nis.so.2
ELF	7efb1000-7efc9000	Deferred        libnsl.so.1
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c46000-b7c4a000	Deferred        libdl.so.2
ELF	b7c4a000-b7d99000	Deferred        libc.so.6
ELF	b7d9a000-b7db2000	Deferred        libpthread.so.0
ELF	b7dc4000-b7efa000	Deferred        libwine.so.1
ELF	b7efc000-b7f18000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\troll\Games\Heroes of Might and Magic V\bin\H5_Game.exe
	00000019    0
	00000018    0
	00000009    0 <==
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
=>1 0x00941542 in h5_game (+0x541542) (0x01c8fdcc)
  2 0x1062eda6 (0x1062ed90)
  3 0x5f4a424f (0x5f564441)
```
Did somebody manage to play it?Please tell me how.

PS:I saw the how-to from this link: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4905](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4905)

---

### Post by DrFaust on 2008-08-23
I had the same issue. The solution I found was to start the game from within the bin/-directory of the HOMMV installation. It is not working for me right now, but the error-message has changes so I guess the issue is a different one now.
Just try it, maybe it helps. Although I must admit I have no idea what you are doing with wine in the command you use. I'm not very skilled in using it, hence my command looks rather simple: [FONT="Courier New"].../bin$wine H5_Game.exe[/FONT]...

---

