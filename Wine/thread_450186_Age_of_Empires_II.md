---
title: "Age of Empires II"
date: 2007-05-21
forum: Wine
---

### Post by showty on 2007-05-21
Hi. I can't get AoEII running under Wine (9.0.37 or something to that effect? The latest one anyway..)

It gets into the menu, then when i try to load a learn to play map, it crashes back to desktop but the in-game music is still heard in the background (even though there are no wine/aoe related processes listed in the system monitor).

I can't test any other modes because even though my CD is in the drive it thinks I do not have a CD..

Here is a console output:
```
Unhandled exception: page fault on read access to 0x00000008 in 32-bit code (0x7e7eaeae).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e7eaeae ESP:0034ccac EBP:0034ccd4 EFLAGS:00210216(   - 00      -RIAP1)
 EAX:00000000 EBX:7e8073f8 ECX:7c8ab4c0 EDX:001748c8
 ESI:001747b8 EDI:00174788
Stack dump:
0x0034ccac:  00174788 0000022d 00000245 0000022d
0x0034ccbc:  03e00001 00000075 7ed47e7c 00003878
0x0034cccc:  001747b8 00003878 0034ccf4 7e7eed26
0x0034ccdc:  001747b8 00000000 0034ccf8 00003878
0x0034ccec:  009b3750 009b3750 0098bce8 0048ba2c
0x0034ccfc:  001747bc 00000000 00000000 0098bce8
Backtrace:
=>1 0x7e7eaeae in ddraw (+0x2aeae) (0x0034ccd4)
  2 0x7e7eed26 in ddraw (+0x2ed26) (0x0034ccf4)
  3 0x0048ba2c in empires2 (+0x8ba2c) (0x0098bce8)
  4 0x00000000 (0x0062b7dc)
  5 0x004a0820 in empires2 (+0xa0820) (0x005c6690)
0x7e7eaeae: movl        0x8(%eax),%eax
Modules:
Module  Address                 Debug info      Name (99 modules)
PE        400000-  781000       Export          empires2
PE      10000000-1007a000       Deferred        language
ELF     7b800000-7b927000       Deferred        kernel32<elf>
  \-PE  7b820000-7b927000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c45d000-7c4a1000       Deferred        riched20<elf>
  \-PE  7c470000-7c4a1000       \               riched20
ELF     7c4a1000-7c4b5000       Deferred        riched32<elf>
  \-PE  7c4b0000-7c4b5000       \               riched32
ELF     7c4b5000-7c506000       Deferred        libgcrypt.so.11
ELF     7c506000-7c51b000       Deferred        libtasn1.so.3
ELF     7c51b000-7c549000       Deferred        libcrypt.so.1
ELF     7c557000-7c5c7000       Deferred        libgnutls.so.13
ELF     7c5c7000-7c5f8000       Deferred        libcups.so.2
ELF     7c625000-7c629000       Deferred        libgpg-error.so.0
ELF     7c695000-7c6ac000       Deferred        mcicda<elf>
  \-PE  7c6a0000-7c6ac000       \               mcicda
ELF     7c768000-7c7e8000       Deferred        libglu.so.1
ELF     7c7e8000-7c8ad000       Deferred        wined3d<elf>
  \-PE  7c800000-7c8ad000       \               wined3d
ELF     7c8ad000-7c8df000       Deferred        uxtheme<elf>
  \-PE  7c8b0000-7c8df000       \               uxtheme
ELF     7c8df000-7c8f4000       Deferred        midimap<elf>
  \-PE  7c8f0000-7c8f4000       \               midimap
ELF     7c8f4000-7c91a000       Deferred        msacm32<elf>
  \-PE  7c900000-7c91a000       \               msacm32
ELF     7c91a000-7c932000       Deferred        msacm32<elf>
  \-PE  7c920000-7c932000       \               msacm32
ELF     7c932000-7c9f7000       Deferred        libasound.so.2
ELF     7c9f7000-7ca28000       Deferred        winealsa<elf>
  \-PE  7ca00000-7ca28000       \               winealsa
ELF     7ca28000-7ca31000       Deferred        libxcursor.so.1
ELF     7ca31000-7ca39000       Deferred        libxrender.so.1
ELF     7d061000-7d067000       Deferred        libxrandr.so.2
ELF     7d165000-7d16a000       Deferred        libxfixes.so.3
ELF     7d9ba000-7d9c3000       Deferred        librt.so.1
ELF     7da8b000-7e3bc000       Deferred        fglrx_dri.so
ELF     7e3bc000-7e45c000       Deferred        libgl.so.1
ELF     7e45c000-7e4eb000       Deferred        winex11<elf>
  \-PE  7e470000-7e4eb000       \               winex11
ELF     7e56d000-7e58d000       Deferred        libexpat.so.1
ELF     7e58d000-7e5b8000       Deferred        libfontconfig.so.1
ELF     7e5b8000-7e5cc000       Deferred        libz.so.1
ELF     7e5cc000-7e637000       Deferred        libfreetype.so.6
ELF     7e637000-7e664000       Deferred        ws2_32<elf>
  \-PE  7e640000-7e664000       \               ws2_32
ELF     7e664000-7e67e000       Deferred        wsock32<elf>
  \-PE  7e670000-7e67e000       \               wsock32
ELF     7e67e000-7e69b000       Deferred        imm32<elf>
  \-PE  7e690000-7e69b000       \               imm32
ELF     7e69b000-7e6a0000       Deferred        libxdmcp.so.6
ELF     7e6a0000-7e791000       Deferred        libx11.so.6
ELF     7e791000-7e79f000       Deferred        libxext.so.6
ELF     7e79f000-7e7b7000       Deferred        libice.so.6
ELF     7e7b7000-7e809000       Export          ddraw<elf>
  \-PE  7e7c0000-7e809000       \               ddraw
ELF     7e809000-7e852000       Deferred        dsound<elf>
  \-PE  7e810000-7e852000       \               dsound
ELF     7e852000-7e865000       Deferred        libresolv.so.2
ELF     7e865000-7e883000       Deferred        iphlpapi<elf>
  \-PE  7e870000-7e883000       \               iphlpapi
ELF     7e883000-7e8d8000       Deferred        rpcrt4<elf>
  \-PE  7e890000-7e8d8000       \               rpcrt4
ELF     7e8d8000-7e975000       Deferred        ole32<elf>
  \-PE  7e8f0000-7e975000       \               ole32
ELF     7e975000-7e9a9000       Deferred        dplayx<elf>
  \-PE  7e980000-7e9a9000       \               dplayx
ELF     7e9a9000-7ea65000       Deferred        comctl32<elf>
  \-PE  7e9b0000-7ea65000       \               comctl32
ELF     7ea65000-7eaac000       Deferred        advapi32<elf>
  \-PE  7ea70000-7eaac000       \               advapi32
ELF     7eaac000-7eab8000       Deferred        libgcc_s.so.1
ELF     7eba2000-7ec61000       Deferred        gdi32<elf>
  \-PE  7ebc0000-7ec61000       \               gdi32
ELF     7ec61000-7ed9d000       Deferred        user32<elf>
  \-PE  7ec80000-7ed9d000       \               user32
ELF     7ed9d000-7ee2c000       Deferred        winmm<elf>
  \-PE  7edb0000-7ee2c000       \               winmm
ELF     7ee2c000-7ee53000       Deferred        msvfw32<elf>
  \-PE  7ee30000-7ee53000       \               msvfw32
ELF     7ee53000-7ee67000       Deferred        lz32<elf>
  \-PE  7ee60000-7ee67000       \               lz32
ELF     7ee67000-7ee80000       Deferred        version<elf>
  \-PE  7ee70000-7ee80000       \               version
ELF     7ee80000-7ee8b000       Deferred        libnss_files.so.2
ELF     7ee8b000-7eea2000       Deferred        libnsl.so.1
ELF     7eea2000-7eeab000       Deferred        libnss_compat.so.2
ELF     7eeab000-7eeb0000       Deferred        libxxf86vm.so.1
ELF     7eeb0000-7eeb9000       Deferred        libsm.so.6
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff2000-7eff5000       Deferred        libxau.so.6
ELF     7eff5000-7efff000       Deferred        libnss_nis.so.2
ELF     b7cd3000-b7cd7000       Deferred        libdl.so.2
ELF     b7cd7000-b7e18000       Deferred        libc.so.6
ELF     b7e18000-b7e2f000       Deferred        libpthread.so.0
ELF     b7e3d000-b7f4e000       Deferred        libwine.so.1
ELF     b7f50000-b7f6b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000b (D) C:\Program Files\Microsoft Games\Age of Empires II\empires2.exe
        0000000f    0
        0000000e    0
        0000000d   15
        0000000c    0 <==
00000008 
        0000000a    0
        00000009    0

```
Thanks!

---

### Post by maxamillion on 2007-05-21
I haven't been able to get AOE2 to run on wine or cedega, I think there is just something it calls for that isn't supported yet but if I am wrong, I would love to know how its working .... I played that game on a friends windows machine and bought it (thinking it was old enough that wine wouldn't have a problem running it) and haven't been able to get it going yet.... thus i stick to blizzard titles.

Starcraft and WarCraft3 are wonderful :)

---

### Post by showty on 2007-05-21
No.. says on winehq that some people have got it running.

---

### Post by BetaguyGZT on 2007-05-21
It probably needs IE or some other related component. I suspect that the install and loading screens use some kind of hta thing.

---

### Post by showty on 2007-05-22
> **BetaguyGZT said:**
> It probably needs IE or some other related component. I suspect that the install and loading screens use some kind of hta thing.

Is there a possibility I can try installing IE?

---

### Post by bittibuumi on 2007-05-30
I want too play AoE2! Pls Help me! I have the same problem.

---

### Post by Iarwain ben-adar on 2007-05-30
Anyone tried [this](http://appdb.winehq.org/appview.php?iVersionId=147)?


Iarwain

---

### Post by Gwijde on 2008-01-23
What is the actual problem?
If you can install it, try cd in terminal to the games directory (supposedly Age Of Empires II) and type wine empire2.exe

Thats how I got it to run.

Good luck!

---

### Post by Sef on 2008-01-23
Moved to WINE.

---

### Post by TSN on 2008-01-25
Hi all.

I have a problem with running my aoe2. The installation is okay, but when i run the game, it shuts down and comes up the a box which says:
"Could not initalize graphics system. Make sure that your video card and driver are compatible with DirectDraw".

i don't understand this, cause it is a new computer, and it has all this things it needs to run it. 

Please help me.
Greetings
TSN

---

### Post by TolTime on 2008-04-12
> **showty said:**
> Hi. I can't get AoEII running under Wine (9.0.37 or something to that effect? The latest one anyway..)

It gets into the menu, then when i try to load a learn to play map, it crashes back to desktop but the in-game music is still heard in the background (even though there are no wine/aoe related processes listed in the system monitor).

I can't test any other modes because even though my CD is in the drive it thinks I do not have a CD..

Here is a console output:
```
Unhandled exception: page fault on read access to 0x00000008 in 32-bit code (0x7e7eaeae).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e7eaeae ESP:0034ccac EBP:0034ccd4 EFLAGS:00210216(   - 00      -RIAP1)
 EAX:00000000 EBX:7e8073f8 ECX:7c8ab4c0 EDX:001748c8
 ESI:001747b8 EDI:00174788
Stack dump:
0x0034ccac:  00174788 0000022d 00000245 0000022d
0x0034ccbc:  03e00001 00000075 7ed47e7c 00003878
0x0034cccc:  001747b8 00003878 0034ccf4 7e7eed26
0x0034ccdc:  001747b8 00000000 0034ccf8 00003878
0x0034ccec:  009b3750 009b3750 0098bce8 0048ba2c
0x0034ccfc:  001747bc 00000000 00000000 0098bce8
Backtrace:
=>1 0x7e7eaeae in ddraw (+0x2aeae) (0x0034ccd4)
  2 0x7e7eed26 in ddraw (+0x2ed26) (0x0034ccf4)
  3 0x0048ba2c in empires2 (+0x8ba2c) (0x0098bce8)
  4 0x00000000 (0x0062b7dc)
  5 0x004a0820 in empires2 (+0xa0820) (0x005c6690)
0x7e7eaeae: movl        0x8(%eax),%eax
Modules:
Module  Address                 Debug info      Name (99 modules)
PE        400000-  781000       Export          empires2
PE      10000000-1007a000       Deferred        language
ELF     7b800000-7b927000       Deferred        kernel32<elf>
  \-PE  7b820000-7b927000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c45d000-7c4a1000       Deferred        riched20<elf>
  \-PE  7c470000-7c4a1000       \               riched20
ELF     7c4a1000-7c4b5000       Deferred        riched32<elf>
  \-PE  7c4b0000-7c4b5000       \               riched32
ELF     7c4b5000-7c506000       Deferred        libgcrypt.so.11
ELF     7c506000-7c51b000       Deferred        libtasn1.so.3
ELF     7c51b000-7c549000       Deferred        libcrypt.so.1
ELF     7c557000-7c5c7000       Deferred        libgnutls.so.13
ELF     7c5c7000-7c5f8000       Deferred        libcups.so.2
ELF     7c625000-7c629000       Deferred        libgpg-error.so.0
ELF     7c695000-7c6ac000       Deferred        mcicda<elf>
  \-PE  7c6a0000-7c6ac000       \               mcicda
ELF     7c768000-7c7e8000       Deferred        libglu.so.1
ELF     7c7e8000-7c8ad000       Deferred        wined3d<elf>
  \-PE  7c800000-7c8ad000       \               wined3d
ELF     7c8ad000-7c8df000       Deferred        uxtheme<elf>
  \-PE  7c8b0000-7c8df000       \               uxtheme
ELF     7c8df000-7c8f4000       Deferred        midimap<elf>
  \-PE  7c8f0000-7c8f4000       \               midimap
ELF     7c8f4000-7c91a000       Deferred        msacm32<elf>
  \-PE  7c900000-7c91a000       \               msacm32
ELF     7c91a000-7c932000       Deferred        msacm32<elf>
  \-PE  7c920000-7c932000       \               msacm32
ELF     7c932000-7c9f7000       Deferred        libasound.so.2
ELF     7c9f7000-7ca28000       Deferred        winealsa<elf>
  \-PE  7ca00000-7ca28000       \               winealsa
ELF     7ca28000-7ca31000       Deferred        libxcursor.so.1
ELF     7ca31000-7ca39000       Deferred        libxrender.so.1
ELF     7d061000-7d067000       Deferred        libxrandr.so.2
ELF     7d165000-7d16a000       Deferred        libxfixes.so.3
ELF     7d9ba000-7d9c3000       Deferred        librt.so.1
ELF     7da8b000-7e3bc000       Deferred        fglrx_dri.so
ELF     7e3bc000-7e45c000       Deferred        libgl.so.1
ELF     7e45c000-7e4eb000       Deferred        winex11<elf>
  \-PE  7e470000-7e4eb000       \               winex11
ELF     7e56d000-7e58d000       Deferred        libexpat.so.1
ELF     7e58d000-7e5b8000       Deferred        libfontconfig.so.1
ELF     7e5b8000-7e5cc000       Deferred        libz.so.1
ELF     7e5cc000-7e637000       Deferred        libfreetype.so.6
ELF     7e637000-7e664000       Deferred        ws2_32<elf>
  \-PE  7e640000-7e664000       \               ws2_32
ELF     7e664000-7e67e000       Deferred        wsock32<elf>
  \-PE  7e670000-7e67e000       \               wsock32
ELF     7e67e000-7e69b000       Deferred        imm32<elf>
  \-PE  7e690000-7e69b000       \               imm32
ELF     7e69b000-7e6a0000       Deferred        libxdmcp.so.6
ELF     7e6a0000-7e791000       Deferred        libx11.so.6
ELF     7e791000-7e79f000       Deferred        libxext.so.6
ELF     7e79f000-7e7b7000       Deferred        libice.so.6
ELF     7e7b7000-7e809000       Export          ddraw<elf>
  \-PE  7e7c0000-7e809000       \               ddraw
ELF     7e809000-7e852000       Deferred        dsound<elf>
  \-PE  7e810000-7e852000       \               dsound
ELF     7e852000-7e865000       Deferred        libresolv.so.2
ELF     7e865000-7e883000       Deferred        iphlpapi<elf>
  \-PE  7e870000-7e883000       \               iphlpapi
ELF     7e883000-7e8d8000       Deferred        rpcrt4<elf>
  \-PE  7e890000-7e8d8000       \               rpcrt4
ELF     7e8d8000-7e975000       Deferred        ole32<elf>
  \-PE  7e8f0000-7e975000       \               ole32
ELF     7e975000-7e9a9000       Deferred        dplayx<elf>
  \-PE  7e980000-7e9a9000       \               dplayx
ELF     7e9a9000-7ea65000       Deferred        comctl32<elf>
  \-PE  7e9b0000-7ea65000       \               comctl32
ELF     7ea65000-7eaac000       Deferred        advapi32<elf>
  \-PE  7ea70000-7eaac000       \               advapi32
ELF     7eaac000-7eab8000       Deferred        libgcc_s.so.1
ELF     7eba2000-7ec61000       Deferred        gdi32<elf>
  \-PE  7ebc0000-7ec61000       \               gdi32
ELF     7ec61000-7ed9d000       Deferred        user32<elf>
  \-PE  7ec80000-7ed9d000       \               user32
ELF     7ed9d000-7ee2c000       Deferred        winmm<elf>
  \-PE  7edb0000-7ee2c000       \               winmm
ELF     7ee2c000-7ee53000       Deferred        msvfw32<elf>
  \-PE  7ee30000-7ee53000       \               msvfw32
ELF     7ee53000-7ee67000       Deferred        lz32<elf>
  \-PE  7ee60000-7ee67000       \               lz32
ELF     7ee67000-7ee80000       Deferred        version<elf>
  \-PE  7ee70000-7ee80000       \               version
ELF     7ee80000-7ee8b000       Deferred        libnss_files.so.2
ELF     7ee8b000-7eea2000       Deferred        libnsl.so.1
ELF     7eea2000-7eeab000       Deferred        libnss_compat.so.2
ELF     7eeab000-7eeb0000       Deferred        libxxf86vm.so.1
ELF     7eeb0000-7eeb9000       Deferred        libsm.so.6
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff2000-7eff5000       Deferred        libxau.so.6
ELF     7eff5000-7efff000       Deferred        libnss_nis.so.2
ELF     b7cd3000-b7cd7000       Deferred        libdl.so.2
ELF     b7cd7000-b7e18000       Deferred        libc.so.6
ELF     b7e18000-b7e2f000       Deferred        libpthread.so.0
ELF     b7e3d000-b7f4e000       Deferred        libwine.so.1
ELF     b7f50000-b7f6b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000b (D) C:\Program Files\Microsoft Games\Age of Empires II\empires2.exe
        0000000f    0
        0000000e    0
        0000000d   15
        0000000c    0 <==
00000008 
        0000000a    0
        00000009    0

```
Thanks!


I have the same output any new information to fix this problem

Thanks,
Toltime

---

### Post by Reggie Manzer on 2009-03-13
Hey guys, My dad ran Age of Empires II using wine, but the problem is that it was so slow that the game wasn't even play-able. So it is [SIZE="4"]"possible"[/SIZE] to run it... just don't expect anything grand.
If you hear anything more on it, let me know cause I would like to play it too!

---

### Post by kokiriwave on 2010-09-19
Direct X problem ?

---

### Post by aBaldrich on 2010-09-20
I used to have the same problem but then I tried a couple of things and made it run without any problems.

Unfortunately I can't remember exactly what made it work. Try to change wine's config so that it emulates an older version of windows, like 98 or XP. Or enable Graphics > Emulate a Virtual Desktop

---

### Post by Boab1993 on 2012-05-08
Hey just came across this post while trying to fix my aoe2 
I know its an old post but its now fully compatible with ubuntu if you download the directx codec. 
Boab1993

---

### Post by garyzw on 2012-08-14
> **Boab1993 said:**
> Hey just came across this post while trying to fix my aoe2 
I know its an old post but its now fully compatible with ubuntu if you download the directx codec. 
Boab1993

I have a problem with keyboard not working with AOE II. Anyone else have the problem?

---

### Post by borderman53 on 2012-08-17
i am having a problem that is different than yours i got the game running, but the colors are all neon and stuff. i have an ask ubuntu page on it here: [http://askubuntu.com/questions/176732/how-do-i-fix-age-of-empires-color-problem](http://askubuntu.com/questions/176732/how-do-i-fix-age-of-empires-color-problem)

---

### Post by garyzw on 2012-08-17
> **borderman53 said:**
> i am having a problem that is different than yours i got the game running, but the colors are all neon and stuff. i have an ask ubuntu page on it here: [http://askubuntu.com/questions/176732/how-do-i-fix-age-of-empires-color-problem](http://askubuntu.com/questions/176732/how-do-i-fix-age-of-empires-color-problem)

When I ran Windows I had the same problem.  When I had the problem in Windows I would minimize the game and  then un-minumize nd the colors would be correct.

I wonder if the same work around would work in Ubuntu?

---

### Post by borderman53 on 2012-08-17
> **garyzw said:**
> When I ran Windows I had the same problem.  When I had the problem in Windows I would minimize the game and  then un-minumize nd the colors would be correct.

I wonder if the same work around would work in Ubuntu?i am runing the game on ubuntu using wine, and that does not work, please reply with an solution.

---

