---
title: "How do I contact the Wine people?"
date: 2008-01-22
forum: Wine
---

### Post by Greg Mueller on 2008-01-22
I've looked around on the WineHQ page and can't really see a way to send an email to them with a question I have.
How do I do that?

---

### Post by b0rka7a on 2008-01-22
Why don't you ask them in the Wine's irc channel :D
[http://www.winehq.org/site/irc](http://www.winehq.org/site/irc)

---

### Post by Greg Mueller on 2008-01-22
I really didn't want to get into a whole new arena of setting things up.
I just wanted to send them an email and ask a question.

Seems like whatever I want to do I have to do two other things before it.

---

### Post by b0rka7a on 2008-01-22
> Seems like whatever I want to do I have to do two other things before it.
Don't worry... me too :lolflag:

---

### Post by denali on 2008-01-22
As with most open source projects, it's a group effort and not an effort by an individual or a single corporation.  So finding a single point of contact for "The Wine People" is going to be a Sisyphean task at best.

Is your issue one involving a source code level issue or is it an end-user issue?

---

### Post by buntunub on 2008-01-22
>  How do I contact the Wine people?



:lolflag:

---

### Post by Greg Mueller on 2008-01-22
My question for them regards running an app and having it recognize a USB camera.

Using the device manager I can see the camera sitting there. When I turn off the power to the camera it goes away, when I turn it on it comes back. It's a CCD astronomical USB camera for astrophotography.

I am running an windows astronomy app under Wine. It's call Maxim DL/CCD. It starts up but will not recognize the camera.

---

### Post by denali on 2008-01-22
Ahhhh...

If you wouldn't mind, lets try something.  Have you tried starting the application from a terminal?  The reason I ask is that Wine prints (sometimes) useful information when you start it from a terminal.  Go to the directory where Maxim DL/CCD is stored and type:

wine (program executable name)

Substitute the name of the main Maxim DL/CCD program for (program executable name). When you hit enter, you should begin to see quite a bit of text scroll on the terminal screen.  Tell the program to try to connect to the camera and paste back what it says on the terminal here in the forum.

**EDIT:**  Did some research on the program.  Does your camera require something called the "ASCOM Platform" to run under Windows?  If so, did you install the "ASCOM Platform" and associated drivers in Wine?

---

### Post by Greg Mueller on 2008-01-22
Holy Cow an expert
I'll have to check for sure but I do remember seeing the ascom platform go by. I do have a working edition in a windows computer. I'll look

I spent most of the day working on a couple other windows computers that are going to be in the network

---

### Post by Greg Mueller on 2008-01-23
Yesterday while messing with my other computers I had to reinstall this software on a computer with a windows OS. The installer program for this camera was on an install disk which contained to utility programs to operate the camera. This is the one that tried to start and then just disappeared. I tried to do a terminal start of this program under wine and got the following message

greg@OB-1:~$ wine "/home/greg/.wine/drive_c/Program Files/Finger Lakes Instrumentation/FLIGrab.exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\cfitsio.dll") not found
err:module:import_dll Library cfitsio.dll (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\FLIGrab.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Finger Lakes Instrumentation\\FLIGrab.exe" failed, status c0000135
greg@OB-1:~$ 


I hope this provides some clue to it's non start issues

---

### Post by Greg Mueller on 2008-01-23
When I tried to install the camera software off of the CD I got this message...

greg@OB-1:~$ wine "/media/cdrom1/FLI Installation Files/FLI Installation Files/Setup.Exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet

Copyright 2004 Vincent B&#65533;ron
greg@OB-1:~$ 




Without installing this software (from FLI) first (in Windows) the Maxim Application would not recognize the camera. After installing the software (in Windows) it would

Also in Windows when I plugged in the camera and the filter wheel, windows had to "install the new hardware" which is something Ubuntu doesn't seem to do

---

### Post by denali on 2008-01-23
I've read both messages.  What version of Wine are you using?

wine --version

---

### Post by Greg Mueller on 2008-01-23
I just installed the latest version within the last two days. I think it is 9.53

---

### Post by denali on 2008-01-23
I'm not sure this will work, but for the sake of experimentation, try this:

wine **start** "/media/cdrom1/FLI Installation Files/FLI Installation Files/Setup.Exe"

Notice the part in bold, which is different than your original command line.  The file appears to be an MS Installer file and for some reason Wine doesn't appear to be handling it properly.  using start may rectify that, but I have little faith it will.  Meantime, I'm going to see what I can find out about the FLI drivers.

**EDIT**: A question - FLI is Finger Lakes Instrumentation?  If so, have you tried installing the drivers at [http://www.fli-cam.com/software/FLI-Installer.exe](http://www.fli-cam.com/software/FLI-Installer.exe) instead?

---

### Post by Greg Mueller on 2008-01-23
Tried it and got this
greg@OB-1:~$ wine start "/media/cdrom1/FLI Installation Files/FLI Installation Files/Setup.Exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:start:wmain Option 'L"/cdrom1/FLI Installation Files/FLI Installation Files/Setup.Exe"' not recognized
Start a program, or open a document in the program normally used for files with that suffix. 
Usage: 
start [options] program_filename [...] 
start [options] document_filename 

Options: 
/M[inimized] Start the program minimized. 
/MAX[imized] Start the program maximized. 
/R[estored]  Start the program normally (neither minimized nor maximized). 
/W[ait]      Wait for started program to finish, then exit with its exit code. 
/L           Show end-user license. 

start.exe version 0.2 Copyright (C) 2003, Dan Kegel 
Start comes with ABSOLUTELY NO WARRANTY; for details run with /L option. 
This is free software, and you are welcome to redistribute it 
under certain conditions; run 'start /L' for details. 
greg@OB-1:~$

---

### Post by denali on 2008-01-23
I was afraid of that.  I modified my last post to ask the following question:

A question - FLI is Finger Lakes Instrumentation? If so, have you tried installing the drivers at [http://www.fli-cam.com/software/FLI-Installer.exe](http://www.fli-cam.com/software/FLI-Installer.exe) instead?

---

### Post by Greg Mueller on 2008-01-23
Tried it from the FLI link (Finger Lake Instruments) and got this

greg@OB-1:~$ wine "/home/greg/Desktop/FLI-Installer.exe" 
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\cfitsio.dll") not found
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library libfli.dll (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\FLIFocuserATL.dll") not found
err:module:import_dll Library MFC71.DLL (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\FLIFocuserATL.dll") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\FLIFocuserATL.dll") not found
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:newdev:UpdateDriverForPlugAndPlayDevicesA Stub! USB\VID_0f18&PID_0001 C:\Program Files\Finger Lakes Instrumentation\Drivers\fliusbnt.inf 0x00000000
greg@OB-1:~$

---

### Post by Greg Mueller on 2008-01-23
What is
" pipe r = 0 count = 0 !"
that it keeps failing to read?

---

### Post by denali on 2008-01-23
> **Greg Mueller said:**
> What is
" pipe r = 0 count = 0 !"
that it keeps failing to read?

My understanding of advapi is it has to do with cryptography.  Take that with a grain of salt, tho.

---

### Post by denali on 2008-01-23
> **Greg Mueller said:**
> Tried it from the FLI link (Finger Lake Instruments) and got this

```
greg@OB-1:~$ wine "/home/greg/Desktop/FLI-Installer.exe" 
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\cfitsio.dll") not found
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library libfli.dll (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\FLIFocuserATL.dll") not found
err:module:import_dll Library MFC71.DLL (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\FLIFocuserATL.dll") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\FLIFocuserATL.dll") not found
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:newdev:UpdateDriverForPlugAndPlayDevicesA Stub! USB\VID_0f18&PID_0001 C:\Program Files\Finger Lakes Instrumentation\Drivers\fliusbnt.inf 0x00000000
greg@OB-1:~$
```

This indicates that some required Microsoft DLLs (MFC71.dll and MSVCR71.dll) are missing.  When I get home, I'll take apart the FLI Installer package to see if they're included.

---

### Post by Greg Mueller on 2008-01-23
I started one of my windows computers and found msvcr71.dll in several loacations, one of which was the Maxim DL V4 subdirectory. I copied it and put it in the same subdirectory in the wine C drive and got this when I tried to install from the terminal

greg@OB-1:~$ wine start "/media/cdrom1/FLI Installation Files/FLI Installation Files/Setup.Exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:start:wmain Option 'L"/cdrom1/FLI Installation Files/FLI Installation Files/Setup.Exe"' not recognized
Start a program, or open a document in the program normally used for files with that suffix. 
Usage: 
start [options] program_filename [...] 
start [options] document_filename 

Options: 
/M[inimized] Start the program minimized. 
/MAX[imized] Start the program maximized. 
/R[estored]  Start the program normally (neither minimized nor maximized). 
/W[ait]      Wait for started program to finish, then exit with its exit code. 
/L           Show end-user license. 

start.exe version 0.2 Copyright (C) 2003, Dan Kegel 
Start comes with ABSOLUTELY NO WARRANTY; for details run with /L option. 
This is free software, and you are welcome to redistribute it 
under certain conditions; run 'start /L' for details. 
greg@OB-1:~$ 


at least that error message is no longer there

---

### Post by denali on 2008-01-23
Try running it without start.

---

### Post by Greg Mueller on 2008-01-23
greg@OB-1:~$ wine "/media/cdrom1/FLI Installation Files/FLI Installation Files/Setup.Exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet

Copyright 2004 Vincent B&#65533;ron
greg@OB-1:~$

---

### Post by denali on 2008-01-23
I just realized something.  The missing DLL complaints came from trying to install [http://www.fli-cam.com/software/FLI-Installer.exe](http://www.fli-cam.com/software/FLI-Installer.exe).  Does it install now?

---

### Post by Greg Mueller on 2008-01-23
I tried something new...
I plugged in the camera and filter wheel and powered them up then did this...

greg@OB-1:~$ greg@OB-1:~$ wine "/media/cdrom1/FLI Installation Files/FLI Installation Files/Setup.Exe"
bash: greg@OB-1:~$: command not found
greg@OB-1:~$ fixme:spoolsv:serv_main (0 (nil))
bash: syntax error near unexpected token `0'
greg@OB-1:~$ err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
bash: err:advapi:service_get_status: command not found
greg@OB-1:~$ Usage:
bash: Usage:: command not found
greg@OB-1:~$   Install a product:
bash: Install: command not found
greg@OB-1:~$     msiexec {package|productcode} [property]
bash: productcode}: command not found
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
greg@OB-1:~$     msiexec /i {package|productcode} [property]
bash: productcode}: command not found
err:msi:copy_package_to_temp failed to copy package L"{package"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"{package"
greg@OB-1:~$     msiexec /a package [property]
err:msi:copy_package_to_temp failed to copy package L"package"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"package"
greg@OB-1:~$   Repair an installation:
bash: Repair: command not found
greg@OB-1:~$     msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
bash: o: command not found
bash: d: command not found
bash: e: command not found
bash: a: command not found
bash: u: command not found
bash: m: command not found
bash: s: command not found
bash: c: command not found
bash: productcode}: command not found
bash: v]: command not found
Unknown option "[" in Repair mode
greg@OB-1:~$   Uninstall a product:
bash: Uninstall: command not found
greg@OB-1:~$     msiexec /x {package|productcode} [property]
bash: productcode}: command not found
err:msi:copy_package_to_temp failed to copy package L"{package"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"{package"
greg@OB-1:~$   Advertise a product:
bash: Advertise: command not found
greg@OB-1:~$     msiexec /j[u|m] package [/t transform] [/g languageid]
bash: m]: command not found
Unknown option "[" in Advertise mode
greg@OB-1:~$     msiexec {u|m} package [/t transform] [/g languageid]
bash: m}: command not found
greg@OB-1:~$   Apply a patch:
bash: Apply: command not found
greg@OB-1:~$     msiexec /p patchpackage [property]
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"patchpackage"
greg@OB-1:~$     msiexec /p patchpackage /a package [property]
fixme:msi:MsiApplyPatchW Only reading target products from patch
greg@OB-1:~$   Modifiers for above operations:
bash: Modifiers: command not found
greg@OB-1:~$     msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
bash: !]: event not found
greg@OB-1:~$     msiexec /q{|n|b|r|f|n+|b+|b-}
bash: b: command not found
bash: n: command not found
The program 'r' is currently not installed.  You can install it by typing:
sudo apt-get install littler
bash: r: command not found
bash: f: command not found
bash: n+: command not found
bash: b+: command not found
bash: b-}: command not found
Unknown option "L"{"" for UI level
greg@OB-1:~$   Register a module:
bash: Register: command not found
greg@OB-1:~$     msiexec /y module
Unable to load dll L"module"
greg@OB-1:~$   Unregister a module:
bash: Unregister: command not found
greg@OB-1:~$     msiexec /z module
Unable to load dll L"module"
greg@OB-1:~$   Display usage and copyright:
bash: Display: command not found
greg@OB-1:~$     msiexec {/h|/?}
bash: /?}: No such file or directory
greg@OB-1:~$ NOTE: Product code on commandline unimplemented as of yet
bash: NOTE:: command not found
greg@OB-1:~$ 
greg@OB-1:~$ Copyright 2004 Vincent B&#65533;ron
bash: Copyright: command not found
greg@OB-1:~$ greg@OB-1:~$ 
bash: greg@OB-1:~$: command not found
greg@OB-1:~$ 
greg@OB-1:~$ sudo apt-get install littler
[sudo] password for greg:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  atlas3-base libg2c0 libgfortran2 r-base-core
Suggested packages:
  atlas3-3dnow atlas3-sse atlas3-sse2 refblas3 lapack3 ess r-doc-info r-doc-pdf r-doc-html r-mathlib r-base-html r-base-latex
Recommended packages:
  r-recommended r-base-dev
The following NEW packages will be installed:
  atlas3-base libg2c0 libgfortran2 littler r-base-core
0 upgraded, 5 newly installed, 0 to remove and 12 not upgraded.
Need to get 16.7MB of archives.
After unpacking 51.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libg2c0 1:3.4.6-6ubuntu2 [50.4kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe atlas3-base 3.6.0-20.6 [6275kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libgfortran2 4.2.1-5ubuntu4 [198kB]                                                 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe r-base-core 2.5.1-1 [10.1MB]                                                    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe littler 0.0.8-1 [24.2kB]                                                        
Fetched 16.7MB in 1m49s (152kB/s)                                                                                                 
Preconfiguring packages ...
Selecting previously deselected package libg2c0.
(Reading database ... 200228 files and directories currently installed.)
Unpacking libg2c0 (from .../libg2c0_1%3a3.4.6-6ubuntu2_i386.deb) ...
Selecting previously deselected package atlas3-base.
Unpacking atlas3-base (from .../atlas3-base_3.6.0-20.6_i386.deb) ...
Selecting previously deselected package libgfortran2.
Unpacking libgfortran2 (from .../libgfortran2_4.2.1-5ubuntu4_i386.deb) ...
Selecting previously deselected package r-base-core.
Unpacking r-base-core (from .../r-base-core_2.5.1-1_i386.deb) ...
Selecting previously deselected package littler.
Unpacking littler (from .../littler_0.0.8-1_i386.deb) ...
Setting up libg2c0 (1:3.4.6-6ubuntu2) ...

Setting up atlas3-base (3.6.0-20.6) ...

Setting up libgfortran2 (4.2.1-5ubuntu4) ...

Setting up r-base-core (2.5.1-1) ...
Setting R_PAPERSIZE_USER default to 'letter'

Setting up littler (0.0.8-1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
greg@OB-1:~$ 





It installed a bunch of files. I am going to see if anything works now, I just wanted to get this "on paper" before it disappeared from the terminal

---

### Post by denali on 2008-01-23
I'm fairly certain it's not going to work, based on the output.  It appears the install package has a built-in script that freaked out wine.

Let's try this.  Copy Setup.Exe to the harddrive and rename it to Setup.msi.  Then execute:

wine start Setup.msi

What does it do?

---

### Post by Greg Mueller on 2008-01-23
I copied msvcr71.dll to the FLI subdirectory and now "FLI Grab" will start up in wine!
It still can't seem to find the camera though, but at least the app is starting


greg@OB-1:~$ wine "/home/greg/.wine/drive_c/Program Files/Finger Lakes Instrumentation/FLIGrab.exe"
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\cfitsio.dll") not found
err:module:import_dll Library cfitsio.dll (which is needed by L"C:\\Program Files\\Finger Lakes Instrumentation\\FLIGrab.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Finger Lakes Instrumentation\\FLIGrab.exe" failed, status c0000135
greg@OB-1:~$  wine "/home/greg/.wine/drive_c/Program Files/Finger Lakes Instrumentation/FLIGrab.exe"
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
greg@OB-1:~$

---

### Post by Greg Mueller on 2008-01-23
I can run the program (FLIgrab.exe) and the first thing it wants is to know where the camera is plugged in. It has an option to "scan" for the camera and I tried that, but it does not show the camera.

The latest run from the terminal

greg@OB-1:~$ wine "/home/greg/.wine/drive_c/Program Files/Finger Lakes Instrumentation/FLIGrab.exe"
fixme:spoolsv:serv_main (0 (nil))
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
greg@OB-1:~$ 

guess I'll try to track down
" /dev/snd/seq"   next

---

### Post by Greg Mueller on 2008-01-23
found it

greg@OB-1:~$ sudo modprobe snd-seq
[sudo] password for greg:
greg@OB-1:~$ 
greg@OB-1:~$ 


greg@OB-1:~$  wine "/home/greg/.wine/drive_c/Program Files/Finger Lakes Instrumentation/FLIGrab.exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
greg@OB-1:~$ 


still can't see the camera

---

### Post by denali on 2008-01-23
The command I'm about to provide you will generate a LOT of debug messages.  In order to prevent from spamming the forum, I'm going to send you a private message on the forums with my email address.

```

$ echo quit | WINEDEBUG=+relay wine "/home/greg/.wine/drive_c/Program Files/Finger Lakes Instrumentation/FLIGrab.exe" >& error.log;
$ tail -n 100 filename.out > report_file

```

Send me a copy of report_file and I'll see if anything stands out to me.

---

### Post by Greg Mueller on 2008-01-23
I guess I'm doing something wrong. I can't get it to output anything

---

### Post by denali on 2008-01-23
It should have created a file called report_file.  Is it 0 bytes in length?

---

### Post by Greg Mueller on 2008-01-23
I'm not seeing it anywhere

---

### Post by denali on 2008-01-23
> **Greg Mueller said:**
> I'm not seeing it anywhere

When you entered the command, did you type in the $?  If you did, please leave it out, with my apologies.

---

### Post by Greg Mueller on 2008-01-23
first I did this

greg@OB-1:~$ echo quit | WINEDEBUG=+relay wine "/home/greg/.wine/drive_c/Program Files/Finger Lakes Instrumentation/FLIGrab.exe" >& error.log;

It ran the program, then I exited and did this


greg@OB-1:~$ tail -n 100 filename.out > report_file
tail: cannot open `filename.out' for reading: No such file or directory

---

### Post by denali on 2008-01-23
> **Greg Mueller said:**
> first I did this

greg@OB-1:~$ echo quit | WINEDEBUG=+relay wine "/home/greg/.wine/drive_c/Program Files/Finger Lakes Instrumentation/FLIGrab.exe" >& error.log;

It ran the program, then I exited and did this


greg@OB-1:~$ tail -n 100 filename.out > report_file
tail: cannot open `filename.out' for reading: No such file or directory

Yep, thats my fault.  It should have been:

tail -n 100 error.log > report_file

---

### Post by Greg Mueller on 2008-01-23
Where do I look for the report?

---

### Post by denali on 2008-01-23
It should be in the directory where you executed the command.  Based on the command lines you've posted, my best guess would be your home directory.

---

