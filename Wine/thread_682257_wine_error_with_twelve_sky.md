---
title: "wine error with twelve sky"
date: 2008-01-29
forum: Wine
---

### Post by scottc992004 on 2008-01-29
I'm new to Ubuntu 7.10 and wine.
 I installed wine and updated it then installed twelve sky everything went fine. but when i go to wine and click on twleve sky it starts and then an error "patchserverInt" then i clike ok and the game closes.
What could be the problem? and how can i fix it?

---

### Post by stuart.crouch on 2008-01-30
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10215](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10215)

Did you get a native wininet.dll?

This thread has the steps needed to make the game run -
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9857](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9857)

---

### Post by scottc992004 on 2008-01-30
not sure if it has it i'm new to linux so still not 100% sure were to find things in the system folder. But i'll try it when i get home. do i need to do any configuration with wine?

---

### Post by scottc992004 on 2008-01-31
i tried website [http://appdb.winehq.org/objectManage...rsion&iId=9857](http://appdb.winehq.org/objectManage...rsion&iId=9857)

and went to terminal and entered:

wget [http://neocomy.net/files/public/dlls-12sky.zip;unzip](http://neocomy.net/files/public/dlls-12sky.zip;unzip) dlls-12sky.zip -c ~/.wine/drive_c/windows/system32/;rm dlls-12sky.zip

this is what i get:

scott@scott-desktop:~$ wget [http://neocomy.net/files/public/dlls-12sky.zip;unzip](http://neocomy.net/files/public/dlls-12sky.zip;unzip) dlls-12sky.zip -c ~/.wine/drive_c/windows/system32/;rm dlls-12sky.zip
--20:50:53--  [http://neocomy.net/files/public/dlls-12sky.zip](http://neocomy.net/files/public/dlls-12sky.zip)
           => `dlls-12sky.zip'
Resolving neocomy.net... 78.46.32.138
Connecting to neocomy.net|78.46.32.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,427,334 (1.4M) [application/zip]

100%[====================================>] 1,427,334    159.49K/s    ETA 00:00

20:51:15 (66.94 KB/s) - `dlls-12sky.zip' saved [1427334/1427334]

Archive:  dlls-12sky.zip
caution: filename not matched:  -c
caution: filename not matched:  /home/scott/.wine/drive_c/windows/system32/
scott@scott-desktop:


I copied d3dx9_27.dll and wininet.dll into path: /home/scott/.wine/drive_c/windows/system32/
but still get the same error message when i run the game. :(

---

### Post by scottc992004 on 2008-01-31
i forgot  to do :
Now open winecfg Add Launcher.exe and set wininet.dll to native. 

i go into wine config add launcher.exe in application settings (windows 2000), 
libraries tab:
New override for library: wininet but the 3 buttons beside do not work. so i cannot set wininet to native.

---

### Post by scottc992004 on 2008-01-31
one more thing the error is [error :: GetPatchServerInfo ()]

---

### Post by stuart.crouch on 2008-01-31
I've just tried and the command doesnt unzip the files correctly.

Do this instead

[code]
cd ~/.wine/drive_c/windows/system32
wget http://neocomy.net/files/public/dlls-12sky.zip
unzip dlls-12sky.zip ~/.wine/drive_c/windows/system32
rm dlls-12sky.zip
ls -l
[code]

The last command ls -l will give you a directory listing with dates.  The date of the wininet.dll should now read 2001-08-17 21:34

now type winecfg
go over to the libraries tab
click into the new override for library box
type wininet.dll

The add button should become highlighted, Click it
The existing overrides should now have wininet (native, builtin)

If it says something different in brackets, highlight it and click edit, then select it from the options.

Now try launching the game and let us know how you get on.

---

### Post by scottc992004 on 2008-02-01
Thank you stuart.crouch that worked. 

I don't get the error anymore but it flashes downloading, I stop it after 30 minutes. Added a screenshot.

---

### Post by stuart.crouch on 2008-02-01
Is this a game that can be downloaded?  I went to the website but its all in korean(?) or another language that I have no chance of understanding or translating.

I'm happy to have a go at installing it on my system if there is an installer I can get legally.

---

### Post by scottc992004 on 2008-02-01
It's working now just had to wait for an hour before it started to download. thanks for your help.

if you want to try the game here is the website you can get it from

[http://www.aeriagames.com/](http://www.aeriagames.com/)

:)

---

### Post by leandrovargas on 2008-02-09
Hi all. When i try to run he gives me this error:
```
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 17/02/2008, dlt (d/m/y): 12/10/2008
wine: Unhandled page fault on read access to 0xc0001001 at address 0x3b1470 (thread 0014), starting debugger...
Unhandled exception: page fault on read access to 0xc0001001 in 32-bit code (0x003b1470).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:003b1470 ESP:0033fd84 EBP:0033fec4 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000001 EBX:00000000 ECX:c0001001 EDX:00000007
 ESI:c0001000 EDI:003b6374
Stack dump:
0x0033fd84:  003b7a74 0033fe00 003a0000 012e0368
0x0033fd94:  012e0cec 003b3bbb 0033ff20 003b3f4b
0x0033fda4:  0033fec4 003a0000 00340000 003b4138
0x0033fdb4:  00000000 00000000 00000000 00000000
0x0033fdc4:  00000000 00000000 00000000 00000000
0x0033fdd4:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x003b1470 (0x0033fec4)
  2 0x003b26bc (0x0033fee0)
  3 0x00000000 (0x00e55471)
  4 0x5d895b5b (0x5d895b5d)
  5 0x00000000 (0x00000000)
0x003b1470: movb        0x0(%ecx),%cl
Modules:
Module  Address                 Debug info      Name (91 modules)
PE        400000-  e68000       Deferred        twelvesky
PE        e70000- 10bf000       Deferred        d3dx9_27
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c136000-7c168000       Deferred        uxtheme<elf>
  \-PE  7c140000-7c168000       \               uxtheme
ELF     7c168000-7c17c000       Deferred        midimap<elf>
  \-PE  7c170000-7c17c000       \               midimap
ELF     7c17c000-7c1a2000       Deferred        msacm32<elf>
  \-PE  7c180000-7c1a2000       \               msacm32
ELF     7c1a2000-7c1b9000       Deferred        msacm32<elf>
  \-PE  7c1b0000-7c1b9000       \               msacm32
ELF     7d2c5000-7d300000       Deferred        wineoss<elf>
  \-PE  7d2d0000-7d300000       \               wineoss
ELF     7d320000-7d329000       Deferred        libxcursor.so.1
ELF     7d329000-7d346000       Deferred        imm32<elf>
  \-PE  7d330000-7d346000       \               imm32
ELF     7d346000-7d34b000       Deferred        libxfixes.so.3
ELF     7d34b000-7d34e000       Deferred        libxcomposite.so.1
ELF     7d34e000-7d356000       Deferred        libxrender.so.1
ELF     7d8ef000-7d8f1000       Deferred        libnvidia-tls.so.1
ELF     7d8f1000-7e177000       Deferred        libglcore.so.1
ELF     7e177000-7e203000       Deferred        libgl.so.1
ELF     7e203000-7e208000       Deferred        libxdmcp.so.6
ELF     7e208000-7e20b000       Deferred        libxau.so.6
ELF     7e20b000-7e2fc000       Deferred        libx11.so.6
ELF     7e2fc000-7e30a000       Deferred        libxext.so.6
ELF     7e30a000-7e30f000       Deferred        libxxf86vm.so.1
ELF     7e30f000-7e327000       Deferred        libice.so.6
ELF     7e327000-7e32f000       Deferred        libsm.so.6
ELF     7e32f000-7e335000       Deferred        libxrandr.so.2
ELF     7e33b000-7e3ca000       Deferred        winex11<elf>
  \-PE  7e350000-7e3ca000       \               winex11
ELF     7e44d000-7e46d000       Deferred        libexpat.so.1
ELF     7e46d000-7e498000       Deferred        libfontconfig.so.1
ELF     7e498000-7e4ad000       Deferred        libz.so.1
ELF     7e4ad000-7e51d000       Deferred        libfreetype.so.6
ELF     7e51d000-7e5bd000       Deferred        oleaut32<elf>
  \-PE  7e530000-7e5bd000       \               oleaut32
ELF     7e5bd000-7e5e8000       Deferred        ws2_32<elf>
  \-PE  7e5c0000-7e5e8000       \               ws2_32
ELF     7e5e8000-7e6a7000       Deferred        comctl32<elf>
  \-PE  7e5f0000-7e6a7000       \               comctl32
ELF     7e6a7000-7e7ab000       Deferred        shell32<elf>
  \-PE  7e6c0000-7e7ab000       \               shell32
ELF     7e7ab000-7e802000       Deferred        shlwapi<elf>
  \-PE  7e7c0000-7e802000       \               shlwapi
ELF     7e802000-7e823000       Deferred        mpr<elf>
  \-PE  7e810000-7e823000       \               mpr
ELF     7e823000-7e86e000       Deferred        wininet<elf>
  \-PE  7e830000-7e86e000       \               wininet
ELF     7e86e000-7e8a4000       Deferred        dinput<elf>
  \-PE  7e880000-7e8a4000       \               dinput
ELF     7e8a4000-7e8bc000       Deferred        dinput8<elf>
  \-PE  7e8b0000-7e8bc000       \               dinput8
ELF     7e8bc000-7e8cf000       Deferred        libresolv.so.2
ELF     7e8db000-7e8f9000       Deferred        iphlpapi<elf>
  \-PE  7e8e0000-7e8f9000       \               iphlpapi
ELF     7e8f9000-7e957000       Deferred        rpcrt4<elf>
  \-PE  7e900000-7e957000       \               rpcrt4
ELF     7e957000-7e9f6000       Deferred        ole32<elf>
  \-PE  7e960000-7e9f6000       \               ole32
ELF     7e9f6000-7ea82000       Deferred        winmm<elf>
  \-PE  7ea00000-7ea82000       \               winmm
ELF     7ea82000-7eacc000       Deferred        dsound<elf>
  \-PE  7ea90000-7eacc000       \               dsound
ELF     7eacc000-7eb31000       Deferred        msvcrt<elf>
  \-PE  7eae0000-7eb31000       \               msvcrt
ELF     7eb31000-7eb7b000       Deferred        advapi32<elf>
  \-PE  7eb40000-7eb7b000       \               advapi32
ELF     7eb7b000-7ec12000       Deferred        gdi32<elf>
  \-PE  7eb90000-7ec12000       \               gdi32
ELF     7ec12000-7ed49000       Deferred        user32<elf>
  \-PE  7ec30000-7ed49000       \               user32
ELF     7ed49000-7ee39000       Deferred        wined3d<elf>
  \-PE  7ed60000-7ee39000       \               wined3d
ELF     7ee39000-7ee68000       Deferred        d3d9<elf>
  \-PE  7ee40000-7ee68000       \               d3d9
ELF     7efa2000-7efad000       Deferred        libnss_files.so.2
ELF     7efad000-7efb7000       Deferred        libnss_nis.so.2
ELF     7efb7000-7efcf000       Deferred        libnsl.so.1
ELF     7efcf000-7eff4000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d58000-b7d5c000       Deferred        libdl.so.2
ELF     b7d5c000-b7ea6000       Deferred        libc.so.6
ELF     b7ea6000-b7ebe000       Deferred        libpthread.so.0
ELF     b7eca000-b7fde000       Deferred        libwine.so.1
ELF     b7fe0000-b7ffc000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000013 (D) Z:\home\leandro\.wine\drive_c\AeriaGames\12Sky\TwelveSky.exe
        00000014    0 <==
Backtrace:
=>1 0x003b1470 (0x0033fec4)
  2 0x003b26bc (0x0033fee0)
  3 0x00000000 (0x00e55471)
  4 0x5d895b5b (0x5d895b5d)
  5 0x00000000 (0x00000000)


```
Btw, this link for dll's is broken, so i've get of [www.dll-files.com](www.dll-files.com). Anyone can send to me those dll's that is working? My e-mail is [email]leandrovargas@bol.com.br[/email]
Thanks anyway.

---

### Post by leandrovargas on 2008-02-09
I could run it, but he gets 2 errors messenger:
1ª [Error::mGDATA.Init()]
2ª [Error::ApplicationInit()]

Anyone can help me?

Thanks anyway.

P.S. I Still needed those dlls (leandrovargas@bol.com.br).

---

### Post by leandrovargas on 2008-02-14
Anyone can help me?????

---

### Post by pandayanyan on 2008-02-17
edited

---

### Post by Nawaxo on 2008-03-11
With the advices posted in this thread i could run the game, but i get a graphical error:

[[IMG]http://img210.imageshack.us/img210/5453/screenur5.th.jpg[/IMG]](http://img210.imageshack.us/my.php?image=screenur5.jpg)

It goes on trought the game. How can I fix it?

---

### Post by hooah212002 on 2008-04-09
I need some help here. I have followed all these steps, but still get an  error when I launch the game. If someone can help, I will provide the problem. It won't even launch at all.

---

### Post by hooah212002 on 2008-04-09
> **leandrovargas said:**
> I could run it, but he gets 2 errors messenger:
1ª [Error::mGDATA.Init()]
2ª [Error::ApplicationInit()]

Anyone can help me?

Thanks anyway.

P.S. I Still needed those dlls (leandrovargas@bol.com.br).

I am getting the same errors.

---

### Post by Dude Guadalupe on 2008-09-25
> **leandrovargas said:**
> I could run it, but he gets 2 errors messenger:
1ª [Error::mGDATA.Init()]
2ª [Error::ApplicationInit()]

Anyone can help me?

Thanks anyway.

P.S. I Still needed those dlls (leandrovargas@bol.com.br).

Don't mean to dig up an old thread, but I was struggling with this issue just a few hours ago.

When you configure wine, go to the graphics tab and make sure you check the box that says "Emulate a virtual desktop". It will start right up.

---

