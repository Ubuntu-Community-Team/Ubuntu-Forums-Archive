---
title: "Error in Wine when trying to play System Shock 2"
date: 2008-01-04
forum: Wine
---

### Post by BnetTheAwesome on 2008-01-04
I got the Home of the Underdogs version and used the command: 
wine "Shock2.exe"

And got this:

fixme:win:EnumDisplayDevicesW ((null),0,0x32f8ac,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x128298)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x128298)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x128298)->((nil),00000008)
wine: Unhandled page fault on read access to 0x00000000 at address 0x594937 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00594937).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00594937 ESP:0032fbc0 EBP:00b78680 EFLAGS:00010216(   - 00      -RIAP1)
 EAX:00000000 EBX:00000000 ECX:00657c48 EDX:006af3dc
 ESI:00b7ca94 EDI:00000016
Stack dump:
0x0032fbc0:  00000016 00b7b270 00000000 0054a323
0x0032fbd0:  00000016 0000000a 00000190 0058ece8
0x0032fbe0:  00000016 0000000a 00000030 00b83798
0x0032fbf0:  00b78680 00628d26 00628d42 0075dd70
0x0032fc00:  00ba0950 0065c6f1 00b7d99c 006470c8
0x0032fc10:  00b7bd30 00b7dfcc 00ba144c 00b7bd30
Backtrace:
=>1 0x00594937 in shock2 (+0x194937) (0x00b78680)
  2 0x00b78c48 (0x00650eb0)
  3 0x0040a680 in shock2 (+0xa680) (0x00432540)
  4 0x0c24548b (0x0424448b)
  5 0x00000000 (0x00000000)
0x00594937: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (72 modules)
PE        400000-  83e000       Export          shock2
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d84f000-7d883000       Deferred        dplayx<elf>
  \-PE  7d860000-7d883000       \               dplayx
ELF     7d984000-7d9ba000       Deferred        dinput<elf>
  \-PE  7d990000-7d9ba000       \               dinput
ELF     7db45000-7dc25000       Deferred        wined3d<elf>
  \-PE  7db60000-7dc25000       \               wined3d
ELF     7dc25000-7dc7a000       Deferred        ddraw<elf>
  \-PE  7dc30000-7dc7a000       \               ddraw
ELF     7dc7a000-7dcc4000       Deferred        dsound<elf>
  \-PE  7dc80000-7dcc4000       \               dsound
ELF     7dcc4000-7dcd9000       Deferred        midimap<elf>
  \-PE  7dcd0000-7dcd9000       \               midimap
ELF     7dcd9000-7dd00000       Deferred        msacm32<elf>
  \-PE  7dce0000-7dd00000       \               msacm32
ELF     7dd00000-7dd18000       Deferred        msacm32<elf>
  \-PE  7dd10000-7dd18000       \               msacm32
ELF     7dd18000-7dd52000       Deferred        wineoss<elf>
  \-PE  7dd20000-7dd52000       \               wineoss
ELF     7dd52000-7dd57000       Deferred        libxfixes.so.3
ELF     7dd57000-7dd60000       Deferred        libxcursor.so.1
ELF     7dd60000-7dd7d000       Deferred        imm32<elf>
  \-PE  7dd70000-7dd7d000       \               imm32
ELF     7dd7d000-7dd83000       Deferred        libxrandr.so.2
ELF     7dd83000-7dd8b000       Deferred        libxrender.so.1
ELF     7dd93000-7dd9e000       Deferred        libgcc_s.so.1
ELF     7e480000-7e6f5000       Deferred        r200_dri.so
ELF     7e6f5000-7e6ff000       Deferred        libdrm.so.2
ELF     7e6ff000-7e75f000       Deferred        libgl.so.1
ELF     7e75f000-7e764000       Deferred        libxdmcp.so.6
ELF     7e764000-7e767000       Deferred        libxau.so.6
ELF     7e767000-7e858000       Deferred        libx11.so.6
ELF     7e858000-7e866000       Deferred        libxext.so.6
ELF     7e866000-7e86b000       Deferred        libxxf86vm.so.1
ELF     7e86b000-7e883000       Deferred        libice.so.6
ELF     7e883000-7e88b000       Deferred        libsm.so.6
ELF     7e8a0000-7e92b000       Deferred        winex11<elf>
  \-PE  7e8b0000-7e92b000       \               winex11
ELF     7e9c4000-7e9e4000       Deferred        libexpat.so.1
ELF     7e9e4000-7ea0f000       Deferred        libfontconfig.so.1
ELF     7ea0f000-7ea24000       Deferred        libz.so.1
ELF     7ea24000-7ea94000       Deferred        libfreetype.so.6
ELF     7ea94000-7eaa7000       Deferred        libresolv.so.2
ELF     7eabc000-7eada000       Deferred        iphlpapi<elf>
  \-PE  7eac0000-7eada000       \               iphlpapi
ELF     7eada000-7eb33000       Deferred        rpcrt4<elf>
  \-PE  7eaf0000-7eb33000       \               rpcrt4
ELF     7eb33000-7ebd4000       Deferred        ole32<elf>
  \-PE  7eb40000-7ebd4000       \               ole32
ELF     7ebd4000-7ec62000       Deferred        winmm<elf>
  \-PE  7ebe0000-7ec62000       \               winmm
ELF     7ec62000-7ecab000       Deferred        advapi32<elf>
  \-PE  7ec70000-7ecab000       \               advapi32
ELF     7ecab000-7ed46000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed46000       \               gdi32
ELF     7ed46000-7ee84000       Deferred        user32<elf>
  \-PE  7ed60000-7ee84000       \               user32
ELF     7efa3000-7efae000       Deferred        libnss_files.so.2
ELF     7efae000-7efc6000       Deferred        libnsl.so.1
ELF     7efc6000-7efeb000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c91000-b7c95000       Deferred        libdl.so.2
ELF     b7c95000-b7ddf000       Deferred        libc.so.6
ELF     b7de0000-b7df8000       Deferred        libpthread.so.0
ELF     b7e0d000-b7f21000       Deferred        libwine.so.1
ELF     b7f23000-b7f3f000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\bnet\Shock2.exe
        0000000d    0
        00000009    0 <==

Any ideas?

---

### Post by BnetTheAwesome on 2008-01-04
New development.

I enter this into the terminal:

cd "/home/bnet/.wine/drive_c/Program Files/sysshock2 "

then; wine "Shock2.exe"

It went to the main menu. My cursor kept blinking. I was able to click "New Game" and "Start Game" then it went back to the desktop with the screen really large.

Any solutions?

---

### Post by BnetTheAwesome on 2008-01-04
Can anyone help?

---

### Post by BnetTheAwesome on 2008-01-04
Can anyone help me at all. I followed the readme. I'm a noob who just wants to play SS2. Anyone who can help me with this "modules" problem would be greatly appreciated.

---

### Post by BnetTheAwesome on 2008-01-04
I'll post the readme for anyone who wants to know:

Before you play:

  Run sshock2.exe and chose a directory to install the game to.

  Run OggSetup.exe to prepare the game data.  

  After that, there should be two new files, 

  snd.crf with about 140 MB and snd2.crf with about 120MB.

  Then you can delete OggSetup.exe, LibSndFile.dll, OggDecoder.dll,

  snd_crf.bla and snd2_crf.bla, as the game doesn't need these files.

  Start the game with shock2.exe.

---

### Post by PhutterMan on 2008-01-04
I haven't done the OggSetup thing.  Is that necessary, or is it (as I think I've heard) just for the cutscenes (I don't mind viewing them out of the game)?

I get a very similar error with 'fixme' about some ddraw things and then the page fault.  When I started from other than the sshock2 directory the page fault was at 0x00000000.  After cd'ing to the directory, the page fault was at 0x08ebb37c.  Also, the 'backtrace' section was much longer and referred a great deal to 'ntdll'.

Still, the end result was the same. No System Shock for me.

---

### Post by PhutterMan on 2008-01-04
Oh, I just had a thought.

Have you No-CD patched yours?  I believe that's necessary, as is patching to 2.3.
If you haven't done those, they might do the trick for you.

I don't know where that leaves me, though, as I have done those things.  Still, perhaps the OggSetup will help?

Unfortunately, I have no idea how to interpret Wine's errors.

---

### Post by BnetTheAwesome on 2008-01-04
Is the problem fixable? Is there anything that can be done?

---

### Post by BnetTheAwesome on 2008-01-04
One thing I dislike about these forums is how ineffective my forum posts are. My threads get little views and little responses. Why am I always predisposed? :(

---

### Post by BnetTheAwesome on 2008-01-04
> **PhutterMan said:**
> Oh, I just had a thought.

Have you No-CD patched yours?  I believe that's necessary, as is patching to 2.3.
If you haven't done those, they might do the trick for you.

I don't know where that leaves me, though, as I have done those things.  Still, perhaps the OggSetup will help?

Unfortunately, I have no idea how to interpret Wine's errors.

No-CD? Where/How can I patch this?

---

### Post by BnetTheAwesome on 2008-01-04
Does anyone know how I can patch it?

---

### Post by PhutterMan on 2008-01-04
Get a no-cd crack from a site like gamecopyworld.  They're fixed exe's that you replace SHOCK2.EXE with in the game directory.  Apparently Wine can't do safedisc, so even if you've got a legitimate disc you have to do a full install and use a no-cd crack.

So...maybe that'll do it, since that's the only necessary step (as far as I can tell) you haven't done.  You should patch the game (shkpatch.exe) to the newest version, 2.3, before trying a no-cd crack.

In my case, I haven't done the OggSetup thing, and that's my only hope at this point, I think.  I don't know.  I hope it isn't something to do with my exceedingly weak laptop's graphics card, though it does pass all the tests on dxdiag, albeit slowly.

---

### Post by BnetTheAwesome on 2008-01-04
I'll try that.

---

### Post by BnetTheAwesome on 2008-01-04
Doesn't appear to do much. Says "Already Patched or not able to patch". I think the Underdogs version is prepatched right? Anyone got any suggestions?

---

### Post by Faud on 2008-01-05
What version of WINE are you using ?

---

### Post by BnetTheAwesome on 2008-01-05
0.9.46

---

### Post by Faud on 2008-01-05
I would try upgrading to 0.9.49..not.52 but .49

---

### Post by BnetTheAwesome on 2008-01-05
How do you upgrade to .49?

---

### Post by Faud on 2008-01-05
[www.winehq.org](www.winehq.org) and follow the instructions

---

### Post by BnetTheAwesome on 2008-01-05
> **Faud said:**
> [www.winehq.org](www.winehq.org) and follow the instructions

I went there and I downloaded the 0.9.49 version in an archive. I don't know what to do. The WINE HQ instructions are vague and confusing. Can you help me?

---

### Post by happyhamster on 2008-01-05
You have downloaded a .deb file, right? If not, get one of those, because they are easiest to work with: just double-click it and an installer will open. But take care of a few things first:

- make sure you got the correct .deb file: it should match your ubuntu-version (Gutsy/Feisty/etc) and architecture (i386=default or AMD64).

- if you have other programs already installed with wine, and you want to keep them, then make a backup of your wine folder just for safety. It's a hidden folder called ".wine" in your home dir.

After installing the .deb, open a terminal and update wine with the commando:

wineprefixcreate

Then run:

winecfg

to check if everything is setup properly.

---

### Post by Faud on 2008-01-05
If you downloaded it you should be able to just double click on it and it will install..it may say that there is a more current one in the repositerys but just say you dont want that one.

Is there a specific place that you are having trouble ?

---

### Post by PhutterMan on 2008-01-05
With regards to running System Shock specifically, I recently found that going into Wine's configuration and checking the box in the Graphics tab to emulate a virtual desktop resulted in System Shock launching fine in a window.

However, it runs extremely slowly (ie, seconds per frame, not frames per second), but nevertheless, it's running, and that was all I changed.  Sound works fine without the OggSetup fix.

As far as the speed goes, my computer is extremely slow (it's my ultraportable, old Compaq Armada).  It's got a PIII 500, 320MB of ram, and an ATI Rage pro LT.  Still, it meets System Shock's requirements.  I will do some reading to see if there's anything I can do to speed it up.

Long story short, try the virtual desktop thing.  That may solve your problem completely, especially if you're on a fast machine.

---

### Post by BnetTheAwesome on 2008-01-05
Actually I got a .tar.bz2 file. Where is the .deb file?

Also, I tried the Virtual Desktop.

---

### Post by noerrorsfound on 2008-04-14
I'm having this same problem, even after using a no-cd and [SS2Tool]("http://www.strangebedfellows.de/index.php/topic,392").

64-bit Ubuntu 7.10 and Wine 0.9.59.

---

### Post by espenhw on 2008-05-02
> **noerrorsfound said:**
> I'm having this same problem, even after using a no-cd and [SS2Tool]("http://www.strangebedfellows.de/index.php/topic,392").

64-bit Ubuntu 7.10 and Wine 0.9.59.

I had the same problem, until I tried cd'ing to the SS2 directory (~/.wine/drive_c/Sshock2 by default) and running SS2 in a virtual desktop (wine explorer /desktop=SS2,800x600 shock2.exe). 

The game then starts, but with no videos and I can't actually start a new game.  Yet...  :)

---

