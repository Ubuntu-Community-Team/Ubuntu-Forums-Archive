---
title: "Problems: Oblivion under Wine 0.9.29"
date: 2008-02-23
forum: Wine
---

### Post by Sugi on 2008-02-23
I am installing oblivion under wine (actually PlayOnLinux) version 0.9.29.  I have been following this tutorial step by step.  [http://ubuntuforums.org/showthread.php?t=349764]("http://ubuntuforums.org/showthread.php?t=349764")  But I can't get Oblivion to even load up anymore.  I use to play it under 0.9.54, but it was unstable.  So, I went off the tutorial, but now i can't even get it to load.

Big steps from the tutorial:
 - use WINE 0.9.29
 -  copy d3dx9_27.dll to your ~/.wine/c_drive/Windows/System32
 - [x] Emulate a virtual desktop - Desktop size: [1024]  x  [768]
Vertex Shader Support [Hardware] - [x] Allow Pixel Shader


I tired 
 - wine regedit.exe
> Now browse HKEY_CURRENT_USER / Software / Wine / Direct3D. Right click in the pane to make New > String Value for each of the following key pairs:

Code:
OffscreenRenderingMode	fbo
	UseGLSL					enabled
	VideoMemorySize		256

but I didn't have the directory of "Direct3D" under the Wine directory within the regedit.  How should I go about doing this?

My terminal output:
> :~$ /usr/share/playonlinux/playonlinux --run "Elder Scrolls IV Oblivion"

PlayOnLinux v2.0
----------------
Checking python :                               [ Ok ]
wine client error:16: version mismatch 337/263.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?
:~$ 

I have tired restarting the whole OS and even tired killing wineserver, but that didn't do anything.  Does anyone know what I should do to fix this?

Sugi

---

### Post by happyhamster on 2008-02-23
> **Sugi said:**
> I am installing oblivion under wine (actually PlayOnLinux) version 0.9.29.  I have been following this tutorial step by step.  [http://ubuntuforums.org/showthread.php?t=349764]("http://ubuntuforums.org/showthread.php?t=349764")  But I can't get Oblivion to even load up anymore.  I use to play it under 0.9.54, but it was unstable.  So, I went off the tutorial, but now i can't even get it to load.

Big steps from the tutorial:
 - use WINE 0.9.29
 -  copy d3dx9_27.dll to your ~/.wine/c_drive/Windows/System32
 - [x] Emulate a virtual desktop - Desktop size: [1024]  x  [768]
Vertex Shader Support [Hardware] - [x] Allow Pixel Shader


I tired 
 - wine regedit.exe


but I didn't have the directory of "Direct3D" under the Wine directory within the regedit.  How should I go about doing this?
- An easy way is making a text file and importing that file into the registry. In an empty text file, paste:

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"VideoMemorySize"="256"
"UseGLSL"="enabled"
"OffscreenRenderingMode"="fbo"

- Save it as "desired_name.reg" and import it into the registry using:

regedit desired_name.reg

> 
My terminal output:


I have tired restarting the whole OS and even tired killing wineserver, but that didn't do anything.  Does anyone know what I should do to fix this?

Sugi
- I have no experience with PlayOnLinux, but it sounds like there are (parts of) 2 wine versions present on your system. You can check what versions wine thinks it's at, using:

wine --version

- Perhaps the command:

wineprefixcreate

- will fix things, but I don't know how PlayOnLinuxhow will react to that.

---

### Post by Sugi on 2008-02-23
I have done some tweaking (i did something unknown to me to make it work better, but I am still getting erros.)  I got into the actually game now, but got locked out of it.

Terminal:
> :~$ wine: Unhandled page fault on read access to 0x000002a0 at address 0x7e3021b6 (thread 0016), starting debugger...
Unhandled exception: page fault on read access to 0x000002a0 in 32-bit code (0x7e3021b6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e3021b6 ESP:7c7c78a0 EBP:7c7c793c EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:7ca820bc ECX:7e4cd164 EDX:0019e700
 ESI:00000001 EDI:ff000000
Stack dump:
0x7c7c78a0:  7c9f21ae 00000c11 111f0120 00000000
0x7c7c78b0:  00000400 00000500 00000500 0019e700
0x7c7c78c0:  00000000 00000400 0106e7a5 00000000
0x7c7c78d0:  00000000 00000400 00000000 5a5fa10e
0x7c7c78e0:  00000000 00000058 00dc56de 00000000
0x7c7c78f0:  7c7c7930 7bc5dfed 5a5fa10e 00000000
Backtrace:
=>1 0x7e3021b6 glTexImage2D+0x406() in libgl.so.1 (0x7c7c793c)
  2 0x7ca99a45 in d3d9 (+0x9a45) (0x7c7c796c)
  3 0x0041028a in oblivion (+0x1028a) (0x00000000)
0x7e3021b6 glTexImage2D+0x406 in libgl.so.1: jmp        *0x2a0(%eax)
Modules:
Module  Address                 Debug info      Name (92 modules)
PE      400000-b59000   Export          oblivion
PE      b60000-daf000   Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b91c000       Deferred        kernel32<elf>
  \-PE  7b820000-7b91c000       \               kernel32
ELF     7bc00000-7bc83000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c938000-7c9bb000       Deferred        libglu.so.1
ELF     7c9ca000-7ca83000       Deferred        wined3d<elf>
  \-PE  7c9e0000-7ca83000       \               wined3d
ELF     7ca83000-7caad000       Export          d3d9<elf>
  \-PE  7ca90000-7caad000       \               d3d9
ELF     7cd56000-7cd6b000       Deferred        midimap<elf>
  \-PE  7cd60000-7cd6b000       \               midimap
ELF     7cd91000-7cdcd000       Deferred        wineoss<elf>
  \-PE  7cda0000-7cdcd000       \               wineoss
ELF     7d07e000-7d096000       Deferred        msacm32<elf>
  \-PE  7d080000-7d096000       \               msacm32
ELF     7d096000-7d0c8000       Deferred        uxtheme<elf>
  \-PE  7d0a0000-7d0c8000       \               uxtheme
ELF     7d0c8000-7d0cd000       Deferred        libxfixes.so.3
ELF     7d0cd000-7d0d6000       Deferred        libxcursor.so.1
ELF     7d0d6000-7d0f2000       Deferred        imm32<elf>
  \-PE  7d0e0000-7d0f2000       \               imm32
ELF     7d0f2000-7d0f8000       Deferred        libxrandr.so.2
ELF     7d0f8000-7d100000       Deferred        libxrender.so.1
ELF     7d100000-7d103000       Deferred        libxinerama.so.1
ELF     7d8db000-7d8dd000       Deferred        libnvidia-tls.so.1
ELF     7d8dd000-7e275000       Deferred        libglcore.so.1
ELF     7e275000-7e30b000       Export          libgl.so.1
ELF     7e30b000-7e310000       Deferred        libxdmcp.so.6
ELF     7e310000-7e313000       Deferred        libxau.so.6
ELF     7e313000-7e404000       Deferred        libx11.so.6
ELF     7e404000-7e412000       Deferred        libxext.so.6
ELF     7e412000-7e417000       Deferred        libxxf86vm.so.1
ELF     7e417000-7e42f000       Deferred        libice.so.6
ELF     7e42f000-7e437000       Deferred        libsm.so.6
ELF     7e446000-7e4d3000       Deferred        winex11<elf>
  \-PE  7e460000-7e4d3000       \               winex11
ELF     7e54a000-7e56a000       Deferred        libexpat.so.1
ELF     7e56a000-7e595000       Deferred        libfontconfig.so.1
ELF     7e595000-7e5aa000       Deferred        libz.so.1
ELF     7e5aa000-7e61a000       Deferred        libfreetype.so.6
ELF     7e61a000-7e646000       Deferred        ws2_32<elf>
  \-PE  7e620000-7e646000       \               ws2_32
ELF     7e646000-7e660000       Deferred        wsock32<elf>
  \-PE  7e650000-7e660000       \               wsock32
ELF     7e660000-7e6c4000       Deferred        msvcrt<elf>
  \-PE  7e670000-7e6c4000       \               msvcrt
ELF     7e6c4000-7e6d8000       Deferred        lz32<elf>
  \-PE  7e6d0000-7e6d8000       \               lz32
ELF     7e6d8000-7e6f1000       Deferred        version<elf>
  \-PE  7e6e0000-7e6f1000       \               version
ELF     7e6f1000-7e749000       Deferred        shlwapi<elf>
  \-PE  7e700000-7e749000       \               shlwapi
ELF     7e749000-7e83b000       Deferred        shell32<elf>
  \-PE  7e760000-7e83b000       \               shell32
ELF     7e83b000-7e884000       Deferred        dsound<elf>
  \-PE  7e840000-7e884000       \               dsound
ELF     7e884000-7e912000       Deferred        winmm<elf>
  \-PE  7e890000-7e912000       \               winmm
ELF     7e912000-7e925000       Deferred        libresolv.so.2
ELF     7e925000-7e943000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e943000       \               iphlpapi
ELF     7e943000-7e997000       Deferred        rpcrt4<elf>
  \-PE  7e950000-7e997000       \               rpcrt4
ELF     7e997000-7ea30000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea30000       \               ole32
ELF     7ea30000-7ea67000       Deferred        dinput<elf>
  \-PE  7ea40000-7ea67000       \               dinput
ELF     7ea67000-7ea80000       Deferred        dinput8<elf>
  \-PE  7ea70000-7ea80000       \               dinput8
ELF     7ea80000-7eac6000       Deferred        advapi32<elf>
  \-PE  7ea90000-7eac6000       \               advapi32
ELF     7eac6000-7ead1000       Deferred        libgcc_s.so.1
ELF     7ebc4000-7ec7a000       Deferred        gdi32<elf>
  \-PE  7ebe0000-7ec7a000       \               gdi32
ELF     7ec7a000-7edb2000       Deferred        user32<elf>
  \-PE  7ec90000-7edb2000       \               user32
ELF     7edb2000-7ee72000       Deferred        comctl32<elf>
  \-PE  7edc0000-7ee72000       \               comctl32
ELF     7ee72000-7ee7d000       Deferred        libnss_files.so.2
ELF     7ee7d000-7ee95000       Deferred        libnsl.so.1
ELF     7ee95000-7ee9e000       Deferred        libnss_compat.so.2
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d37000-b7d3b000       Deferred        libdl.so.2
ELF     b7d3b000-b7e85000       Deferred        libc.so.6
ELF     b7e86000-b7e9e000       Deferred        libpthread.so.0
ELF     b7ead000-b7fbe000       Deferred        libwine.so.1
ELF     b7fc0000-b7fdc000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Program Files\Oblivion\Oblivion.exe
        00000016    1 <==
        00000014   -1
        00000013   -1
        00000011    0
        00000010    0
0000000b 
        0000000e    0
        0000000c    0


I will try the input reg thingy, and I'll get back to you on that.  Thanks, I never knew I could do that.

Sugi

---

### Post by Sugi on 2008-02-23
Oh kay, I did the regedit with the gedit to make a file format of .reg.  Then, I also inputed the .reg file and even changed it to 512 for video ram, because I got that much in my PC.  But when I start up the game, I get similar error.  What should I do now?  :(

> 
Running Elder Scrolls IV Oblivion
wine: Unhandled page fault on read access to 0x000002a0 at address 0x7e3021b6 (thread 0016), starting debugger...
Unhandled exception: page fault on read access to 0x000002a0 in 32-bit code (0x7e3021b6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e3021b6 ESP:7bded8a0 EBP:7bded93c EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:7ca850bc ECX:7e4cd164 EDX:0019e768
 ESI:00000001 EDI:ff000000
Stack dump:
0x7bded8a0:  7c9f51ae 00000c11 11300120 00000000
0x7bded8b0:  00000400 00000500 00000500 0019e768
0x7bded8c0:  00000000 00000400 004d326f 00000000
0x7bded8d0:  00000000 00000400 00000000 1a89567e
0x7bded8e0:  00000000 00000058 0040b2ce 00000000
0x7bded8f0:  7bded930 7bc5dfed 1a89567e 00000000
Backtrace:
=>1 0x7e3021b6 glTexImage2D+0x406() in libgl.so.1 (0x7bded93c)
  2 0x7ca9ca45 in d3d9 (+0xca45) (0x7bded96c)
  3 0x0041028a in oblivion (+0x1028a) (0x00000000)
0x7e3021b6 glTexImage2D+0x406 in libgl.so.1: jmp        *0x2a0(%eax)
Modules:
Module  Address                 Debug info      Name (92 modules)
PE      400000-b59000   Export          oblivion
PE      b60000-daf000   Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b91c000       Deferred        kernel32<elf>
  \-PE  7b820000-7b91c000       \               kernel32
ELF     7bc00000-7bc83000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c93b000-7c9be000       Deferred        libglu.so.1
ELF     7c9cd000-7ca86000       Deferred        wined3d<elf>
  \-PE  7c9e0000-7ca86000       \               wined3d
ELF     7ca86000-7cab0000       Export          d3d9<elf>
  \-PE  7ca90000-7cab0000       \               d3d9
ELF     7cd57000-7cd6c000       Deferred        midimap<elf>
  \-PE  7cd60000-7cd6c000       \               midimap
ELF     7cd92000-7cdce000       Deferred        wineoss<elf>
  \-PE  7cda0000-7cdce000       \               wineoss
ELF     7d083000-7d09b000       Deferred        msacm32<elf>
  \-PE  7d090000-7d09b000       \               msacm32
ELF     7d09b000-7d0cd000       Deferred        uxtheme<elf>
  \-PE  7d0a0000-7d0cd000       \               uxtheme
ELF     7d0cd000-7d0d6000       Deferred        libxcursor.so.1
ELF     7d0d6000-7d0f2000       Deferred        imm32<elf>
  \-PE  7d0e0000-7d0f2000       \               imm32
ELF     7d0f2000-7d0f8000       Deferred        libxrandr.so.2
ELF     7d0f8000-7d100000       Deferred        libxrender.so.1
ELF     7d100000-7d103000       Deferred        libxinerama.so.1
ELF     7d8db000-7d8dd000       Deferred        libnvidia-tls.so.1
ELF     7d8dd000-7e275000       Deferred        libglcore.so.1
ELF     7e275000-7e30b000       Export          libgl.so.1
ELF     7e30b000-7e310000       Deferred        libxdmcp.so.6
ELF     7e310000-7e313000       Deferred        libxau.so.6
ELF     7e313000-7e404000       Deferred        libx11.so.6
ELF     7e404000-7e412000       Deferred        libxext.so.6
ELF     7e412000-7e417000       Deferred        libxxf86vm.so.1
ELF     7e417000-7e42f000       Deferred        libice.so.6
ELF     7e42f000-7e437000       Deferred        libsm.so.6
ELF     7e437000-7e43c000       Deferred        libxfixes.so.3
ELF     7e446000-7e4d3000       Deferred        winex11<elf>
  \-PE  7e460000-7e4d3000       \               winex11
ELF     7e54a000-7e56a000       Deferred        libexpat.so.1
ELF     7e56a000-7e595000       Deferred        libfontconfig.so.1
ELF     7e595000-7e5aa000       Deferred        libz.so.1
ELF     7e5aa000-7e61a000       Deferred        libfreetype.so.6
ELF     7e61a000-7e646000       Deferred        ws2_32<elf>
  \-PE  7e620000-7e646000       \               ws2_32
ELF     7e646000-7e660000       Deferred        wsock32<elf>
  \-PE  7e650000-7e660000       \               wsock32
ELF     7e660000-7e6c4000       Deferred        msvcrt<elf>
  \-PE  7e670000-7e6c4000       \               msvcrt
ELF     7e6c4000-7e6d8000       Deferred        lz32<elf>
  \-PE  7e6d0000-7e6d8000       \               lz32
ELF     7e6d8000-7e6f1000       Deferred        version<elf>
  \-PE  7e6e0000-7e6f1000       \               version
ELF     7e6f1000-7e749000       Deferred        shlwapi<elf>
  \-PE  7e700000-7e749000       \               shlwapi
ELF     7e749000-7e83b000       Deferred        shell32<elf>
  \-PE  7e760000-7e83b000       \               shell32
ELF     7e83b000-7e884000       Deferred        dsound<elf>
  \-PE  7e840000-7e884000       \               dsound
ELF     7e884000-7e912000       Deferred        winmm<elf>
  \-PE  7e890000-7e912000       \               winmm
ELF     7e912000-7e925000       Deferred        libresolv.so.2
ELF     7e925000-7e943000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e943000       \               iphlpapi
ELF     7e943000-7e997000       Deferred        rpcrt4<elf>
  \-PE  7e950000-7e997000       \               rpcrt4
ELF     7e997000-7ea30000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea30000       \               ole32
ELF     7ea30000-7ea67000       Deferred        dinput<elf>
  \-PE  7ea40000-7ea67000       \               dinput
ELF     7ea67000-7ea80000       Deferred        dinput8<elf>
  \-PE  7ea70000-7ea80000       \               dinput8
ELF     7ea80000-7eac6000       Deferred        advapi32<elf>
  \-PE  7ea90000-7eac6000       \               advapi32
ELF     7eac6000-7ead1000       Deferred        libgcc_s.so.1
ELF     7ebc4000-7ec7a000       Deferred        gdi32<elf>
  \-PE  7ebe0000-7ec7a000       \               gdi32
ELF     7ec7a000-7edb2000       Deferred        user32<elf>
  \-PE  7ec90000-7edb2000       \               user32
ELF     7edb2000-7ee72000       Deferred        comctl32<elf>
  \-PE  7edc0000-7ee72000       \               comctl32
ELF     7ee72000-7ee7d000       Deferred        libnss_files.so.2
ELF     7ee7d000-7ee95000       Deferred        libnsl.so.1
ELF     7ee95000-7ee9e000       Deferred        libnss_compat.so.2
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d28000-b7d2c000       Deferred        libdl.so.2
ELF     b7d2c000-b7e76000       Deferred        libc.so.6
ELF     b7e77000-b7e8f000       Deferred        libpthread.so.0
ELF     b7e9e000-b7faf000       Deferred        libwine.so.1
ELF     b7fb1000-b7fcd000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Program Files\Oblivion\Oblivion.exe
        00000016    1 <==
        00000014   -1
        00000013   -1
        00000011    0
        00000010    0
0000000b 
        0000000e    0
        0000000c    0


Sugi

---

### Post by Sugi on 2008-02-23
I have been tweaking Oblivion for the last hour just to make it run, but I haven't even got it to run.  I was starting to lose hope, but then I tired changing wine's versions and I finally got it to run under 0.9.51.  But now, it's going to be crazy unstable.  Does anyone know if I should keep trying to get it to work under 0.9.29 or try to tweak it under 0.9.51?

Sugi

---

### Post by happyhamster on 2008-02-23
Well, wine 0.9.29 was released quite a while ago. Apparently people succeeded in running Oblivion with it, but they were using different linux kernels, different video drivers etc. So I think a more recent wine version will increase your chances. Also, Oblivion itself is not that stable: it'll crash sometimes even when running it on a monster gaming rig under windows XP.

If you're not tired of experimenting yet, this is what the Oblivion community itself has written concerning linux/wine: [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux) 

[edit: They recommend wine 0.9.38, which is also quite old.]

---

### Post by Mongoose on 2008-02-23
Don't use 0.9.29 -- use 0.9.38.  You can get the deb from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) as mentioned in the Oblivion wiki.  You should also read the wiki for proper setup.

wiki:

[http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

---

### Post by Sugi on 2008-02-23
Wow, thanks for the link.  I'll start looking into it now.  This might take a while. :)


Sugi

---

