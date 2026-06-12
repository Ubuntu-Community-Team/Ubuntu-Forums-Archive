---
title: "Error when trying to run compiled WINE with rgl.patch"
date: 2013-01-28
forum: Wine
---

### Post by Thee on 2013-01-28
Hi

So I downloaded Wine sources, unpacked and did:

```
cd wine-1.4
patch -p1 < ../rgl.patch
./configure --enable-win64
make

```

Note, I couldnt download the rgl.patch from the official site since its down, so I used the patch from here and it didnt return any errors when I applied it: [http://bugs.winehq.org/show_bug.cgi?id=11674](http://bugs.winehq.org/show_bug.cgi?id=11674)


When its done compiling, and when I try to run WoW I get:

```

./wine64 /home/zoran/Games/wow/Wow-64.exe
fixme:seh:RtlAddFunctionTable 0x61e45620 1 61e40000: stub
fixme:seh:RtlAddFunctionTable 0x61776ba0 1 61700000: stub
fixme:seh:RtlAddFunctionTable 0x64f69540 1 64f40000: stub
fixme:seh:RtlAddFunctionTable 0x622c6620 1 622c0000: stub
fixme:seh:RtlAddFunctionTable 0x6ce47620 1 6ce40000: stub
fixme:seh:RtlAddFunctionTable 0x682d4b20 1 682c0000: stub
fixme:seh:RtlAddFunctionTable 0x638d1dc0 1 63800000: stub
fixme:seh:RtlAddFunctionTable 0x3b6ea0 1 390000: stub
fixme:seh:RtlAddFunctionTable 0x68f5b6a0 1 68f40000: stub
fixme:seh:RtlAddFunctionTable 0x6b431bc0 1 69c40000: stub
fixme:iphlpapi:NotifyAddrChange (Handle 0xdbe308, overlapped 0xdbe2d0): stub
wine client error:0: version mismatch 431/438.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?
wine: configuration in '/home/zoran/.wine' has been updated.
fixme:heap:HeapSetInformation 0x3c4000 0 0x22fce0 4
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:win:EnumDisplayDevicesW ((null),0,0x22e7a0,0x00000000), stub!
err:d3d:InitAdapters Can't load opengl32.dll!
Direct3D9 is not available without OpenGL.
fixme:win:EnumDisplayDevicesW ((null),0,0x22a460,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x22a460,0x00000000), stub!
fixme:dbghelp_dwarf:compute_location Only supporting one breg (rax/328 -> rdi/333)
fixme:dbghelp_dwarf:dwarf2_parse_subprogram_block Unhandled Tag type 0x15 at ctx(0x2274d0,L"kernel32<elf>"), for debug_info(abbrev:0x3ed1918,symt:(nil))
fixme:dbghelp_dwarf:dwarf2_parse_subprogram_block Unhandled Tag type 0xf at ctx(0x2274d0,L"kernel32<elf>"), for debug_info(abbrev:0x3ed1918,symt:(nil))
wine client error:0: version mismatch 431/438.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

```

Anyone knows what I'm doing wrong?

---

### Post by Thee on 2013-01-28
Ok I removed Wine 1.5 that I had installed, and now I'm getting only this:

```

fixme:heap:HeapSetInformation 0x3c4000 0 0x22fce0 4
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:win:EnumDisplayDevicesW ((null),0,0x22e7a0,0x00000000), stub!
err:d3d:InitAdapters Can't load opengl32.dll!
Direct3D9 is not available without OpenGL.
fixme:win:EnumDisplayDevicesW ((null),0,0x22a460,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x22a460,0x00000000), stub!
fixme:dbghelp_dwarf:compute_location Only supporting one breg (rax/328 -> rdi/333)
fixme:dbghelp_dwarf:dwarf2_parse_subprogram_block Unhandled Tag type 0x15 at ctx(0x2274d0,L"kernel32<elf>"), for debug_info(abbrev:0x3ee1948,symt:(nil))
fixme:dbghelp_dwarf:dwarf2_parse_subprogram_block Unhandled Tag type 0xf at ctx(0x2274d0,L"kernel32<elf>"), for debug_info(abbrev:0x3ee1948,symt:(nil))

```

So I'm guessing that Wine cant find OpenGL 32 libraries for some reason...?

---

### Post by Tweak42 on 2013-01-29
Part of the problem could be multi-arch. It was a headache trying to compile muti-arch wine after ubuntu 12.04 shipped.  Ended up compiling wine on a 32bit ubuntu virtual machine install then zip/export the wine directory to my 64 bit system. Eventually I was getting pretty much the same errors as you after wine1.5 shipped and never got it to work using the rgl.so modules.  

I beleive the best chance you to get rgl to work is to use Ubuntu 11.10 32bit (before multi-arch) and wine1.4.x.  My only experience with it was using Nvidia drivers 280.x - 300.x   


The peformance with the lastest beta Nvidia multi_threaded drivers is close enough for me to the rgl peformance so that's what I'm using now.

---

