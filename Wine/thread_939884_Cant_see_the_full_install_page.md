---
title: "Cant see the full install page?"
date: 2008-10-06
forum: Wine
---

### Post by ceaser_salad on 2008-10-06
Hi there

I'm new to ubuntu, deleted windows and installed ubuntu without the live cd, so I'm pleasantly surprised by how it looks! 

I installed wine, so I could get google sketch up running. No problems there. 
Now I'd like to install Garmin's Training Centre(gps data logger). After choosing the install option on its menu it takes me to the EULA page. Heres where I get stuck. Now although I can tick and agree to the terms, Wine doesnt display the full window, so I can click Next.

The virtual desktop is set to 1000x700.

Any help is appreciated.

---

### Post by kostkon on 2008-10-06
> **ceaser_salad said:**
> Hi there

I'm new to ubuntu, deleted windows and installed ubuntu without the live cd, so I'm pleasantly surprised by how it looks! 

I installed wine, so I could get google sketch up running. No problems there. 
Now I'd like to install Garmin's Training Centre(gps data logger). After choosing the install option on its menu it takes me to the EULA page. Heres where I get stuck. Now although I can tick and agree to the terms, Wine doesnt display the full window, so I can click Next.

The virtual desktop is set to 1000x700.

Any help is appreciated.
Yes, it seems that Wine has a problem displaying the EULA page.

Have you tried pressing *Enter*, you never know, maybe the *Next* button is in focus. Or you can try pressing *Tab* to bring this button in focus.

Which version of *Wine* are you using?

---

### Post by ceaser_salad on 2008-10-06
Hi

Tried pressing enter, no luck. Same with tab, that only high lights the eula script.

I tried an earlier version of training centre(3.4.1 as opposed to 3.4.5), but that gave the same problem.

I'm using Wine 1.0

---

### Post by ceaser_salad on 2008-10-09
bump

---

### Post by ceaser_salad on 2008-10-13
bump

---

### Post by ceaser_salad on 2008-10-14
I've been thinking, since Garmin have a training centre version for mac OSX, could I use a mac emulator to run this program in wine? I really dont want to do this, but short of someone being able to solve my problem, this could be a work around. 
Can anybody recommend a good mac emulator?

---

### Post by david_kt on 2008-10-15
> **ceaser_salad said:**
> 
Now I'd like to install Garmin's Training Centre(gps data logger). After choosing the install option on its menu it takes me to the EULA page. Heres where I get stuck. Now although I can tick and agree to the terms, Wine doesnt display the full window, so I can click Next.

The virtual desktop is set to 1000x700.

Any help is appreciated.

Please open wine registry editor:

Open terminal and issue below command:
```
regedit
```

click HKEY_CURRENT_CONFIG > Software > fonts > and double click "LogPixels".

It will open edit Dword with value data 60. Try to change to lower value, e.g. 40.

Hopefully it would help.

DK

---

### Post by ceaser_salad on 2008-10-15
Thanks DK!

I managed to install it. Now I've got a new problem. When I start the program, before it even initializes the program it switches to the default page, and shuts down wine. What could be causing this? Also, would wine have any difficulties reading from a USB device?

---

### Post by david_kt on 2008-10-15
> **ceaser_salad said:**
> Thanks DK!

I managed to install it. Now I've got a new problem. When I start the program, before it even initializes the program it switches to the default page, and shuts down wine. What could be causing this? Also, would wine have any difficulties reading from a USB device?

I guess it managed to create a desktop launcher so taht you could launch it. Right click on the desktop launcher, choose properties, and then launcher. Copy the command there.

Open terminal, and paste the command ( <ctrl> <shift> V or right click on the terminal and then choose paste).

Then, press enter to launch the program. Post the out put of terminal here.

DK

---

### Post by ceaser_salad on 2008-10-15
OK, heres what I got:

emile@emile:~$ env WINEPREFIX="/home/emile/.wine" wine "C:\Garmin\Training Center.exe"
wine: Call from 0x7b844b20 to unimplemented function gdiplus.dll.GdipCreateBitmapFromResource, aborting
wine: Unimplemented function gdiplus.dll.GdipCreateBitmapFromResource called at address 0x7b844b20 (thread 0009), starting debugger...
Unhandled exception: unimplemented function gdiplus.dll.GdipCreateBitmapFromResource called in 32-bit code (0x7b844b96).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b844b96 ESP:0032f30c EBP:0032f370 EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82eb09 EBX:7b8b3884 ECX:00000000 EDX:0011fda8
 ESI:0011fda8 EDI:00400000
Stack dump:
0x0032f30c:  0032f398 00000008 00000010 0032f338
0x0032f31c:  80000100 00000001 00000000 7b844b20
0x0032f32c:  00000002 7ea1d740 7ea1db34 0032f398
0x0032f33c:  7bc4384e 00110048 00000000 00000010
0x0032f34c:  00000000 00002800 010418e0 7bc589be
0x0032f35c:  7bc589be 7bc33d21 0090cba0 01020000
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x0032f370)
  2 0x7ea1d6d5 in gdiplus (+0x1d6d5) (0x0032f3a0)
  3 0x7ea0a2ac in gdiplus (+0xa2ac) (0x0032f950)
  4 0x7bc46ec1 in ntdll (+0x36ec1) (0x0032fa20)
  5 0x7bc47877 LdrGetDllHandle+0x117() in ntdll (0x0032fb80)
  6 0x00110dc4 (0x00a82e3c)
  7 0x00720065 in training center (+0x320065) (0x00730075)
0x7b844b96: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (100 modules)
PE	  400000-  df8000	Export          training center
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7dfed000-7dff1000	Deferred        libgpg-error.so.0
ELF	7dff1000-7e03e000	Deferred        libgcrypt.so.11
ELF	7e03e000-7e04e000	Deferred        libtasn1.so.3
ELF	7e04e000-7e051000	Deferred        libkeyutils.so.1
ELF	7e051000-7e083000	Deferred        libcrypt.so.1
ELF	7e083000-7e0f9000	Deferred        libgnutls.so.13
ELF	7e0f9000-7e11c000	Deferred        libk5crypto.so.3
ELF	7e11c000-7e1a9000	Deferred        libkrb5.so.3
ELF	7e1a9000-7e1d2000	Deferred        libgssapi_krb5.so.2
ELF	7e1d2000-7e205000	Deferred        libcups.so.2
ELF	7e268000-7e29b000	Deferred        uxtheme<elf>
  \-PE	7e270000-7e29b000	\               uxtheme
ELF	7e29b000-7e2a4000	Deferred        libxcursor.so.1
ELF	7e2a4000-7e2a9000	Deferred        libxfixes.so.3
ELF	7e2a9000-7e2ac000	Deferred        libxcomposite.so.1
ELF	7e2ac000-7e2b2000	Deferred        libxrandr.so.2
ELF	7e2b2000-7e2ba000	Deferred        libxrender.so.1
ELF	7e2ba000-7e2da000	Deferred        imm32<elf>
  \-PE	7e2c0000-7e2da000	\               imm32
ELF	7e2da000-7e2df000	Deferred        libxdmcp.so.6
ELF	7e2df000-7e2f7000	Deferred        libxcb.so.1
ELF	7e2f7000-7e3de000	Deferred        libx11.so.6
ELF	7e3de000-7e3ec000	Deferred        libxext.so.6
ELF	7e3ec000-7e404000	Deferred        libice.so.6
ELF	7e404000-7e40c000	Deferred        libsm.so.6
ELF	7e40d000-7e415000	Deferred        libkrb5support.so.0
ELF	7e415000-7e418000	Deferred        libcom_err.so.2
ELF	7e41a000-7e4b1000	Deferred        winex11<elf>
  \-PE	7e430000-7e4b1000	\               winex11
ELF	7e4d9000-7e4fa000	Deferred        libexpat.so.1
ELF	7e4fa000-7e524000	Deferred        libfontconfig.so.1
ELF	7e524000-7e527000	Deferred        libxinerama.so.1
ELF	7e527000-7e52a000	Deferred        libxau.so.6
ELF	7e532000-7e547000	Deferred        libz.so.1
ELF	7e547000-7e5b4000	Deferred        libfreetype.so.6
ELF	7e5b4000-7e5d5000	Deferred        mpr<elf>
  \-PE	7e5c0000-7e5d5000	\               mpr
ELF	7e5d5000-7e623000	Deferred        wininet<elf>
  \-PE	7e5e0000-7e623000	\               wininet
ELF	7e623000-7e637000	Deferred        lz32<elf>
  \-PE	7e630000-7e637000	\               lz32
ELF	7e637000-7e650000	Deferred        version<elf>
  \-PE	7e640000-7e650000	\               version
ELF	7e650000-7e665000	Deferred        psapi<elf>
  \-PE	7e660000-7e665000	\               psapi
ELF	7e665000-7e6af000	Deferred        dbghelp<elf>
  \-PE	7e670000-7e6af000	\               dbghelp
ELF	7e6af000-7e6c6000	Deferred        imagehlp<elf>
  \-PE	7e6b0000-7e6c6000	\               imagehlp
ELF	7e6c6000-7e6d9000	Deferred        shfolder<elf>
  \-PE	7e6d0000-7e6d9000	\               shfolder
ELF	7e6d9000-7e705000	Deferred        ws2_32<elf>
  \-PE	7e6e0000-7e705000	\               ws2_32
ELF	7e705000-7e72c000	Deferred        oledlg<elf>
  \-PE	7e710000-7e72c000	\               oledlg
ELF	7e72c000-7e762000	Deferred        winspool<elf>
  \-PE	7e730000-7e762000	\               winspool
ELF	7e762000-7e80d000	Deferred        comdlg32<elf>
  \-PE	7e770000-7e80d000	\               comdlg32
ELF	7e80d000-7e820000	Deferred        libresolv.so.2
ELF	7e820000-7e822000	Deferred        libxcb-xlib.so.0
ELF	7e822000-7e827000	Deferred        libxxf86vm.so.1
ELF	7e82e000-7e84c000	Deferred        iphlpapi<elf>
  \-PE	7e830000-7e84c000	\               iphlpapi
ELF	7e84c000-7e8ad000	Deferred        rpcrt4<elf>
  \-PE	7e860000-7e8ad000	\               rpcrt4
ELF	7e8ad000-7e951000	Deferred        ole32<elf>
  \-PE	7e8c0000-7e951000	\               ole32
ELF	7e951000-7e9f3000	Deferred        oleaut32<elf>
  \-PE	7e960000-7e9f3000	\               oleaut32
ELF	7e9f3000-7ea2b000	Export          gdiplus<elf>
  \-PE	7ea00000-7ea2b000	\               gdiplus
ELF	7ea2b000-7eaea000	Deferred        comctl32<elf>
  \-PE	7ea30000-7eaea000	\               comctl32
ELF	7eaea000-7eb3c000	Deferred        advapi32<elf>
  \-PE	7eb00000-7eb3c000	\               advapi32
ELF	7eb3c000-7ebd7000	Deferred        gdi32<elf>
  \-PE	7eb50000-7ebd7000	\               gdi32
ELF	7ebd7000-7ed1e000	Deferred        user32<elf>
  \-PE	7ebf0000-7ed1e000	\               user32
ELF	7ed1e000-7ed77000	Deferred        shlwapi<elf>
  \-PE	7ed30000-7ed77000	\               shlwapi
ELF	7ed77000-7ee8a000	Deferred        shell32<elf>
  \-PE	7ed90000-7ee8a000	\               shell32
ELF	7efaa000-7efb5000	Deferred        libnss_files.so.2
ELF	7efb5000-7efcd000	Deferred        libnsl.so.1
ELF	7efcd000-7eff2000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cb3000-b7cbc000	Deferred        libnss_compat.so.2
ELF	b7cbd000-b7cc1000	Deferred        libdl.so.2
ELF	b7cc1000-b7e10000	Deferred        libc.so.6
ELF	b7e10000-b7e28000	Deferred        libpthread.so.0
ELF	b7e36000-b7f6c000	Deferred        libwine.so.1
ELF	b7f6e000-b7f8a000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Garmin\Training Center.exe
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
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x0032f370)
  2 0x7ea1d6d5 in gdiplus (+0x1d6d5) (0x0032f3a0)
  3 0x7ea0a2ac in gdiplus (+0xa2ac) (0x0032f950)
  4 0x7bc46ec1 in ntdll (+0x36ec1) (0x0032fa20)
  5 0x7bc47877 LdrGetDllHandle+0x117() in ntdll (0x0032fb80)
  6 0x00110dc4 (0x00a82e3c)
  7 0x00720065 in training center (+0x320065) (0x00730075)
wine: Call from 0x7b844b20 to unimplemented function gdiplus.dll.GdipCreateCachedBitmap, aborting
wine: Call from 0x7b844b20 to unimplemented function gdiplus.dll.GdipCreateEffect, aborting
emile@emile:~$

---

### Post by david_kt on 2008-10-15
> **ceaser_salad said:**
> OK, heres what I got:

emile@emile:~$ env WINEPREFIX="/home/emile/.wine" wine "C:\Garmin\Training Center.exe"
wine: Call from 0x7b844b20 to unimplemented function gdiplus.dll.GdipCreateBitmapFromResource, aborting
$

Open terminal and:

```
emile@emile:~$wget http://www.kegel.com/wine/winetricks

```

Upon successfully download winetricks:

```
emile@emile:~$chmod +x winetricks
emile@emile:~$sh winetricks gdiplus
```

Upon successfully install pp.viewer, try again

```
emile@emile:~$ env WINEPREFIX="/home/emile/.wine" wine "C:\Garmin\Training Center.exe"
```

Hopefully it would help.

DK

---

### Post by ceaser_salad on 2008-10-16
WoW! I actually got to see the the GUI this time! Now a little error message pops up, saying that theres a problem with this program and gives an error report. 
I cant see anything out of place in the report, apart from the year being '60356' and month '49'.

I recall a similar error appearing when I used Training Centre in XP. There I just clicked OK, and could carry on using the program. 

This is what the terminal showed during the error:

fixme:win:EnumDisplayDevicesW ((null),0,0x32ed88,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10026 0x00000000
fixme:dciman:DCICreatePrimary 0x374 0x12413a0
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x10026
emile@emile:~$ 

Thanks for your help so far!!!

---

### Post by david_kt on 2008-10-16
> **ceaser_salad said:**
> 
This is what the terminal showed during the error:

fixme:win:EnumDisplayDevicesW ((null),0,0x32ed88,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10026 0x00000000
fixme:dciman:DCICreatePrimary 0x374 0x12413a0
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x10026


I can't see anything that cause wine to crash here, I guess it is the garmin that cause it to close.

You could try to emulate different windows version to see if that help. 
Application > Wine > Configure wine

Click on windows version drop down box. Choose different kind of windows and start garmin again, hopefully some of the windows version there is suitable.

And please post the whole output of terminal in order to see when it start to have problem.

DK

---

### Post by ceaser_salad on 2008-10-16
I tried every version of windows available, still no luck :-(

This is all that appears in the terminal when I launch the program:

emile@emile:~$ env WINEPREFIX="/home/emile/.wine" wine "C:\Garmin\Training Center.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed88,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10026 0x00000000
fixme:dciman:DCICreatePrimary 0x374 0x12513a0
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:tab:TAB_SetCurFocus Should set input focus
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x10026
emile@emile:~$ 

Something I forgot to mention. In my earlier attempts at getting this to work, I installed an earlier version of TC. I had a look at uninstalling the older one, but nothing happened. So I tried the newer one, which at the the end of the uninstall, says thanks for installing Garmin... D I have to reboot after uninstalling a program in wine?

---

### Post by ceaser_salad on 2008-10-20
Thanks for all your help david_kt! Although I haven't gotten training centre working, I wouldn't have come this far with out your help :-) 

In the meantime I found a work around. At first all I could find were posts saying one should use gpsbabel(command line only for converting files to the right format) and a program called Qlandkarte(to move maps to the gps). 
Well, I have a very basic gps, with no map support, and all I wanted to do was see the data I had collected on my training rides/runs. It didnt need to be on a map(though that looks better than dots and lines on a blank screen).

While hunting around, I found gpsbabel for windows, and this time there was a GUI version. This allowed me to put the data on Qlandkarte, as I couldnt figure out the command line version of 'babel. I still didnt like using this setup, even if it is potentially a powerful combination. 

So I installed a very basic garmin app called Foreahtlete(designed for my gps, which is the forerunner). 
Funny, this one worked in wine! 
As I said, its basic, but it gave me my data in a format that I was used to.
I also found a program called EasyGPS(windows). Also a basic little tool, that lets me see my data on a map(if I choose to put one on it, which I haven't). Unlike foreathlete, this program lets me upload waypoints and tracks to my gps. It does other things, but for now, this is all I need it to do.

Well, thats the story so far. Hope its useful to someone out there.

---

### Post by david_kt on 2008-10-20
> **ceaser_salad said:**
> Thanks for all your help david_kt! Although I haven't gotten training centre working, I wouldn't have come this far with out your help :-) 

I don't think I am much of help for your case, you had solved your problem yourself. Hopefully what you write would help other people facing similar problem.

DK

---

