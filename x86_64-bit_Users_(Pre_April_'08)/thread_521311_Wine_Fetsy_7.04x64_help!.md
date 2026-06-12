---
title: "Wine Fetsy 7.04x64 help!"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by rentacop on 2007-08-09
Hey guys, I have been doing some research for the past couple of days on this error i have been getting in wine. I couldn't find any sure answers so i came to you 'the community'!


First off, I have a brand new install of ubuntu 7.04 x64 installed, Its updated with the new kernals.

sysSpecs : Amd x64 3200, Nvidia Geforce 6600gt , madwifi drivers for dwl-g510_revB

The only thing i have done to this system were install wifi drivers and nvidia drivers
 
I followed this guide on how to install the newest nvidia drivers
[http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)


```

sudo apt-get install wine // install runs fine
...
Setting up wine (0.9.42~winehq0~ubuntu~7.04-1) ..


>$ winecfg
wine: creating configuration directory '/home/davey/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/davey/.wine'.
davey@davey-pc:~$ wineserver: could not save registry branch to /home/davey/.wine-iFkSv7/system.reg : No such file or directory
wineserver: could not save registry branch to /home/davey/.wine-iFkSv7/user.reg : No such file or directory

 
```


I had wine working last week with no problems at all on my other install of ubuntu the only difference now is that i am not using the restricted drivers

Thanks!

---

### Post by Kilz on 2007-08-09
Open nautilus, your home folder will do. If you dont have hidden files showing do the following. Click Edit > Preferences then check the "Show hidden and backup files" box. Close your home folder then reopen it.
Do you have a .wine and a .wine-iFkSv7 folder?
Next, exactly how did you install wine?

---

### Post by rentacop on 2007-08-09
I installed wine by typing this in term "sudo apt-get install wine" with updated respos

Yes, i do have a .wine folder but not a .wine-iFkSv7 folder

---

### Post by rentacop on 2007-08-09
Hey guys, i have another question. I got wine working however when i try to install warcraft 2 BNE using wine it freeses at about 55% during the install


The code below is how i try to install the file
```
wine d:\install.exe 
``` 

I was wondering if there was anyway that i could get this up and running!

---

### Post by leespa on 2007-08-09
rentacop, what did you have to do to get past the segfault issue(s)?

im having same issue where initial winecfg segfaults. i have installed 64-bit repo version with all ia32* libraries, etc.

picasa doesnt work either so something missing for both...

thanks

---

### Post by Kilz on 2007-08-09
> **rentacop said:**
> Hey guys, i have another question. I got wine working however when i try to install warcraft 2 BNE using wine it freeses at about 55% during the install


The code below is how i try to install the file
```
wine d:\install.exe 
``` 

I was wondering if there was anyway that i could get this up and running!

Have you looked at the wine application database page [for warcraft 2 ]("http://appdb.winehq.org/appview.php?iVersionId=592"). Have you setup cd drives in winecfg? Here is a section from wc3 on how to do that.

Launch winecfg to do the following tasks:

    * Make sure the Windows version for Warcraft 3 is 2000, XP, or 2003 for copy protection support. Warcraft 3 supports Win2000 or later.
    * Create a drive letter for your cdrom if you have not already.For each cdrom drive letter, click advanced, and set the drive type from automatic to cdrom. You *MUST* have a drive letter before installing.

It helps to add a device node symlink, so do the following. If your cd-rom drive letter in winecfg is d: and the corresponding device node to your mount point is /dev/hdc then run the following command:
$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
Note, you *must* have two colons! You can tell what your device node is in /etc/fstab or by viewing your boot-log.

I cant remember if wc2 was multi cd, but if it is, when the installer stops change cd. Then hit enter. For some reason the change cd dialog is broken in wine. I remember it was that way with diablo 2.

---

### Post by rentacop on 2007-08-09
> **leespa said:**
> rentacop, what did you have to do to get past the segfault issue(s)?

im having same issue where initial winecfg segfaults. i have installed 64-bit repo version with all ia32* libraries, etc.

picasa doesnt work either so something missing for both...

thanks


Leespa, I used this guide here [http://ubuntuforums.org/showthread.php?t=432604](http://ubuntuforums.org/showthread.php?t=432604)

Kilz, I tried what you suggested and the install didn't work. I did mange to get warcraft 2 running by copying the directory over from my winblows half. The game seems to be running okay, only problem i have now is that when i try to connect to battle.net the game crashes

Below is what term spits out


```
wine Warcraft\ II\ BNE.exe 
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1829f8) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1826d0)->(0x10024,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1826d0)->(1,(nil)): Stub
wine: Unhandled page fault on write access to 0x00a5c000 at address 0x4e04a4 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00a5c000 in 32-bit code (0x004e04a4).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:004e04a4 ESP:0033ef84 EBP:0033f044 EFLAGS:00010206(   - 00      - RIP1)
 EAX:dcdcdedc EBX:004e009c ECX:00000000 EDX:0000002c
 ESI:01161014 EDI:00a5c000
Stack dump:
0x0033ef84:  00000000 00a5b000 00a5b000 00000000
0x0033ef94:  01160010 00000000 7cfd8dd4 0033eff0
0x0033efa4:  7cfbd325 7cfd9b8c 001c3be0 0000006c
0x0033efb4:  00000001 7c02ecb0 7e782b2c 0033efe0
0x0033efc4:  7e6db5ef 7c02f238 001c3be0 00000000
0x0033efd4:  00000001 7c19e470 00000280 00a10000
Backtrace:
=>1 0x004e04a4 (0x0033f044)
  2 0x1500719d in storm (+0x719d) (0x00000280)
  3 0x00000000 (0x00000000)
0x004e04a4: movl        %eax,0x0(%edi)
Modules:
Module  Address                 Debug info      Name (93 modules)
PE        400000-  4db000       Deferred        warcraft ii bne
PE       2000000- 200f000       Deferred        w2local
PE      10000000-1001a000       Deferred        smackw32
PE      15000000-15045000       Export          storm
PE      19000000-19068000       Deferred        battle.snp
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7caa4000-7cab9000       Deferred        midimap<elf>
  \-PE  7cab0000-7cab9000       \               midimap
ELF     7cab9000-7cadf000       Deferred        msacm32<elf>
  \-PE  7cac0000-7cadf000       \               msacm32
ELF     7cadf000-7caf7000       Deferred        msacm32<elf>
  \-PE  7caf0000-7caf7000       \               msacm32
ELF     7caf7000-7cb33000       Deferred        wineoss<elf>
  \-PE  7cb00000-7cb33000       \               wineoss
ELF     7cb33000-7cbc1000       Deferred        winmm<elf>
  \-PE  7cb40000-7cbc1000       \               winmm
ELF     7cbc1000-7cc09000       Deferred        dsound<elf>
  \-PE  7cbd0000-7cc09000       \               dsound
ELF     7cd36000-7cd42000       Deferred        libgcc_s.so.1
ELF     7ce2c000-7ceac000       Deferred        libglu.so.1
ELF     7ceba000-7cf85000       Deferred        wined3d<elf>
  \-PE  7ced0000-7cf85000       \               wined3d
ELF     7cf85000-7cfda000       Deferred        ddraw<elf>
  \-PE  7cf90000-7cfda000       \               ddraw
ELF     7d10f000-7d168000       Deferred        rpcrt4<elf>
  \-PE  7d120000-7d168000       \               rpcrt4
ELF     7d168000-7d207000       Deferred        ole32<elf>
  \-PE  7d180000-7d207000       \               ole32
ELF     7d207000-7d239000       Deferred        uxtheme<elf>
  \-PE  7d210000-7d239000       \               uxtheme
ELF     7d4df000-7d4fc000       Deferred        imm32<elf>
  \-PE  7d4f0000-7d4fc000       \               imm32
ELF     7d4fc000-7d502000       Deferred        libxrandr.so.2
ELF     7d502000-7d50a000       Deferred        libxrender.so.1
ELF     7d50a000-7d50d000       Deferred        libxinerama.so.1
ELF     7dc67000-7e5ff000       Deferred        libglcore.so.1
ELF     7e5ff000-7e695000       Deferred        libgl.so.1
ELF     7e695000-7e786000       Deferred        libx11.so.6
ELF     7e786000-7e794000       Deferred        libxext.so.6
ELF     7e7a2000-7e831000       Deferred        winex11<elf>
  \-PE  7e7b0000-7e831000       \               winex11
ELF     7e8aa000-7e8ca000       Deferred        libexpat.so.1
ELF     7e8ca000-7e8f5000       Deferred        libfontconfig.so.1
ELF     7e8f5000-7e909000       Deferred        libz.so.1
ELF     7e909000-7e973000       Deferred        libfreetype.so.6
ELF     7e973000-7e986000       Deferred        libresolv.so.2
ELF     7e986000-7e9a4000       Deferred        iphlpapi<elf>
  \-PE  7e990000-7e9a4000       \               iphlpapi
ELF     7e9a4000-7e9d1000       Deferred        ws2_32<elf>
  \-PE  7e9b0000-7e9d1000       \               ws2_32
ELF     7e9d1000-7e9eb000       Deferred        wsock32<elf>
  \-PE  7e9e0000-7e9eb000       \               wsock32
ELF     7e9eb000-7e9ff000       Deferred        lz32<elf>
  \-PE  7e9f0000-7e9ff000       \               lz32
ELF     7e9ff000-7ea19000       Deferred        version<elf>
  \-PE  7ea10000-7ea19000       \               version
ELF     7ea19000-7ea4c000       Deferred        winspool<elf>
  \-PE  7ea20000-7ea4c000       \               winspool
ELF     7ea4c000-7eb09000       Deferred        comctl32<elf>
  \-PE  7ea60000-7eb09000       \               comctl32
ELF     7eb09000-7eba1000       Deferred        gdi32<elf>
  \-PE  7eb20000-7eba1000       \               gdi32
ELF     7eba1000-7ecde000       Deferred        user32<elf>
  \-PE  7ebc0000-7ecde000       \               user32
ELF     7ecde000-7ed37000       Deferred        shlwapi<elf>
  \-PE  7ecf0000-7ed37000       \               shlwapi
ELF     7ed37000-7ee35000       Deferred        shell32<elf>
  \-PE  7ed50000-7ee35000       \               shell32
ELF     7ee35000-7eed6000       Deferred        comdlg32<elf>
  \-PE  7ee40000-7eed6000       \               comdlg32
ELF     7eed6000-7ef1e000       Deferred        advapi32<elf>
  \-PE  7eee0000-7ef1e000       \               advapi32
ELF     7ef1e000-7ef85000       Deferred        msvcrt<elf>
  \-PE  7ef30000-7ef85000       \               msvcrt
ELF     7ef85000-7ef9f000       Deferred        crtdll<elf>
  \-PE  7ef90000-7ef9f000       \               crtdll
ELF     7ef9f000-7efaa000       Deferred        libnss_files.so.2
ELF     7efaa000-7efb4000       Deferred        libnss_nis.so.2
ELF     7efb4000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff2000-7eff7000       Deferred        libxdmcp.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     f7ca2000-f7ca6000       Deferred        libdl.so.2
ELF     f7ca6000-f7de7000       Deferred        libc.so.6
ELF     f7de8000-f7dff000       Deferred        libpthread.so.0
ELF     f7dff000-f7e01000       Deferred        libnvidia-tls.so.1
ELF     f7e01000-f7e04000       Deferred        libxau.so.6
ELF     f7e0d000-f7f21000       Deferred        libwine.so.1
ELF     f7f23000-f7f41000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
00000008 (D) C:\Program Files\Warcraft II BNE\Warcraft II BNE.exe
        00000010    2
        0000000f   15
        0000000e   15
        0000000c    1
        00000009    0 <==

```

---

