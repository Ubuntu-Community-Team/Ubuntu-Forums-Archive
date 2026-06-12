---
title: "No Screen Detected?"
date: 2006-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chillaxed on 2006-02-26
i keep getting the "no screen detected" error and i'm ripping my hair out trying to figure it out

i'm dual booting ubuntu and windows xp pro corprate edition

everything works fine except that, so therefore i can't go to the logon screen and boot onto my desktop, it makes me do a text login but then it does nothing. it just says josh@ubuntu:~$ and i try typing "startx" and thats when it tell me "fatal server error, no screens detected"

i want to see what ubuntu looks like! i'm tired of this black screen with white text!!!!

someone help me out PLEASE!

---

### Post by pestilence4hr on 2006-02-26
Paste output of /var/log/Xorg.0.log here, especially the line that is prefixed with (EE)

---

### Post by Chillaxed on 2006-02-26
so just like type in that or should i see it?

i'll go try it

---

### Post by pestilence on 2006-02-26
```

cat /var/log/Xorg.0.log

```

---

### Post by Chillaxed on 2006-02-26
what do i do with that? type it into the prompt?

sry first time linux user :-?

---

### Post by Chillaxed on 2006-02-26
ok well i don't know how to get into that log

i have also tried the FAQ and it also said go to teh log file, and to fix it try the graphical thingy. well how do you do that if its saying no screen is detected? :rolleyes: 

i'm thinking about trying redhat or something cuz i'm getting absolutely furious!

---

### Post by Chillaxed on 2006-02-26
someone said to install new drivers but i can't even get into ubuntu

is there a way?

---

### Post by Mustard on 2006-02-26
[QUOTE=Chillaxed]someone said to install new drivers but i can't even get into ubuntu

is there a way?[/QUOTE]

Well, you have described being at a login prompt, so you have a 'command line'.  From there it is possible to reconfigure the system to use different drivers, and to view you logs.  What is really needed is some patience and a bit of learning to solve the issue.  Can you describe how succesful you have been with logging in to the system from the command line?  What commands have you attempted to do?  What errors have you seen when you did them?  These are all questions that are going through my mind atm, but I'm not seeing any answers in your posts.  Try to be a bit more descriptive of what you have done and what you are seeing.  The error messages you see are vital clues as to what is going wrong in the process.

I'm going to assume you have logged in with the user name and password you set up in the install from the command line login prompt.  If you have you should try this command...

```
sudo dpkg-reconfigure xserver-xorg
```

It will ask for your user password.  Please be aware that when you type in the user password you will not see your keypresses echoed to the screen.  The password being entered is entirely invisible to the user.  Just  type it in when prompted and hit enter when finished.

When you succesfully run that command it will start up a dialog on your screen.  Give the default answers to all questions you don't have a clue what the answers are to.  When you get to the drivers part, choose the 'vesa' drivers.

When its finished, try typing this command to start the 'x server' (the gui display),...

```
startx
```

Come back with detailed explanations of what went wrong if you get errors.

If you haven't even logged in yet, then when you get to a 'login prompt', you should do so with your username and password that you set up in the installation process. You can't do much until you have logged in and are looking at a 'command prompt'.

Can you also give information on what graphics card you have in your system?  I'm thinking its probably an ATI graphics card, since most people with this issue have ATI cards.  If you could confirm that though, it would be nice. :)

---

### Post by Mustard on 2006-02-26
[QUOTE=Chillaxed]ok well i don't know how to get into that log

i have also tried the FAQ and it also said go to teh log file, and to fix it try the graphical thingy. well how do you do that if its saying no screen is detected? :rolleyes: 

i'm thinking about trying redhat or something cuz i'm getting absolutely furious![/QUOTE]

Just for your information, if people feel you're going to 'give up' half way through the the troubleshooting process, then do you think they will be motivated to help you?  We are all just normal ubuntu users who happened to take the time to help others with their problems.  We are not paid support people.

Saying that your furious and are going to go try something else is just going to make people think that all the typing that is necessary to help you with **your problem** is going to be a bit of a waste of time.  Try to give the impression that you are going to at least attempt to follow instructions and give reasonable feedback on what you have tried to do.

---

### Post by Chillaxed on 2006-02-27
THANK YOU!

everything is working all i need to do is install drivers for everything and thats about it!

---

### Post by Shampyon on 2006-03-21
I've just started having this same problem a few minutes ago. I'm using an ATI Radeon x700Super (512MB). I'd installed the ATI drivers a few hours ago, and everything was going well, until I decided to install Doom 3.

I followed the instructions carefully, but whenever I tried to start the game I got some wierd magnifying-glass effect on the desktop, and the game never starts or even shows up in the System Monitor list. So I though, hey, maybe I just beed to change a setting in the ATI Control settings. That's when things went horribly wrong.

My screen shrunk. It took up about 3/4 of it's usual size. The rest of what's usually my work area was filled with the default Human Theme brown. I tried to correct the settings I'd changed, but noticed that there was nothing [i[to[/i] change. My TV out settings (which should be irrelevant, since I have no TV hooked up) are set to PAL - normal for Australia. I'd reset from Dual Screen to Single Screen, since I only have the one.

I logged out, logged back in - now X won't start. Yay! So I start up the config editor, change driver from ATI to VESA. I can use Ubuntu again, but the ATI control panel doesn't have any relevant options to fix it. Plus I staill get that stupid magnifying error when I try to run Doom.

Here's my log:
```
        BytesPerScanline: 1856
        XResolution: 1856
        YResolution: 1392
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 5
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 1856
        BnkNumberOfImagePages: 5
        LinNumberOfImagePages: 5
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 400000000
Mode: 1d4 (1856x1392)
        ModeAttributes: 0xbb
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00057bb
        BytesPerScanline: 3712
        XResolution: 1856
        YResolution: 1392
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 2
        RedMaskSize: 5
        RedFieldPosition: 10
        GreenMaskSize: 5
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 3712
        BnkNumberOfImagePages: 2
        LinNumberOfImagePages: 2
        LinRedMaskSize: 5
        LinRedFieldPosition: 10
        LinGreenMaskSize: 5
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 400000000
Mode: 1d5 (1856x1392)
        ModeAttributes: 0xbb
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00057bb
        BytesPerScanline: 3712
        XResolution: 1856
        YResolution: 1392
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 2
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 3712
        BnkNumberOfImagePages: 2
        LinNumberOfImagePages: 2
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 400000000
*(WW) (1856x1392,BENQ V773) mode clock 218.3MHz exceeds DDC maximum 110MHz
Mode: 1d6 (1856x1392)
        ModeAttributes: 0xbb
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00057bb
        BytesPerScanline: 7424
        XResolution: 1856
        YResolution: 1392
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 1
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 7424
        BnkNumberOfImagePages: 1
        LinNumberOfImagePages: 1
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 400000000
Mode: 1e3 (1920x1440)
        ModeAttributes: 0xbb
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00057bb
        BytesPerScanline: 1920
        XResolution: 1920
        YResolution: 1440
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 4
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 1920
        BnkNumberOfImagePages: 4
        LinNumberOfImagePages: 4
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 400000000
Mode: 1e4 (1920x1440)
        ModeAttributes: 0xbb
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00057bb
        BytesPerScanline: 3840
        XResolution: 1920
        YResolution: 1440
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 2
        RedMaskSize: 5
        RedFieldPosition: 10
        GreenMaskSize: 5
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 3840
        BnkNumberOfImagePages: 2
        LinNumberOfImagePages: 2
        LinRedMaskSize: 5
        LinRedFieldPosition: 10
        LinGreenMaskSize: 5
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 400000000
Mode: 1e5 (1920x1440)
        ModeAttributes: 0xbb
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00057bb
        BytesPerScanline: 3840
        XResolution: 1920
        YResolution: 1440
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 2
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 3840
        BnkNumberOfImagePages: 2
        LinNumberOfImagePages: 2
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 400000000
*(WW) (1920x1440,BENQ V773) mode clock 234MHz exceeds DDC maximum 110MHz
Mode: 1e6 (1920x1440)
        ModeAttributes: 0xbb
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00057bb
        BytesPerScanline: 7680
        XResolution: 1920
        YResolution: 1440
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 1
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 7680
        BnkNumberOfImagePages: 1
        LinNumberOfImagePages: 1
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 400000000

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): BENQ V773: Using default hsync range of 30.00-72.00 kHz
(II) VESA(0): BENQ V773: Using default vrefresh range of 50.00-120.00 Hz
(II) VESA(0): Not using built-in mode "1920x1440" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1856x1392" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1400x1050" (width too large for virtual size)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0):  Built-in mode "1280x1024"
(**) VESA(0):  Built-in mode "1280x1024"
(**) VESA(0):  Built-in mode "1152x864"
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "720x400"
(**) VESA(0):  Built-in mode "640x400"
(**) VESA(0):  Built-in mode "640x400"
(**) VESA(0):  Built-in mode "640x350"
(++) VESA(0): DPI set to (100, 100)
(WW) (1280x1024,BENQ V773) mode clock 135MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,BENQ V773) mode clock 157.5MHz exceeds DDC maximum 110MHz
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (11b)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 85Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x480" (112)
(WW) (1280x1024,BENQ V773) mode clock 135MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,BENQ V773) mode clock 157.5MHz exceeds DDC maximum 110MHz
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (166)
(WW) (1280x1024,BENQ V773) mode clock 135MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,BENQ V773) mode clock 157.5MHz exceeds DDC maximum 110MHz
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (124)
(WW) (1152x864,BENQ V773) mode clock 121.5MHz exceeds DDC maximum 110MHz
(II) VESA(0): Attempting to use 75Hz refresh for mode "1152x864" (156)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1024x768" (123)
(II) VESA(0): Attempting to use 85Hz refresh for mode "800x600" (122)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x480" (121)
(II) VESA(0): Attempting to use 85Hz refresh for mode "720x400" (136)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x400" (186)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x400" (186)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x350" (1c6)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/X11R6/lib/modules/libshadow.a
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
        [6] -1  0       0xfdce0000 - 0xfdcfffff (0x20000) MX[B]
        [7] -1  0       0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
        [8] -1  0       0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
        [9] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[B](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [11] -1 0       0xfd9e0000 - 0xfd9effff (0x10000) MX[B](B)
        [12] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [13] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [14] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [17] -1 0       0x0000ef00 - 0x0000ef1f (0x20) IX[B]
        [18] -1 0       0x0000cf00 - 0x0000cf1f (0x20) IX[B]
        [19] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [20] -1 0       0x0000fb00 - 0x0000fb0f (0x10) IX[B]
        [21] -1 0       0x0000fc00 - 0x0000fc1f (0x20) IX[B]
        [22] -1 0       0x0000fd00 - 0x0000fd1f (0x20) IX[B]
        [23] -1 0       0x0000fe00 - 0x0000fe1f (0x20) IX[B]
        [24] -1 0       0x0000ff00 - 0x0000ff1f (0x20) IX[B]
        [25] -1 0       0x0000be00 - 0x0000beff (0x100) IX[B](B)
        [26] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [27] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 9.10
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: RV410
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(==) VESA(0): Write-combining range (0xd0000000,0x1000000)
(II) VESA(0): virtual address = 0xb6d5b000,
        physical address = 0xd0000000, size = 16777216
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.

```

---

### Post by Shampyon on 2006-03-21
I'm thinking of uninstalling the ATI drivers and reinstalling them.
This may well fix the problem, but I don't know how to prevent it from happening again. Should I just stick with the VESA drivers, or should I go ahead and reinstall the ATI?

And anyone have any clues on what's wrong with Doom 3? Even using VESA, when I try to start it (menu or terminal) it still refuses to actually start, instead putting a magnifier on my desktop. I have to log out to return to normal, and the log out options have all disappeared. Instead I only get to click "Log Out" on the menu, and it returns me to the black screen command line interface.

---

