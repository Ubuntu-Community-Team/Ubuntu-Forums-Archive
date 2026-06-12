---
title: "Goonzu with Wine"
date: 2007-06-19
forum: Wine
---

### Post by liquidfunk on 2007-06-19
Right, I'm having some problems using Goonzu with wine. I installed it fine and its installed into "/root/.wine/drive_c/Program Files/NDOORS/GoonzuEng" 

 When I try  $ wine "/root/.wine/drive_c/Program Files/NDOORS/GoonzuEng/goonzu.exe". It just gives me an error. What am I doing wrong? I'm used to using Crossover. 

 Any ideas?

---

### Post by cogadh on 2007-06-19
What's the error?

Also, I think the command should be
```
wine "C:\Program Files\NDOORS\GoonzuEng\goonzu.exe"
```
If you put the path in quotes, you can use the Windows environment path, not the Linux path.

---

### Post by liquidfunk on 2007-06-19
Well I got that from the WineHQ how to.

 I get this when I type my code in:- 

root@liquidfunk-desktop:/home/liquidfunk# $ wine "/root/.wine/drive_c/Program Files/NDOORS/GoonzuEng/goonzu.exe"
bash: $: command not found

 When I type yours in:- 

root@liquidfunk-desktop:/home/liquidfunk# wine "C:\Program Files\NDOORS\GoonzuEng\goonzu.exe"
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b

 (Then a pop-up saying Load helmet.txt error). 

 Followed by:- 

 root@liquidfunk-desktop:/home/liquidfunk# wine "C:\Program Files\NDOORS\GoonzuEng\goonzu.exe"
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
wine: Unhandled page fault on read access to 0x00000380 at address 0x43dfef (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000380 in 32-bit code (0x0043dfef).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0043dfef ESP:0033fdfc EBP:007a2e00 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:7c369cb2 EDX:017b27cc
 ESI:01408b64 EDI:0033fe50
Stack dump:
0x0033fdfc:  01408b4c 007a2e00 0033ff08 00000000
0x0033fe0c:  00000000 00000000 00000000 00000000
0x0033fe1c:  00000000 00000000 00000000 00000000
0x0033fe2c:  00000000 00000000 00000000 00000000
0x0033fe3c:  00000000 00000000 00000000 00000000
0x0033fe4c:  00000000 c0889d9f 0043e577 7b862060
Backtrace:
=>1 0x0043dfef in goonzu (+0x3dfef) (0x007a2e00)
  2 0x00000000 (0x00000000)
0x0043dfef: cmpl        $1,0x380(%eax)
Modules:
Module  Address                 Debug info      Name (101 modules)
PE        340000-  34d000       Deferred        ogg
PE        400000- 1474000       Export          goonzu
PE      10000000-100e3000       Deferred        openal32
PE      60000000-6005d000       Deferred        ijl15
PE      76080000-760d0000       Deferred        winhttp
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7c835000-7c883000       Deferred        libgcrypt.so.11
ELF     7c883000-7c8b1000       Deferred        libcrypt.so.1
ELF     7c8b1000-7c920000       Deferred        libgnutls.so.13
ELF     7c920000-7c94f000       Deferred        libcups.so.2
ELF     7ce57000-7ce5b000       Deferred        libgpg-error.so.0
ELF     7ce5b000-7ce6e000       Deferred        libtasn1.so.3
ELF     7ce98000-7ceca000       Deferred        uxtheme<elf>
  \-PE  7cea0000-7ceca000       \               uxtheme
ELF     7ceca000-7cedf000       Deferred        midimap<elf>
  \-PE  7ced0000-7cedf000       \               midimap
ELF     7cedf000-7cf05000       Deferred        msacm32<elf>
  \-PE  7cef0000-7cf05000       \               msacm32
ELF     7cf05000-7cf1d000       Deferred        msacm32<elf>
  \-PE  7cf10000-7cf1d000       \               msacm32
ELF     7cf1d000-7cf59000       Deferred        wineoss<elf>
  \-PE  7cf20000-7cf59000       \               wineoss
ELF     7cf5b000-7cf60000       Deferred        libxfixes.so.3
ELF     7cf60000-7cf69000       Deferred        libxcursor.so.1
ELF     7cf69000-7cf87000       Deferred        ximcp.so.2
ELF     7cf87000-7cf89000       Deferred        xlcutf8load.so.2
ELF     7cf8c000-7cf94000       Deferred        libxrender.so.1
ELF     7df94000-7e1bf000       Deferred        i915_dri.so
ELF     7e1bf000-7e1c6000       Deferred        libdrm.so.2
ELF     7e1c6000-7e235000       Deferred        libgl.so.1
ELF     7e235000-7e2c4000       Deferred        winex11<elf>
  \-PE  7e240000-7e2c4000       \               winex11
ELF     7e2c4000-7e2e2000       Deferred        libexpat.so.1
ELF     7e2e2000-7e311000       Deferred        libfontconfig.so.1
ELF     7e311000-7e325000       Deferred        libz.so.1
ELF     7e325000-7e38f000       Deferred        libfreetype.so.6
ELF     7e38f000-7e3f4000       Deferred        msvcrt<elf>
  \-PE  7e3a0000-7e3f4000       \               msvcrt
ELF     7e3f4000-7e411000       Deferred        imm32<elf>
  \-PE  7e400000-7e411000       \               imm32
ELF     7e411000-7e431000       Deferred        mpr<elf>
  \-PE  7e420000-7e431000       \               mpr
ELF     7e431000-7e47a000       Deferred        wininet<elf>
  \-PE  7e440000-7e47a000       \               wininet
ELF     7e47a000-7e4ad000       Deferred        winspool<elf>
  \-PE  7e480000-7e4ad000       \               winspool
ELF     7e4ad000-7e506000       Deferred        shlwapi<elf>
  \-PE  7e4c0000-7e506000       \               shlwapi
ELF     7e506000-7e603000       Deferred        shell32<elf>
  \-PE  7e520000-7e603000       \               shell32
ELF     7e603000-7e6a4000       Deferred        comdlg32<elf>
  \-PE  7e610000-7e6a4000       \               comdlg32
ELF     7e6a4000-7e761000       Deferred        comctl32<elf>
  \-PE  7e6b0000-7e761000       \               comctl32
ELF     7e761000-7e78d000       Deferred        ws2_32<elf>
  \-PE  7e770000-7e78d000       \               ws2_32
ELF     7e78d000-7e81b000       Deferred        winmm<elf>
  \-PE  7e7a0000-7e81b000       \               winmm
ELF     7e81b000-7e864000       Deferred        dsound<elf>
  \-PE  7e820000-7e864000       \               dsound
ELF     7e864000-7e869000       Deferred        libxdmcp.so.6
ELF     7e869000-7e86c000       Deferred        libxau.so.6
ELF     7e86c000-7e935000       Deferred        libx11.so.6
ELF     7e935000-7e942000       Deferred        libxext.so.6
ELF     7e942000-7e947000       Deferred        libxxf86vm.so.1
ELF     7e947000-7e95f000       Deferred        libice.so.6
ELF     7e95f000-7e9b3000       Deferred        ddraw<elf>
  \-PE  7e970000-7e9b3000       \               ddraw
ELF     7e9b3000-7e9c6000       Deferred        libresolv.so.2
ELF     7e9c6000-7e9e4000       Deferred        iphlpapi<elf>
  \-PE  7e9d0000-7e9e4000       \               iphlpapi
ELF     7e9e4000-7ea39000       Deferred        rpcrt4<elf>
  \-PE  7e9f0000-7ea39000       \               rpcrt4
ELF     7ea39000-7ea44000       Deferred        libgcc_s.so.1
ELF     7ea46000-7ea4f000       Deferred        libsm.so.6
ELF     7eb2e000-7ebe9000       Deferred        gdi32<elf>
  \-PE  7eb40000-7ebe9000       \               gdi32
ELF     7ebe9000-7ed24000       Deferred        user32<elf>
  \-PE  7ec00000-7ed24000       \               user32
ELF     7ed24000-7edc2000       Deferred        ole32<elf>
  \-PE  7ed30000-7edc2000       \               ole32
ELF     7edc2000-7ee5d000       Deferred        oleaut32<elf>
  \-PE  7edd0000-7ee5d000       \               oleaut32
ELF     7ee5d000-7eea4000       Deferred        advapi32<elf>
  \-PE  7ee70000-7eea4000       \               advapi32
ELF     7efae000-7efb9000       Deferred        libnss_files.so.2
ELF     7efb9000-7efcf000       Deferred        libnsl.so.1
ELF     7efcf000-7eff5000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ca6000-b7caf000       Deferred        libnss_compat.so.2
ELF     b7cb0000-b7cb4000       Deferred        libdl.so.2
ELF     b7cb4000-b7de8000       Deferred        libc.so.6
ELF     b7de9000-b7dfc000       Deferred        libpthread.so.0
ELF     b7e07000-b7f1b000       Deferred        libwine.so.1
ELF     b7f1d000-b7f38000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\NDOORS\GoonzuEng\goonzu.exe
        00000009    0 <==

---

### Post by cogadh on 2007-06-19
Do you have 3D accelerated drivers for your video card installed?

Also, I just noticed the "root" reference in your command entry. Applications you install through Wine install in your home folder, not in the root home folder. That is likely why the command you used didn't work.

---

### Post by liquidfunk on 2007-06-19
Ok, well I'm assuming my graphics card drivers have already been installed as I have been able to play games well enough.

 When I installed Wine it went into the root folder. So did the game.

 How do I change this?

---

### Post by liquidfunk on 2007-06-19
Oh also its an Intel 82865G Integrated Graphics card.

---

### Post by cogadh on 2007-06-19
Did you run "winecfg" immediately after installing Wine? Did you use "sudo" to run it? If so, that is likely where things have gone wrong. You should not use sudo to run wine commands.

Even if you did not use sudo, I would suggest that you wipe out your current Wine install and start fresh. Something is not quite right about your setup. You will need to manually delete the fake Windows directory from root's home directory:
```
sudo rm -d -r /root/.wine
```
Then re-run "winecfg" (without the sudo) to create a new fake Windows directory in your home folder. When you run winecfg, go to the Drives tab and autodetect your drives, then go to the Graphics tab and check the "Emulate a virtual desktop" option. Set the size to a standard size that is smaller than your full screen resolution. Now when you launch applications through Wine, they will be contained in a virtual desktop, which can assist in the troubleshooting process.

Once you have done that, re-install the application and try running it. If it produces the same error then we need to start looking at your graphics hardware setup.

---

### Post by liquidfunk on 2007-06-29
Ok done and done.

 Installed the latest Wine. Installed Goonzu. Now I get the error Load helmet.txt error?

 Any ideas?

 Have posted this one the WineHQ too.

---

### Post by cogadh on 2007-06-29
Well, I looked up the AppDB entry for this game and one of the people there recommended adding "WINEBUBUG='-all' & nice -20" to the launch command:
```
wine WINEBUBUG='-all' & nice -20 "C:\Program Files\NDOORS\GoonzuEng\goonzu.exe"
```
Also, did you ever determine if you installed your correct video drivers? I know you said you had played some games already, but the default drivers for both ATI and Nvidia cards don't support full 3D acceleration (not sure about the Intel driver). That LibGL warning you got before could be an indication that you do not have the accelerated 3D driver installed.

---

### Post by liquidfunk on 2007-06-29
Hmmm..
 
 Well in another of my posts I asked about my graphics card, saying that it was working quite slowly. The person who helped me did quite a lot for me. In the end it said that Direct rendering was on. So I assume that its working.

 I shall try the code you gave me when I get home. Cheers.

---

### Post by hikaricore on 2007-06-29
One thing that I don't think has been mentioned.

The i810 drivers are notorious for working well with some games and terribly with others.
This is no fault of Ubuntu/Linux, but the responsibility falls on Intel for not developing the drivers very well
then abandoning them officially leaving it up to the Linux community to try and make them equal to their
***dows counterpart.  I hope this may help in some way even if it's not what you wanted to hear.

---

### Post by liquidfunk on 2007-06-29
Hmm.. Well it worked very well on Windows 2000. So I'm hoping it will work on this. If not, I have an older nvidia card with 64mb that could be installed. Just needs to be configured.

---

### Post by hikaricore on 2007-06-29
Like I said the ***dows drivers were created more reliably than the drivers Intel made for Linux.

You may want to check to see if the Nvidia card is supported by the binary drivers: [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

And if it is, go for it.  ^_^

---

### Post by liquidfunk on 2007-07-03
Sadly your code didn't work (wine WINEBUBUG='-all' & nice -20 "C:\Program Files\NDOORS\GoonzuEng\goonzu.exe").

 I must be doing something wrong. The processes I do are as follows.

 Get wine: Sudo apt-get install wine

 Configure: Winecfg

 Find the installer and install: cd .. 
                                               cd /home/liquidfunk/desktop/ 
                                               wine goonzueng.exe 
 
 Then it installs fine.

 Open it up: Do I install the HTML reader or not?

 Anything I'm missing?

 I'm know for sure Goonzu works, I've seen screenshots and videos. I must be going through a noob patch.

---

### Post by joojle on 2007-07-27
liquidfunk:
I just click yes to let wine download gecko html render engine
--------------------------
Now Goonzu can run on my kubuntu 7.04 but I also have a problem with login. I click login button it show message "Now have Loged in to front server" but it does not show server select dialog. What should i do next.

---

### Post by liquidfunk on 2007-08-16
Starting to look up a bit.

 Installed, Opened up, it gives me an error message, but there are no fonts. 

 I installed Gecko and it says that the Goonzu site cannot be found. Then it closes shortly after.

 Heres a screenie.

---

### Post by liquidfunk on 2007-08-18
Bump! :confused:

---

### Post by wisedrunkard on 2009-01-07
Bump

---

