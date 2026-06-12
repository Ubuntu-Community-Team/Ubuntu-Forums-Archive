---
title: "Yes, its another steam problem...."
date: 2008-04-26
forum: Wine
---

### Post by goMON on 2008-04-26
Well, I've seen loads of Steam problems about on the net, and a lot on the Forum...
But, most I either don't understand, or it's not the same problem as mine....

Basically, I have downloaded the latest Steaminstall.msi, and tried opening it with Wine, but nothing happens...
I suspect it's because its msi, and not exe...
If so, does anyone know where I can get a exe file for Steam from?

If you are going to tell me to use a Terminal, please be very simple, or as simple as you can, because I know absolutely nothing about them...

Thanks :) Richard..
P.S. Sorry for posting yet another steam problem...

---

### Post by Swarms on 2008-04-26
Cd into the right directory, write ```
wine start SteamInstall.msi
``` What do you get?

---

### Post by andrebrait on 2008-04-26
Poor guy...

---

### Post by goMON on 2008-04-26
Hello, I get the following:
```

preloader: Warning: failed to reserve range 00000000-60000000
wine: creating configuration directory '/home/richard/.wine'...
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Could not load Mozilla. HTML rendering will be disabled.
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: '/home/richard/.wine' created successfully.
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

```

But, I don't know if I done it right anyway..
I done the following:
```

richard@Richard-PC:~$ dir Desktop
ies4linux-2.99.0  ies4linux-ie6.desktop  SteamInstall.msi

```

If that is completely and utterly wrong, then I'm sorry, as I said, I have no idea how to use the Terminal, I've been searching Google, but couldn't find anything :confused:

---

### Post by goMON on 2008-04-26
Woooh, I found out how to change directory hehe :)
The setup has started :) Thanks

---

### Post by Swarms on 2008-04-27
No problem mate, you are here to learn, like I am. :)
If you need any other help you are free to ask again.

---

### Post by goMON on 2008-04-27
Thanks :D

---

### Post by andrebrait on 2008-04-27
To fix the memory bug, see this link

[http://ubuntuforums.org/showthread.php?t=770262](http://ubuntuforums.org/showthread.php?t=770262)
If Steam don't display any page and installing the gecko engine only show you a grey page (Try the command **wine iexplore [http://winehq.com](http://winehq.com)**. It should prompt for the Gecko engine installation, which is needed by Steam.), install the lib32nss-mdns package.

BTW, ies4linux 2.99.0.1 solves the blank screen bug, but ies4linus has serious issues. Last time I tested, it wasn't installing an important update, downloading an important cab and wasn't installing Flash, so you'd better wait for a new version.

And ies4linux does't install IE in the same bottle wine do, to install things in the same bottle of ies4linux, you have to type **export WINEPREFIX=~/.ies4linux/ie6 wine *EXE NAME HERE***. (NOT RECOMMENDED)

---

