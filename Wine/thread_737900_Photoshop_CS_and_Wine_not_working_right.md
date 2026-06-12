---
title: "Photoshop CS and Wine not working right?"
date: 2008-03-28
forum: Wine
---

### Post by jhyland87 on 2008-03-28
Hey, so I have wine, and it works good so far, I goto install photoshop, and I try to run setup.exe with wine, and I get these errors

Error: .\AutoPlay\main.ini
>click ok
Error: MAIN_FILE_VERSION
>click ok
Error: PRODUCT_REGISTRY_PARENT
>Click ok
Error: PRODUCT_REGISTRY_KEY


who has had these errors?

---

### Post by asdfoo on 2008-03-28
are you using the latest version of wine? 0.9.58? 

to check, type wine --version

[http://winehq.org/download](http://winehq.org/download)

If you still have problems, it might be a good idea to post on the winehq forum [http://forum.winehq.org](http://forum.winehq.org)

---

### Post by jhyland87 on 2008-03-28
its this.. 

administrator@IT-justin:~$ wine --version
wine-0.9.58


ill check it out. thanks

---

### Post by phil90 on 2008-03-28
Hello 

Have you tried this If you have Photoshopt CS2.

if not select your version of photoshop here: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)


    *  You shouldn't have to copy Photoshop from Windows; just install it under Wine by running its Setup.e*xe. (To run a .exe under wine, you have to doubleclick it, right click and choose "Run with Wine", or run it from the commandline using the 'wine' command, depending on how your Linux distribution integrates Wine.)
    * Never use a cracked version of Photoshop.
    * Never run Wine as root.
    * Use a recent version of Wine (0.9.54 or later).
    * Before installing Photoshop, install the Times32 font by downloading and running one of the corefont installers, e.g. [http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe) , else Photoshop will abort with a "hardware error" [see bug 9623]*
    * Some UI elements might use a too-small font. In CS2, you can fix this with Edit / Preferences / General, and change UI Font Size from Small to Medium.
    * The Clone tool uses the ALT key in a way that conflicts with many window managers. Here's how to fix that:
          o Ubuntu: System / Windows / Movement Key, and pick "Super" instead of "Alt".
          o Kubuntu: K / System Settings / Look and Feel / Windows / Movement Key, and pick "Super" instead of "Alt"
          o Suse with Gnome: Computer / Control Center / Look and Feel / Windows / Movement Key, and pick "Super" instead of "Alt"
          o Fedora 8 Gnome: System / Preferences / Look and Feel / Windows / Movement Key, and pick "Super" instead of "Alt
          o Suse with KDE: Gecko / Favorites / Configure Desktop / Desktop / Window Behavior / Window Actions / "Inner Window, Titlebar & Frame" , and pick "Meta" instead of "Alt"
          o Earlier KDE: KDE Control Center / Desktop / Window Behavior / Window Actions / turn off the alt-combos.
          o Earlier Gnome: Destop Preferences / Keyboard Layout / Options / Alt/Win key behavior [expand tree]; select new behavior for modifier keys


It was taken from Wine 's website. 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631)

---

### Post by jhyland87 on 2008-03-28
Interesting.. its not a cracked version

ill download the cs3 trial and see if that works.

---

### Post by michaelzap on 2008-03-28
I remember that I had trouble installing Photoshop from a folder with an accented character and spaces in the name. When I renamed the folder it installed fine. I guess that Wine doesn't like that.

---

### Post by jhyland87 on 2008-03-28
if thats the case I think its linux in general.. I remember I couldnt use spaces in my files hosted on yahoo, or when I used ubuntu server..

ill try both of those when I go home, thanks a lot guys

---

### Post by jhyland87 on 2008-03-30
so I tried it, and I get the same errors.. :(

---

### Post by michaelzap on 2008-03-30
Try reinstalling it using [Wine Doors]("http://www.wine-doors.org/").

---

### Post by jhyland87 on 2008-03-31
dude.. that worked great!! thanks!

---

### Post by Rowdy73 on 2008-04-06
> **michaelzap said:**
> Try reinstalling it using [Wine Doors]("http://www.wine-doors.org/").

AWESOME!!

Many thanks.

---

### Post by MemoryDump on 2008-04-18
I'm trying to get CS2 working as well, however I get this error once I excute the application:

"An error has been detected with a required application library and the product connot continue. Please reinstall the applications."

Any ideas?
I'm using the latest wine.
- tried installing with and without winedoors.
- applied the 9.02 patch
- when I tried installing with winedoors the installer repaired my previous installation.

:(

---

### Post by MemoryDump on 2008-04-18
> **MemoryDump said:**
> I'm trying to get CS2 working as well, however I get this error once I excute the application:

"An error has been detected with a required application library and the product connot continue. Please reinstall the applications."

Any ideas?
I'm using the latest wine.
- tried installing with and without winedoors.
- applied the 9.02 patch
- when I tried installing with winedoors the installer repaired my previous installation.

:(

I just tried to re-install everything from scratch and run Photoshop from a shell. Here are the results I get before it crashes:

```
~/.wine/drive_c/Program Files/Adobe/Adobe Photoshop CS2$ wine Photoshop.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:keyboard:UnregisterHotKey (0x10026,99): stub
fixme:keyboard:RegisterHotKey (0x10026,99,0x00000000,27): stub
fixme:font:WineEngRemoveFontResourceEx :stub
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:ole:CoResumeClassObjects stub
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:ntdll:RtlpWaitForCriticalSection section 0x1502750 "?" wait timed out in thread 0051, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x1502750 "?" wait timed out in thread 0051, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x1502750 "?" wait timed out in thread 0051, blocked by 0009, retrying (60 sec)
```

help! :confused:

EDIT: it seems this is a known bug with Hardy.
check out: [http://bugs.winehq.org/show_bug.cgi?id=12592](http://bugs.winehq.org/show_bug.cgi?id=12592)
what fixed it for me was: [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
hopefully this gets fixed in the near future :)

---

### Post by nrub on 2008-04-30
The fix found at [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem), solved the same problem for me! Thanks!

---

### Post by Prefix100 on 2008-05-02
Fixed it for me too, tyvm.

---

### Post by Roundel on 2008-05-30
The above fix worked great for Photoshop (CS2), but I am still having some trouble with Imageready on Hardy.  When I try to open it, I get the error message "Could not fully start the application. An unknown error has occurred".  It seems I am [_[COLOR="RoyalBlue"]not the only one with this problem[/COLOR]_]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631").  Does anyone have any suggestions?

Thanks!

---

### Post by Roundel on 2008-06-12
bump

---

### Post by Momof9Blessings on 2008-06-14
> **michaelzap said:**
> I remember that I had trouble installing Photoshop from a folder with an accented character and spaces in the name. When I renamed the folder it installed fine. I guess that Wine doesn't like that.

what is an accented character?

I have been searching and trying to get cs2 to work

I have the latest of everything

---

### Post by michaelzap on 2008-06-14
> **Momof9Blessings said:**
> what is an accented character?


A character with an accent, e.g., é, á, etc.

Try installing Photoshop via Wine Doors. That worked well for me.

---

### Post by Momof9Blessings on 2008-06-14
it did not work either - it tries to start....  I have added all types of fonts - I have done "repair"....  Would have anything to do with the "trial version"

---

### Post by kumo99 on 2008-07-05
> **michaelzap said:**
> A character with an accent, e.g., é, á, etc.

Try installing Photoshop via Wine Doors. That worked well for me.

Does "Save for web" works for you when you installed ps using wine-doors?

---

