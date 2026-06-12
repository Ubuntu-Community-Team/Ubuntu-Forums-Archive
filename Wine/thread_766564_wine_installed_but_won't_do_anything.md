---
title: "wine installed but won't do anything"
date: 2008-04-25
forum: Wine
---

### Post by wildman4god on 2008-04-25
i installed wine on y ubuntu 7.10 laptop but when i go to install a windows program like packet tracer it won't do anything, it won't install, i can't bring up the wine config or even uninstall it. some one help me please.

---

### Post by bmwman on 2008-04-25
I have the same problem. It was working fine when I hat Ubuntu 7.10 but now i'm using 8.04 on a different computer and get install any windows stuff. I need to run few work apps which used to work before. Installin wine goes flawless but can do anything with it.

---

### Post by cogadh on 2008-04-25
We need more details, like how are you trying to run the installs and what, if any, error output are you getting in the terminal when you try to do things like winecfg.

---

### Post by wildman4god on 2008-04-25
like i said it does literly nothing, i right click the exe to choose open with wine and it just sits there like i don't have the program installed, so i go to the aplications menu and select wine>wineconfig and again it does nothing, i even check the system monitor to see if its running and its not. no error just acts like i didn't click on anything, i cans till do everything else on linux fine but not wine

---

### Post by cogadh on 2008-04-25
You need to use the terminal to run Wine, not the mostly useless GUI tools, i.e. open a terminal and type "winecfg" or "wine foo.exe". That way you will get error output in the terminal that might tell you what is going on.

---

### Post by bmwman on 2008-04-25
Here is what i get 
bmw-man@bmw-man-laptop:~$ wine /home/bmw-man/Desktop/Vantive/setup.exepreloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
winevdm: unable to exec 'Y:\Desktop\Vantive\setup.exe': DOS memory range unavailable

I've had this program working before. Don't know what's the problem now. BTW i tried wine-0.9.59 and wine-0.9.60 and same thing.

---

### Post by cogadh on 2008-04-25
That's a problem that was caused by changes made to the sysctl file to protect the first 64k of kernel memory from potential security risks. The change appears to affect the way Wine works with 8 and 16 bit applications. You can undo the change by running this:
```
sudo sysctl -w vm.mmap_min_addr=0
```

---

### Post by bmwman on 2008-04-25
Great!! That worked. I was able to install. Now the program doesn't appear in the menu tho. Also I remember i was able to right click on a setup file and there was an option to install with wine. Any way I can fix that too? I do get the option "run with Crossover" but some apps don't work with crossover and run with wine.

Thanks for all the help :)

---

### Post by bmwman on 2008-04-25
Great!! That worked. I was able to install. Now the program doesn't appear in the menu tho. Also I remember i was able to right click on a setup file and there was an option to install with wine. Any way I can fix that too? I do get the option "run with Crossover" but some apps don't work with crossover and run with wine.

Thanks for all the help

---

### Post by wildman4god on 2008-04-25
i get this:

wine: creating configuration directory '/home/joshua/.wine'...
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Intel 82801DB-ICH4 Modem, disabling mixer
Could not load Mozilla. HTML rendering will be disabled.
err:seh:setup_exception_record stack overflow 28 bytes in thread 0009 eip 7e096153 esp 00231314 stack 0x230000-0x231000-0x330000
wine: wineprefixcreate failed while creating '/home/joshua/.wine'.
joshua@joshua-laptop:~$ wineserver: could not save registry branch to /home/joshua/.wine-kgfk0Z/system.reg : No such file or directory
wineserver: could not save registry branch to /home/joshua/.wine-kgfk0Z/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/joshua/.wine-kgfk0Z/user.reg : No such file or directory

---

### Post by cogadh on 2008-04-25
I think it would be best for you to start from scratch. Completely remove Wine with this terminal command:
```
sudo apt-get remove --purge wine
```
The open you home folder and show hidden files. Look for any files that start with .wine (there will likely be a few files with names like ".wine_bLaH") and delete them. After that, reinstall Wine and run winecfg (again, from the terminal, not with the GUI tool). If it still errors out, post the error messages again.
> **bmwman said:**
> Great!! That worked. I was able to install. Now the program doesn't appear in the menu tho. Also I remember i was able to right click on a setup file and there was an option to install with wine. Any way I can fix that too? I do get the option "run with Crossover" but some apps don't work with crossover and run with wine.

Thanks for all the help :)
I completely forgot that the command I gave you will reset itself at the next reboot. If you want to set that permanently, follow the instructions here:
http://wiki.winehq.org/PreloaderPageZeroProblem
As for the right-click issue, do you have the binfmt-support package installed? It should be installed before Wine to allow the Wine package to make the necessary file associations with .exe files. The application menu thing is a frequently recurring bug, but I've never seen a real solution for it.

---

### Post by marcw on 2008-04-29
> **cogadh said:**
> You can undo the change by running this:
```
sudo sysctl -w vm.mmap_min_addr=0
```

Thanks, that works great!  As an added benefit, using the same code I can now run my old 16bit DOS game in both my 32bit and 64bit Hardy!  (I was told that I wouldn't be able to under 64bit).

Since you mentioned that this change was a security risk, I wrote a script that uses your code to run my game but return things back to normal when done.

```
#!/bin/sh
sudo sysctl -w vm.mmap_min_addr=0
cd "/the/full/path/to/my/16bit/game/"
wine my_16bit_game.exe
sudo sysctl -w vm.mmap_min_addr=65536
exit
```

---

### Post by thornlord on 2008-04-30
Hi all,

I am also having problems running wine.  I am not certain wine has worked since I installed 7.10 but I've uninstalled and re-installed as per the instructions and here is the output of my attempt to run $winecfg

> sean@buddhist:~$ sudo winecfg
wine: creating configuration directory '/home/sean/.wine'...
wine: Unhandled illegal instruction at address 0x7e54f350 (thread 0009), starting debugger...
Unhandled exception: illegal instruction in 32-bit code (0x7e54f350).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e54f350 ESP:0033e490 EBP:00000050 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000001 EBX:00000040 ECX:7c032860 EDX:7d4fd000
 ESI:7c032860 EDI:7d4fd000
Stack dump:
0x0033e490:  7d4fd000 00000000 00000000 00000000
0x0033e4a0:  00000010 00000000 00000000 7d4fd000
0x0033e4b0:  7c0b9c60 00000050 7d712330 7e5307b2
0x0033e4c0:  7d4fd000 7c032860 00000050 00000006
0x0033e4d0:  000e1500 7e533f80 00000000 00000000
0x0033e4e0:  00000056 7c032860 0ffbd000 00000000
Backtrace:
=>1 0x7e54f350 in libglcore.so.1 (+0x7da350) (0x00000050)
  2 0x00000000 (0x00000000)
0x7e54f350: 
Modules:
Module  Address                 Debug info      Name (39 modules)
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dd73000-7dd75000       Deferred        libnvidia-tls.so.1
ELF     7dd75000-7e88a000       Export          libglcore.so.1
ELF     7e88a000-7e92e000       Deferred        libgl.so.1
ELF     7e92e000-7e933000       Deferred        libxdmcp.so.6
ELF     7e933000-7e936000       Deferred        libxau.so.6
ELF     7e936000-7ea27000       Deferred        libx11.so.6
ELF     7ea27000-7ea35000       Deferred        libxext.so.6
ELF     7ea35000-7ea3a000       Deferred        libxxf86vm.so.1
ELF     7ea3a000-7ea52000       Deferred        libice.so.6
ELF     7ea52000-7ea5a000       Deferred        libsm.so.6
ELF     7ea6b000-7eaf6000       Deferred        winex11<elf>
  \-PE  7ea80000-7eaf6000       \               winex11
ELF     7eb70000-7eb90000       Deferred        libexpat.so.1
ELF     7eb90000-7ebbb000       Deferred        libfontconfig.so.1
ELF     7ebbb000-7ebd0000       Deferred        libz.so.1
ELF     7ebd0000-7ec40000       Deferred        libfreetype.so.6
ELF     7ec51000-7ec9a000       Deferred        advapi32<elf>
  \-PE  7ec60000-7ec9a000       \               advapi32
ELF     7ec9a000-7ed35000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed35000       \               gdi32
ELF     7ed35000-7ee73000       Deferred        user32<elf>
  \-PE  7ed50000-7ee73000       \               user32
ELF     7ee73000-7ee88000       Deferred        rundll32<elf>
  \-PE  7ee80000-7ee88000       \               rundll32
ELF     7efa7000-7efb2000       Deferred        libnss_files.so.2
ELF     7efb2000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7efef000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cf4000-b7cfd000       Deferred        libnss_compat.so.2
ELF     b7cfe000-b7d02000       Deferred        libdl.so.2
ELF     b7d02000-b7e4c000       Deferred        libc.so.6
ELF     b7e4c000-b7e64000       Deferred        libpthread.so.0
ELF     b7e75000-b7f89000       Deferred        libwine.so.1
ELF     b7f8b000-b7fa7000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\rundll32.exe
        00000009    0 <==
wine: wineprefixcreate failed while creating '/home/sean/.wine'.
sean@buddhist:~$ wineserver: could not save registry branch to /home/sean/.wine-4TvPNb/system.reg : No such file or directory
wineserver: could not save registry branch to /home/sean/.wine-4TvPNb/user.reg : No such file or directory

---

### Post by cogadh on 2008-04-30
This one is easy:
```
sean@buddhist:~$ sudo winecfg
```
NEVER RUN WINE USING SUDO OR WITH ROOT PERMISSIONS!

Wine is only meant to be run as a normal user. Using sudo or a root account to run Wine screws up the permissions on the .wine directory (best case scenario) and allows Windows applications, including viruses, access to the entire Linux system (worst case scenario). You need to delete your existing .wine directory with this command:
```
sudo rm -r ~/.wine
```
Then create a new .wine directory the correct way:
```
winecfg  <---just "winecfg", no "sudo"
```

---

### Post by WebWatch on 2008-05-16
```
#!/bin/sh
sudo sysctl -w vm.mmap_min_addr=0
cd "/the/full/path/to/my/16bit/game/"
wine my_16bit_game.exe
sudo sysctl -w vm.mmap_min_addr=65536
exit
```[/QUOTE]
 
I've been trying to get this script to work with Dos Emulator

So far my .sh file contains

#!/bin/sh
sudo sysctl -w vm.mmap_min_addr=0
password
cd "/the/full/path/to/my/16bit/program/"
dosemu my_16bit_program.exe
sudo sysctl -w vm.mmap_min_addr=65536
password
exit

this will launch dosemu and then close it without launching my exe file

---

### Post by marcw on 2008-05-16
Sorry, don't know anything about dosemu, but have you tried running those commands one at a time in a terminal?

---

