---
title: "[SOLVED] error 22 with Diablo 2 running on wine 0.9.55"
date: 2008-02-17
forum: Wine
---

### Post by Colemanvt on 2008-02-17
So the main thing with this issue is I'm not getting anything when I run the video test so error 22 just states the fact that I don't have video capabilities for some reason and of course the game won't start... 

this is all I get when I run wine in the terminal..

```
colemanvt@CVT-Deskbuntu:~$ wine diablo 2
wine: could not load L"c:\\windows\\system32\\diablo.exe": Module not found
colemanvt@CVT-Deskbuntu:~$ fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!


```

Anyone have an idea

---

### Post by ekravche on 2008-02-17
try to disalbe 3d glide support. Make it run under direct 3d instead...

---

### Post by karth on 2008-02-17
> colemanvt@CVT-Deskbuntu:~$ wine diablo 2

Why is there a space between "diablo" and "2" ?

Wine enables the user to ommit the ".exe" part of the executable you intend to run, therefore it looks for diablo.exe, which is not, I think, the name of the diablo2 exe.

More, your command specifies a relative path, which suggests to the system that diablo.exe is in the current working directory (e.g. your home dir, or ~/ ). Try running it from it's real directory, i.e. .wine/drive_c/Program Files/Diablo 2/

---

### Post by Colemanvt on 2008-02-17
> **ekravche said:**
> try to disalbe 3d glide support. Make it run under direct 3d instead...

No clue how to do that actually :-\ I'm a newb face


> **karth said:**
> Why is there a space between "diablo" and "2" ?

Wine enables the user to ommit the ".exe" part of the executable you intend to run, therefore it looks for diablo.exe, which is not, I think, the name of the diablo2 exe.

More, your command specifies a relative path, which suggests to the system that diablo.exe is in the current working directory (e.g. your home dir, or ~/ ). Try running it from it's real directory, i.e. .wine/drive_c/Program Files/Diablo 2/

And I tried running it from the terminal from the install directory but I don't know how to type into the terminal the file path it doesn't seem to want to take what I put if there are spaces in between the folder names.

```
colemanvt@CVT-Deskbuntu:~$ wine /media/500GB irock/Wine Program Files/Diablo II/Diablo II.exe
wine: cannot find '/media/500GB'

```

See what I mean? :-(

---

### Post by happyhamster on 2008-02-17
- You can work around the spaces by putting the entire path between quotes.

- Try like this:

locate diablo -i

- It will look for files/folders called diablo, and when it finds something, it will show the full path.* Then just copy and paste that path and put it between quotes. (copy = select that line using the mouse, paste = click middle mouse button)

- For example, I have a game "Undying.exe". If I do a search:

locate undying.exe -i

- The result is:

/home/username/.wine/drive_c/Program Files/Clive Barker's Undying/System/Undying.exe

- So, in this case the command to navigate to the proper folder is:

cd "/home/username/.wine/drive_c/Program Files/Clive Barker's Undying/System/"


* If "locate diablo -i" didn't find anything, perhaps you need to update the database first (this could take a minute or so):

sudo updatedb

---

### Post by Colemanvt on 2008-02-17
nice thanks for that tidbit always kinda confused me a bit and I never found anything about the quotes whenever I googled the idea... so now this is what I get when I try and run d2

```
colemanvt@CVT-Deskbuntu:~$ wine "/media/500GB irock/Wine Program Files/Diablo II/Diablo II.exe"
err:aspi:SCSI_OpenDevice Failed to open device /dev/hda: Read-only file system
err:aspi:SCSI_OpenDevice Failed to open device /dev/hdc: No medium found
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg1: Permission denied
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg4: Permission denied
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg3: Permission denied
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg2: Permission denied
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg5: Permission denied
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
fixme:advapi:SetSecurityInfo stub
colemanvt@CVT-Deskbuntu:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x817ff0,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?   colemanvt@CVT-Deskbuntu:~$ wine "/media/500GB irock/Wine Program Files/Diablo II/Diablo II.exe"

```

I'm guessing maybe that I need to edit my xorg.conf and add in a resolution with a low bit rate? just a guess. Even if you guys think that's right I'm at a loss as to how to actually do that. >_<

---

### Post by happyhamster on 2008-02-17
> 
I'm guessing maybe that I need to edit my xorg.conf and add in a resolution with a low bit rate? just a guess. Even if you guys think that's right I'm at a loss as to how to actually do that. >_<
No, don't edit xorg.conf if you're not 100% sure how to or why. (And know how to repair things when the system breaks.)

---

### Post by happyhamster on 2008-02-17
> **Colemanvt said:**
> colemanvt@CVT-Deskbuntu:~$ wine "/media/500GB irock/Wine Program Files/Diablo II/Diablo II.exe"
I really don't understand what's going on here: is diablo already installed? Is it on a different harddrive?

---

### Post by Colemanvt on 2008-02-17
> **happyhamster said:**
> I really don't understand what's going on here: is diablo already installed? Is it on a different harddrive?

I installed it on a separate hard drive from that of my main file system. I just thought that would  be wise incase I need to format or something I would already have all the files set up and good to go and not have to reinstall diablo.

Do you think the fact that I made it install on another hard drive is what's giving me troubles?

---

### Post by happyhamster on 2008-02-17
> **Colemanvt said:**
> I installed it on a separate hard drive from that of my main file system.
Ok, that should be possible (never tried it myself though). But how did you install it? Did you install it onto that drive using wine (using wineprefixcreate), or is it a real windows install perhaps?

>  I just thought that would  be wise incase I need to format or something I would already have all the files set up and good to go and not have to reinstall diablo.
The way wine works is that it creates a mock windows drive in a hidden folder ".wine" in your home folder. When using wine you can always backup or delete that .wine folder if needed. Basically, as long as you *don't* run anything wine related as root (by using 'sudo') your'se safe to experiment.

> 
Do you think the fact that I made it install on another hard drive is what's giving me troubles?
I think that getting applications to run well under wine is difficult enough as it is. Anything that complicates things even more is, well, a challenge :)

---

### Post by Colemanvt on 2008-02-17
> But how did you install it? Did you install it onto that drive using wine (using wineprefixcreate), or is it a real windows install perhaps?


the one I'm working with I Installed under wine. I do actually have another installation of diablo that I installed using xp on another hard drive that's attached to the computer. It does the same thing...

> I think that getting applications to run well under wine is difficult enough as it is. Anything that complicates things even more is, well, a challenge :)

So you don't think I should do that huh? hrm.. maybe I should try installing again just using the default install path?... It seems a long one but worth a shot just the same right?

---

### Post by happyhamster on 2008-02-17
> **Colemanvt said:**
> the one I'm working with I Installed under wine.
But how did you get wine to install diablo on something else than the default c: drive? (sorry if I'm just dense)

> 
So you don't think I should do that huh? hrm.. maybe I should try installing again just using the default install path?... It seems a long one but worth a shot just the same right?
Well, you'll have to decide for yourself of course. I do think that a default install has several advantages: you can be sure that the used paths are correct (so that the game can find its own files) and all permissions, etc are correct (so that the game can access those files). The game might still not work (yet), but at least you have eliminated some variables.

Anyway, keep us informed.

---

### Post by Colemanvt on 2008-02-17
> But how did you get wine to install diablo on something else than the default c: drive? (sorry if I'm just dense)

I mapped one of my hard drives in wine and then I just re targeted the install path at the beginning of the d2 installation.


> Well, you'll have to decide for yourself of course. I do think that a default install has several advantages: you can be sure that the used paths are correct (so that the game can find its own files) and all permissions, etc are correct (so that the game can access those files). The game might still not work (yet), but at least you have eliminated some variables.

Anyway, keep us informed

Cool cool will do :-D

alright I tried re-installing still no go do I need to install some kinda of video driver support or something for wine? I mean I do have video support in ubuntu compiz works and all etc... :-\ wine hates me

---

### Post by happyhamster on 2008-02-17
> **Colemanvt said:**
> alright I tried re-installing still no go do I need to install some kinda of video driver support or something for wine? I mean I do have video support in ubuntu compiz works and all etc... :-\ wine hates me
Do you still get the same errors? And if you disable compiz (System-->Preferences-->Appearance-->Visual Effects-->none)

Could you post the output of:

cat /etc/X11/xorg.conf

---

### Post by Colemanvt on 2008-02-17
tried with no go on the visual effects off 

```
colemanvt@CVT-Deskbuntu:~$ cat /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV40 [GeForce 6800 GT]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "DELL 2005FPW"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV40 [GeForce 6800 GT]"
        Monitor         "DELL 2005FPW"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1680x1050"     "1280x1024"     "1152x864"     "1024x768"       "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

---

### Post by happyhamster on 2008-02-17
- Ok, try adding a line for 8 bits depth. First, make a copy of xorg.conf:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

- Open xorg.conf:

gksudo gedit /etc/X11/xorg.conf

- And add an extra  "'SubSection "Display"" in the screen section:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV40 [GeForce 6800 GT]"
        Monitor         "DELL 2005FPW"
        Defaultdepth    24

        SubSection "Display"
                Depth       8
                Modes           "1680x1050"     "1280x1024"     "1152x864"     "1024x768"       "800x600"       "720x400"       "640x480"
        EndSubSection

        SubSection "Display"
                Depth       24
                Modes           "1680x1050"     "1280x1024"     "1152x864"     "1024x768"       "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection
```

- So basically all you have to do is copy and paste the existing Subsection Display and add a line for Depth  8 and Depth  24. 

BTW. Make sure that you run the game from within its own folder (that's how most windows apps expect to run).
So, instead of: wine "/path-to/Diablo II.exe" use wine "Diablo II.exe" from inside its folder.

A lot more info (most of it applicable to older wine versions I think):
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=74](http://appdb.winehq.org/objectManager.php?sClass=application&iId=74)

---

### Post by Colemanvt on 2008-02-17
YES! that's what I was thinking! I bet you that's what it is gonna try that I just wanted someone to spell it out for me cause I'm a baby and didn't wanna mess up my xorg.conf I hear that's nasty hahahaha

Gonna try I'll edit with results

---

### Post by happyhamster on 2008-02-17
I forgot: after editing and saving xorg.conf, restart X by pressing ctrl-alt-backspace.

In case things went catastrophically wrong, you can use the backup xorg.conf from the console:

sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf

---

### Post by Colemanvt on 2008-02-17
WELL PLAYED SIR!

That was it all day long! worked like a charm I'm glad we changed that too cause I'm sure the same thing would've happened if I'd tried and installed another older game like starcraft.

---

### Post by happyhamster on 2008-02-17
Well, glad it worked :)  Let us know if anything else comes up.

---

