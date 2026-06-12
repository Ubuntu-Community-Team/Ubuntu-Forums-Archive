---
title: "Why can't I run Adobe Flash CS3?"
date: 2007-11-29
forum: Wine
---

### Post by Jammy4041 on 2007-11-29
Using WINE, I am able to run Macromedia Flash 8. So why am I not able to install Flash CS3? I want to utilize the latest version of ActionScript, and I don't want to use Windows! 

The installer keeps coming up with the error, Needs Windows XP SP2 or Later. Please upgrade to meet this...BLAH BLAH BLAH!

Could it be because I need a later version of WINE?

Any help would be much appricated.
Thanks in advance,

---

### Post by cogadh on 2007-11-29
Adobe Flash CS3 does not work with Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7120](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7120)

---

### Post by Stealth on 2007-11-29
You can run 8 and not CS3, why? Because CS3 obviously is jacking up the security measures, and WINE does not cope well with them. So far WINE (latest versions even) do NOT work with any of the CS3 products as far as I know. You can only wait and submit bug reports for now.

---

### Post by oiler920 on 2007-11-29
Somehow someone on another forum got Photoshop CS3 installed but it crashed on startup. I still don't understand how he got even CS2 running. We need a good up-to-date guide on how to run CS2. =/

---

### Post by Jammy4041 on 2007-11-30
Hmm, some person's got dreamweaver CS3 running... I wonder if I can use flash...

[http://www.openaddict.com/node/25]("http://www.openaddict.com/node/25")

But I can run Macromedia Flash 8, but I cannot run CS3. It bugs me because I want to use Actionscript 3. Oh well!

Here's how to run studio 8 at least
First download the Flash 8 here (or Dreamweaver, Fireworks and Contribute).
Download the Windows version, (this is the version which I can get to work in WINE)

To do this, you will need a (free) Macromedia ID

Now the rest is assuming you have already a code, but you can still try Studio 8 for 30 days.

Now in a Terminal/Konsole put:

wine /BLAH

(where BLAH is the exe file. For Flash, this will probably be, Flash8-en.exe.)

I found that you have to put in the full path of the exe file: this will be probably easiest to burn the .exe files to a disc and install it from there.

In a terminal, if you have burned it to a disc, put in the disc in the drive and the path will be:

wine /media/cdrom0/BLAH

(where BLAH is again the exe file)

It should then install under wine.
Hopefully you should find your new file under Applications>Wine>Programs>Macromedia>Macromedia Flash.

I found out that I had to repair the installation of Flash, but if you encounter problems, feel free to post

---

### Post by Jammy4041 on 2007-11-30
I now have an idea (YET TO BE TESTED!!!!!) 
If you type in winecfg in the Terminal, you get to your wine configuration settings. On the tab, Applications, click on add Application. 
Locate the CS3 installer (should be called Setup.exe in your Adobe CS3 folder. 

By doing it this way, you can tell the setup to run in the windows version XP (or Vista). So maybe this will work...

---

### Post by cogadh on 2007-11-30
You can get the same effect by simply setting the default OS to whatever you want. On a vanilla Wine install, it is set to Windows 2000, but you can make the default XP. It shouldn't make a difference, since Win 2000 and XP are virtually the same, from a Wine perspective.

---

### Post by Jammy4041 on 2007-11-30
The Error message it comes up with when I try to set up is basically I need Win XP to install Cs3.

Now I can't even try and setup to see if it works because it won't play ball. When I double click on the CS3 setup, it won't load. For a check, other exes work.
It won't even load into an error message! 

Maybye I should complain. But how can I ask Adobe to make flash for Linux?

---

### Post by cogadh on 2007-11-30
When running applications or installs with Wine, don't do it by the double-click method, use the terminal instead. When Wine is run through the terminal, any errors Wine encounters are output in the terminal window and can be very helpful in troubleshooting the problem.

As for complaining, I doubt they would listen, even if you do find the proper channels to go through.

---

### Post by Jammy4041 on 2007-11-30
> **cogadh said:**
> When running applications or installs with Wine, don't do it by the double-click method, use the terminal instead. When Wine is run through the terminal, any errors Wine encounters are output in the terminal window and can be very helpful in troubleshooting the problem.

As for complaining, I doubt they would listen, even if you do find the proper channels to go through.

Yes, that is the correct way, but even using the terminal, I can't seem to get the installation. It's driving me (ALMOST) CRAZY!

The exe file is located in home/james/Adobe CS3/Setup.exe

So what do I put into the terminal?

Thankyou for you kind help Cogadh.

---

### Post by cogadh on 2007-11-30
```
cd ~/Adobe\ CS3/
wine Setup.exe
```

---

### Post by Jammy4041 on 2007-12-01
I don't think it has installed using that method.
This is what I get in the terminal:

[FONT="Courier New"]fixme:actctx:ActivateActCtx 0x16ae80 0x33f6b0
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:console:AttachConsole stub ffffffff
Begin Adobe Setup
UI mode: Full GUI
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x1743e4 0x1743f0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x1743e4 0x1743f0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x1743e4 0x1743f0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x1743e4 0x1743f0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x1743e4 0x1743f0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x1743e4 0x1743f0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x1743e4 0x1743f0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:SetEntriesInAclW 2 0x33f110 (nil) 0x33f18c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:advapi:SetEntriesInAclW 2 0x33f634 (nil) 0x33f6b0
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x17b1c4 0x17b1d0 (nil) (nil)
fixme:advapi:SetEntriesInAclW 2 0x33f3ac (nil) 0x33f428
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x192134 0x192140 (nil) (nil)
fixme:advapi:SetEntriesInAclW 2 0x33f65c (nil) 0x33f6d8
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x192134 0x192140 (nil) (nil)
err:ole:CoGetClassObject class {f8383852-fcd3-11d1-a6b9-006097df5bd4} not registered
err:ole:CoGetClassObject no class object {f8383852-fcd3-11d1-a6b9-006097df5bd4} could be created for context 0x1
End Adobe Setup.  Exit code: 0
fixme:console:GetConsoleWindow stub
james@james-laptop:~/Adobe CS3$ [/FONT]


If you can find what I am doing wrong, I'd like to know.
Thanks

---

### Post by cogadh on 2007-12-01
The "fixme" messages are just developer notes about incomplete or unimplemented functions in Wine. Generally speaking, they mean nothing to end users and most applications will still run with a few "fixme" errors. Have you tried actually running the app, now that it is installed? You should "cd" to the app's install directory before trying to run it:
```
cd .wine/drive_c/Program\ Files/<path to Adobe>
wine <Adobe executable name>.exe
```

---

### Post by bluekage on 2008-03-17
Just wondering if anyone has gotten this to work yet, I tried using the method for installing dreamweaver cs3 with flash and met with...a small amount of success I would say.

It actually starts to load now instead of just sitting there doing nothing, the little splash screen will popup, do a few things and then it freezes.

Here's the output from terminal.

fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:wineboot:ProcessRunKeys Error running cmd #0 (2)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetEntriesInAclW 2 0x7bdbb704 (nil) 0x7bdbb784
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x15584c 0x155858 (nil) (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetEntriesInAclW 2 0x7bdbb66c (nil) 0x7bdbb6ec
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x156444 0x156450 (nil) (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetEntriesInAclW 2 0x7bdbb7b0 (nil) 0x7bdbb830
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x156444 0x156450 (nil) (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetEntriesInAclW 2 0x7bdbb7cc (nil) 0x7bdbb84c
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x156444 0x156450 (nil) (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:secur32:schan_FreeCredentialsHandle (0x15f8a0): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:shell:SHGetFileInfoW pidl is null!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed28,0x00000000), stub!
wine: Unhandled page fault on read access to 0x06472508 at address 0x7e317e15 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x06472508 in 32-bit code (0x7e317e15).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e317e15 ESP:0034d738 EBP:0034d758 EFLAGS:00010297(   - 00     RISAP1C)
 EAX:7c2a2120 EBX:7e367588 ECX:7e366120 EDX:00000000
 ESI:06472508 EDI:00000000
Stack dump:
0x0034d738:  00000000 00000002 00000004 00000000
0x0034d748:  00000000 7c2a2120 00000012 00000012
0x0034d758:  0034d978 7e310cfc 00000012 00000012
0x0034d768:  06472508 00000038 7c2a2120 ffffffb8
0x0034d778:  00000240 00000012 00000020 00000000
0x0034d788:  0034d7b8 7edf8734 001397fc 0034d8ec
Backtrace:
=>1 0x7e317e15 in winex11 (+0x27e15) (0x0034d758)
  2 0x7e310cfc in winex11 (+0x20cfc) (0x0034d978)
  3 0x7e315e4a X11DRV_SetDIBits+0x1f2() in winex11 (0x0034da48)
  4 0x7edda702 SetDIBits+0x190() in gdi32 (0x0034da88)
  5 0x7edda85a StretchDIBits+0x141() in gdi32 (0x0034daf8)
  6 0x006fc999 in flash (+0x2fc999) (0x7ee00a03)
  7 0x5d8928ec (0x83e58955)
  8 0x00000000 (0x00000000)
0x7e317e15: movl        0x0(%esi),%ecx
Modules:
Module  Address                 Debug info      Name (150 modules)
PE        350000-  377000       Deferred        ssleay32
PE        400000- 177d000       Export          flash
PE       1780000- 1921000       Deferred        gdiplus
PE       1930000- 1a01000       Deferred        libeay32
PE       2070000- 272b000       Deferred        flashresources
PE       2730000- 2767000       Deferred        adobe_caps
PE       2770000- 27f7000       Deferred        msvcp80
PE       38a0000- 38ea000       Deferred        bib
PE       3a00000- 3a40000       Deferred        bibutils
PE       3b50000- 3c26000       Deferred        ace
PE       3d40000- 4284000       Deferred        agm
PE       43a0000- 43ef000       Deferred        are
PE       4500000- 48b7000       Deferred        mps
PE       49d0000- 4c55000       Deferred        cooltype
PE       4e80000- 4f83000       Deferred        pdfport
PE       4f90000- 5405000       Deferred        adobepdfl
PE       5410000- 5472000       Deferred        adobexmp
PE       5480000- 54ef000       Deferred        jp2klib
PE       54f0000- 551d000       Deferred        axe8sharedexpat
PE       5aa0000- 5b7e000       Deferred        adobeowl
PE      10000000-103b0000       Deferred        flash video extension
PE      12000000-121ca000       Deferred        xerces-c_2_6
PE      30000000-3036f000       Deferred        authplay
PE      78130000-781cb000       Deferred        msvcr80
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7b98e000-7b9ad000       Deferred        wintab32<elf>
  \-PE  7b9a0000-7b9ad000       \               wintab32
ELF     7bb54000-7bb7a000       Deferred        secur32<elf>
  \-PE  7bb60000-7bb7a000       \               secur32
ELF     7bb7a000-7bb9a000       Deferred        mlang<elf>
  \-PE  7bb80000-7bb9a000       \               mlang
ELF     7bb9a000-7bc00000       Deferred        crypt32<elf>
  \-PE  7bba0000-7bc00000       \               crypt32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bdbd000-7bdd1000       Deferred        oleacc<elf>
  \-PE  7bdc0000-7bdd1000       \               oleacc
ELF     7bdd1000-7bde6000       Deferred        midimap<elf>
  \-PE  7bde0000-7bde6000       \               midimap
ELF     7bde6000-7bdfe000       Deferred        msacm32<elf>
  \-PE  7bdf0000-7bdfe000       \               msacm32
ELF     7bdfe000-7be3a000       Deferred        wineoss<elf>
  \-PE  7be10000-7be3a000       \               wineoss
ELF     7be3a000-7bf00000       Deferred        libasound.so.2
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf0a000-7bf3f000       Deferred        winealsa<elf>
  \-PE  7bf10000-7bf3f000       \               winealsa
ELF     7bf3f000-7bf90000       Deferred        libgcrypt.so.11
ELF     7bf90000-7c000000       Deferred        libgnutls.so.13
ELF     7c36c000-7c37c000       Deferred        libtasn1.so.3
ELF     7c37c000-7c3aa000       Deferred        libcrypt.so.1
ELF     7c3aa000-7c3cf000       Deferred        libk5crypto.so.3
ELF     7c3cf000-7c457000       Deferred        libkrb5.so.3
ELF     7c457000-7c480000       Deferred        libgssapi_krb5.so.2
ELF     7c480000-7c4b5000       Deferred        libcups.so.2
ELF     7c4e9000-7c51b000       Deferred        uxtheme<elf>
  \-PE  7c4f0000-7c51b000       \               uxtheme
ELF     7c61e000-7c622000       Deferred        libgpg-error.so.0
ELF     7cdf5000-7cdf7000       Deferred        libkeyutils.so.1
ELF     7cdf7000-7cdff000       Deferred        libkrb5support.so.0
ELF     7ce1f000-7ce24000       Deferred        libxfixes.so.3
ELF     7ce24000-7ce2d000       Deferred        libxcursor.so.1
ELF     7ce2d000-7ce35000       Deferred        libxrender.so.1
ELF     7ce40000-7ce43000       Deferred        libcom_err.so.2
ELF     7d6d6000-7d6e1000       Deferred        libgcc_s.so.1
ELF     7d6e1000-7d6ea000       Deferred        librt.so.1
ELF     7d7a4000-7e107000       Deferred        fglrx_dri.so
ELF     7e107000-7e1a7000       Deferred        libgl.so.1
ELF     7e1a7000-7e1ac000       Deferred        libxdmcp.so.6
ELF     7e1ac000-7e1af000       Deferred        libxau.so.6
ELF     7e1af000-7e2a0000       Deferred        libx11.so.6
ELF     7e2a0000-7e2ae000       Deferred        libxext.so.6
ELF     7e2ae000-7e2b3000       Deferred        libxxf86vm.so.1
ELF     7e2b3000-7e2cb000       Deferred        libice.so.6
ELF     7e2cb000-7e2d3000       Deferred        libsm.so.6
ELF     7e2d4000-7e2da000       Deferred        libxrandr.so.2
ELF     7e2e3000-7e36d000       Export          winex11<elf>
  \-PE  7e2f0000-7e36d000       \               winex11
ELF     7e3ed000-7e40d000       Deferred        libexpat.so.1
ELF     7e40d000-7e438000       Deferred        libfontconfig.so.1
ELF     7e438000-7e44d000       Deferred        libz.so.1
ELF     7e44d000-7e4bd000       Deferred        libfreetype.so.6
ELF     7e4bd000-7e4e3000       Deferred        netapi32<elf>
  \-PE  7e4c0000-7e4e3000       \               netapi32
ELF     7e4e3000-7e507000       Deferred        oledlg<elf>
  \-PE  7e4f0000-7e507000       \               oledlg
ELF     7e507000-7e56c000       Deferred        msvcrt<elf>
  \-PE  7e520000-7e56c000       \               msvcrt
ELF     7e56c000-7e60d000       Deferred        oleaut32<elf>
  \-PE  7e580000-7e60d000       \               oleaut32
ELF     7e60d000-7e621000       Deferred        msimg32<elf>
  \-PE  7e610000-7e621000       \               msimg32
ELF     7e621000-7e63b000       Deferred        wsock32<elf>
  \-PE  7e630000-7e63b000       \               wsock32
ELF     7e63b000-7e65c000       Deferred        mpr<elf>
  \-PE  7e640000-7e65c000       \               mpr
ELF     7e65c000-7e6a7000       Deferred        wininet<elf>
  \-PE  7e670000-7e6a7000       \               wininet
ELF     7e6a7000-7e6d2000       Deferred        ws2_32<elf>
  \-PE  7e6b0000-7e6d2000       \               ws2_32
ELF     7e6d2000-7e6ef000       Deferred        imm32<elf>
  \-PE  7e6e0000-7e6ef000       \               imm32
ELF     7e6ef000-7e704000       Deferred        psapi<elf>
  \-PE  7e700000-7e704000       \               psapi
ELF     7e704000-7e717000       Deferred        libresolv.so.2
ELF     7e727000-7e746000       Deferred        iphlpapi<elf>
  \-PE  7e730000-7e746000       \               iphlpapi
ELF     7e746000-7e7a4000       Deferred        rpcrt4<elf>
  \-PE  7e750000-7e7a4000       \               rpcrt4
ELF     7e7a4000-7e843000       Deferred        ole32<elf>
  \-PE  7e7b0000-7e843000       \               ole32
ELF     7e843000-7e86a000       Deferred        msvfw32<elf>
  \-PE  7e850000-7e86a000       \               msvfw32
ELF     7e86a000-7e890000       Deferred        msacm32<elf>
  \-PE  7e870000-7e890000       \               msacm32
ELF     7e890000-7e8ca000       Deferred        avifil32<elf>
  \-PE  7e8a0000-7e8ca000       \               avifil32
ELF     7e8ca000-7e956000       Deferred        winmm<elf>
  \-PE  7e8e0000-7e956000       \               winmm
ELF     7e956000-7e96a000       Deferred        lz32<elf>
  \-PE  7e960000-7e96a000       \               lz32
ELF     7e96a000-7e983000       Deferred        version<elf>
  \-PE  7e970000-7e983000       \               version
ELF     7e983000-7e9b8000       Deferred        winspool<elf>
  \-PE  7e990000-7e9b8000       \               winspool
ELF     7e9b8000-7ea58000       Deferred        comdlg32<elf>
  \-PE  7e9c0000-7ea58000       \               comdlg32
ELF     7ea58000-7eb17000       Deferred        comctl32<elf>
  \-PE  7ea60000-7eb17000       \               comctl32
ELF     7eb17000-7ec4e000       Deferred        user32<elf>
  \-PE  7eb30000-7ec4e000       \               user32
ELF     7ec4e000-7eca5000       Deferred        shlwapi<elf>
  \-PE  7ec60000-7eca5000       \               shlwapi
ELF     7eca5000-7eda9000       Deferred        shell32<elf>
  \-PE  7ecc0000-7eda9000       \               shell32
ELF     7eda9000-7ee40000       Export          gdi32<elf>
  \-PE  7edc0000-7ee40000       \               gdi32
ELF     7ee40000-7ee89000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee89000       \               advapi32
ELF     7efa8000-7efb3000       Deferred        libnss_files.so.2
ELF     7efb3000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff0000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c61000-b7c6a000       Deferred        libnss_compat.so.2
ELF     b7c6b000-b7c6f000       Deferred        libdl.so.2
ELF     b7c6f000-b7db9000       Deferred        libc.so.6
ELF     b7dba000-b7dd2000       Deferred        libpthread.so.0
ELF     b7de2000-b7ef6000       Deferred        libwine.so.1
ELF     b7ef8000-b7f14000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000010 
        00000012    0
        00000011    0
0000000a 
        0000000b    0
00000008 (D) C:\Program Files\Adobe\Adobe Flash CS3\Flash.exe
        00000018    0
        00000017    0
        00000016    0
        00000015    0
        00000014   15
        00000013    0
        00000009    0 <==
Backtrace:
=>1 0x7e317e15 in winex11 (+0x27e15) (0x0034d758)
  2 0x7e310cfc in winex11 (+0x20cfc) (0x0034d978)
  3 0x7e315e4a X11DRV_SetDIBits+0x1f2() in winex11 (0x0034da48)
  4 0x7edda702 SetDIBits+0x190() in gdi32 (0x0034da88)
  5 0x7edda85a StretchDIBits+0x141() in gdi32 (0x0034daf8)
  6 0x006fc999 in flash (+0x2fc999) (0x7ee00a03)
  7 0x5d8928ec (0x83e58955)
  8 0x00000000 (0x00000000)
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ec13e80, level 2): Holding 0x7ee2fb00, level 3. Expect deadlock!
err:syslevel:_CheckNotSysLevel Holding lock 0x7ee2fb00 level 3

---

### Post by phonicboom on 2008-04-04
sorry i'm not quoting the post - i'm new and didn't hit the right button i think.

anyway - in reply to the previous post "what do i type into terminal?"

i typed this...

wine '/home/chris/Desktop/Adobe CS3/Flash Professional/Adobe CS3/Setup.exe'

the ' and the ' are so terminal can handle the spaces - it keeps the whole address as 'a string'

thats all i know for now... i just did that and something happened :-)

continuing....... (loving linux so far (day 2))

---

### Post by UNaruto1990 on 2008-05-08
Does Flash CS3 works in Wine now?

---

### Post by Seks on 2008-05-21
I got it to work from a windows partition. It suffers from a lot of layout bugs, but otherwise is usable.

---

### Post by jerome187 on 2008-11-26
Just tried running CS4 that resides on my windows partition, no worko...

Output:

```

jerome187@frylock:~$ wine '/media/ACER/Program Files/Adobe/Adobe Flash CS4/Flash.exe' 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\xerces-c_2_6.dll") not found
err:module:import_dll Library xerces-c_2_6.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Flash.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\dvacore.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\dvacore.dll") not found
err:module:import_dll Library dvacore.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Workspace.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\dvacore.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\dvacore.dll") not found
err:module:import_dll Library dvacore.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\dvaui.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\dvaui.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\dvaui.dll") not found
err:module:import_dll Library dvaui.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Workspace.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\AdobeOwl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\AdobeOwl.dll") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Workspace.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\xerces-c_2_6.dll") not found
err:module:import_dll Library xerces-c_2_6.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Workspace.dll") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Workspace.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Workspace.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Workspace.dll") not found
err:module:import_dll Library Workspace.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Flash.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\AlcidDLL.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\AlcidDLL.dll") not found
err:module:import_dll Library AlcidDLL.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Flash.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\ahclient.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\ahclient.dll") not found
err:module:import_dll Library ahclient.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Flash.exe") not found
fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\LogUtils.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\LogUtils.dll") not found
err:module:import_dll Library LogUtils.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\CrashReporter.dll") not found
fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\LogTransport.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\LogTransport.dll") not found
err:module:import_dll Library LogTransport.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\CrashReporter.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\CrashReporter.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\CrashReporter.dll") not found
err:module:import_dll Library CrashReporter.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Flash.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\LogTransport2.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\LogTransport2.dll") not found
err:module:import_dll Library LogTransport2.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\LogSession.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\LogSession.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\LogSession.dll") not found
err:module:import_dll Library LogSession.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Flash.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Flash.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Flash.exe") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Flash.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\ACER\\Program Files\\Adobe\\Adobe Flash CS4\\Flash.exe" failed, status c0000135
jerome187@frylock:~$ bummer...

```

---

### Post by hikaricore on 2008-11-26
You should be testing any program under WINE for the first time from its own directory...

Anyway don't dig up old threads, start a new one on your topic so our members don't have to wade through outdated crap trying to assist folk.

---

