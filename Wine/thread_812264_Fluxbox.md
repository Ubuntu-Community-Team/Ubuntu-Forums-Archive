---
title: "Fluxbox"
date: 2008-05-29
forum: Wine
---

### Post by hvacr on 2008-05-29
Does anyone know how I would go about putting a menu entry for wine into fluxbox.

---

### Post by kerry_s on 2008-05-29
how do you have your menus set up?

if it's stock> sudo update-menus

---

### Post by hvacr on 2008-05-29
I am using my own menu. Even if I run the above command and check /etc/X11/fluxbox/fluxbox-menum wine is not there.

---

### Post by kerry_s on 2008-05-29
> **hvacr said:**
> I am using my own menu. Even if I run the above command and check /etc/X11/fluxbox/fluxbox-menum wine is not there.

do you have the gui for wine installed?
sudo apt-get install xwine

---

### Post by hvacr on 2008-05-29
sudo apt-get install xwine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xwine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  wine
E: Package xwine has no installation candidate


I have wine installed and working.

---

### Post by kerry_s on 2008-05-29
do-> apt-cache search wine

there's a gui for it, wine by itself is command line. i can't remember what it's called in ubuntu, in debian it's xwine. you want the gui for wine in ubuntu. other just do it like the manpage says & put that in your menu:

[exec] (program-name) {wine /path/to/program}

> 

man wine (1) - run Windows programs on Unix
NAME

wine - run Windows programs on Unix
SYNOPSIS

wine program [arguments ... ]
wine --help
wine --version

For instructions on passing arguments to Windows programs, please see the PROGRAM/ARGUMENTS section of the man page.
DESCRIPTION

wine loads and runs the given program, where the program is a DOS, Windows 3.x, or Win32 executable (x86 binaries only).

For debugging wine, use winedbg instead.

For running CUI executables (Windows console programs), use wineconsole instead of wine. This will display all the output in a separate windows (this requires X11 to run). Not using wineconsole for CUI programs will only provide very limited console support, and your program might not function properly.

When invoked with --help or --version as the only argument, wine will simply print a small help message or its version respectively and exit.
PROGRAM/ARGUMENTS

The program name may be specified in DOS format ( C:WINDOWSSOL.EXE) or in Unix format ( /msdos/windows/sol.exe ). You may pass arguments to the program being executed by adding them to the end of the command line invoking wine (such as: wine notepad C:TEMPREADME.TXT). Note that you need to '' escape special characters (and spaces) when invoking Wine via a shell, e.g.

wine C:Program FilesMyPrgtest.exe

ENVIRONMENT VARIABLES

wine makes the environment variables of the shell from which wine is started accessible to the windows/dos processes started. So use the appropriate syntax for your shell to enter environment variables you need.

WINEPREFIX
    If set, the content of this variable is taken as the name of the directory where wine stores its data (the default is $HOME/.wine ). This directory is also used to identify the socket which is used to communicate with the wineserver. All wine processes using the same wineserver (i.e.: same user) share certain things like registry, shared memory, and config file. By setting WINEPREFIX to different values for different wine processes, it is possible to run a number of truly independent wine processes. 
WINESERVER
    Specifies the path and name of the wineserver binary. If not set, Wine will try to load /usr/bin/wineserver, and if this doesn't exist it will then look for a file named "wineserver" in the path and in a few other likely locations. 
WINELOADER
    Specifies the path and name of the wine binary to use to launch new Windows processes. If not set, Wine will try to load /usr/bin/wine, and if this doesn't exist it will then look for a file named "wine" in the path and in a few other likely locations. 
WINEDEBUG
    Turns debugging messages on or off. The syntax of the variable is of the form [class][+/-]channel[,[class2][+/-]channel2]. 

class is optional and can be one of the following: err, warn, fixme, or trace. If class is not specified, all debugging messages for the specified channel are turned on. Each channel will print messages about a particular component of wine. The following character can be either + or - to switch the specified channel on or off respectively. If there is no class part before it, a leading + can be omitted. Note that spaces are not allowed anywhere in the string.

Examples:

WINEDEBUG=warn+all
    will turn on all warning messages (recommended for debugging).
WINEDEBUG=warn+dll,+heap
    will turn on DLL warning messages and all heap messages.
WINEDEBUG=fixme-all,warn+cursor,+relay
    will turn off all FIXME messages, turn on cursor warning messages, and turn on all relay messages (API calls).
WINEDEBUG=relay
    will turn on all relay messages. For more control on including or excluding functions and dlls from the relay trace look into the [Debug] section of the wine configuration file. 

For more information on debugging messages, see the Running Wine chapter of the Wine User Guide.

WINEDLLPATH
    Specifies the path(s) in which to search for builtin dlls and Winelib applications. This is a list of directories separated by ":". In addition to any directory specified in WINEDLLPATH, Wine will also look in /usr/lib/wine. 
WINEDLLOVERRIDES
    Defines the override type and load order of dlls used in the loading process for any dll. The default is set in the configuration file. There are currently two types of libraries that can be loaded into a process' address space: Native windows dlls ( native ), wine internal dlls ( builtin ). The type may be abbreviated with the first letter of the type ( n, b ). Each sequence of orders must be separated by commas. 

Each dll may have its own specific load order. The load order determines which version of the dll is attempted to be loaded into the address space. If the first fails, then the next is tried and so on. Multiple libraries with the same load order can be separated with commas. It is also possible to use specify different loadorders for different libraries by separating the entries by ";".

The load order for a 16-bit dll is always defined by the load order of the 32-bit dll that contains it (which can be identified by looking at the symbolic link of the 16-bit .dll.so file). For instance if ole32.dll is configured as builtin, storage.dll will be loaded as builtin too, since the 32-bit ole32.dll contains the 16-bit storage.dll.

Examples:

WINEDLLOVERRIDES="comdlg32,shell32=n,b"

    Try to load comdlg32 and shell32 as native windows dll first and try the builtin version if the native load fails. 
WINEDLLOVERRIDES="comdlg32,shell32=n;c:foobarbaz=b"

    Try to load the libraries comdlg32 and shell32 as native windows dlls. Furthermore, if an application request to load c:foobarbaz.dll load the builtin library baz. 
WINEDLLOVERRIDES="comdlg32=b,n;shell32=b;comctl32=n"

    Try to load comdlg32 as builtin first and try the native version if the builtin load fails; load shell32 always as builtin and comctl32 always as native. 
DISPLAY
    Specifies the X11 display to use. 

FILES

/usr/bin/wine
    The wine program loader. 
/usr/bin/wineconsole
    The wine program loader for CUI (console) applications. 
/usr/bin/wineserver
    The wine server 
/usr/bin/winedbg
    The wine debugger 
/usr/lib/wine
    Directory containing wine's shared libraries 
$WINEPREFIX/dosdevices
    Directory containing the DOS device mappings. Each file in that directory is a symlink to the Unix device file implementing a given device. For instance, if COM1 is mapped to /dev/ttyS0 you'd have a symlink of the form $WINEPREFIX/dosdevices/com1 -> /dev/ttyS0.
    DOS drives are also specified with symlinks; for instance if drive D: corresponds to the CDROM mounted at /mnt/cdrom, you'd have a symlink $WINEPREFIX/dosdevices/d: -> /mnt/cdrom. The Unix device corresponding to a DOS drive can be specified the same way, except with '::' instead of ':'. So for the previous example, if the CDROM device is mounted from /dev/hdc, the corresponding symlink would be $WINEPREFIX/dosdevices/d:: -> /dev/hdc. 

AUTHORS

wine is available thanks to the work of many developers. For a listing of the authors, please see the file AUTHORS in the top-level directory of the source distribution.
COPYRIGHT

wine can be distributed under the terms of the LGPL license. A copy of the license is in the file COPYING.LIB in the top-level directory of the source distribution.
BUGS

A status report on many applications is available from [http://appdb.winehq.org](http://appdb.winehq.org). Please add entries to this list for applications you currently run.

Bug reports may be posted to Wine Bugzilla [http://bugs.winehq.org](http://bugs.winehq.org) If you want to post a bug report, please read the file documentation/bugs.sgml in the wine source to see what information is necessary

Problems and suggestions with this manpage please also report to [http://bugs.winehq.org](http://bugs.winehq.org)
AVAILABILITY

The most recent public version of wine can be downloaded from [http://www.winehq.org/download](http://www.winehq.org/download)

The latest snapshot of the code may be obtained via CVS. For information on how to do this, please see [http://www.winehq.org/cvs](http://www.winehq.org/cvs)

WineHQ, the wine development headquarters, is at [http://www.winehq.org](http://www.winehq.org). This website contains a great deal of information about wine.

For further information about wine development, you might want to subscribe to the wine mailing lists at [http://www.winehq.org/forums](http://www.winehq.org/forums)
SEE ALSO

wineserver(1), winedbg(1)



---

### Post by BLTicklemonster on 2008-05-29
Do you mean you want to have wine come up with drop downs you can browse like it does under gnome in applications, wine, etc?

No idea.

But if you want to have a wine section in your menu and use wine to bring up specific programs, then I found this thread helpful:

[http://ubuntuforums.org/showpost.php?p=1772880&postcount=13](http://ubuntuforums.org/showpost.php?p=1772880&postcount=13)

```
      [submenu] (Wine)
        [exec] (uTorrent) {wine "/home/paul/other/utorrent.exe"}
        [exec] (EAC) {wine ~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe}
        [end]

```

like that. Two instances showing how to bring up exe files from within wine and from without.

Hope this is helpful. And if it's the former you want, I can't wait to see. 

Huh, you know you could make it have wine with submenus for different things and just tailor it to look like it does in gnome...


edit: just re read the previous post. I think he means

bill@bill-desktop:~$ winefile

edit:
taking it a bit further:

[[IMG]http://img155.imageshack.us/img155/7480/winefluxsz2.th.png[/IMG]](http://img155.imageshack.us/my.php?image=winefluxsz2.png)

should give you and idea what you want. You can see the edited menu file with wine added, and how it looks in menu, and the wine file browser window thingy it brings up.

That what you were looking for?

(hope so, I had fun making all that work and making the screen shot lol)

Huh, conky's messed up. When did that happen?

---

### Post by kerry_s on 2008-05-29
ahh, winefile, that's the gui that shows all the programs you installed with wine, then you just select and launch?

---

### Post by hvacr on 2008-05-30
Thanks very much everyone, this gets me going in the direction I want.

BLTicklemonster

It is a beautiful screen shot.  :)

---

### Post by BLTicklemonster on 2008-05-30
:) Glad to be of service!

And yes, kerry, I think you have to right click and choose launch.

---

