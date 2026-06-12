---
title: "Ubuntu PPC + UPS: how to auto-boot?"
date: 2005-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by mwnovak on 2005-11-28
I run a server installation (no x/gui) of Ubuntu 5.10 on an Apple G4 Cube.  It's a headless machine, and I use it as my personal web and file server.

I'd like to set up a UPS for the machine so it can shut down gracefully in the event of power failures.  I've found several good tutorials regarding UPS's under x86 Linux.  In particular, the following addresses apcupsd and Debian:  [http://update.itlab.musc.edu/node/126](http://update.itlab.musc.edu/node/126)

Here's my question: how can I configure my Mac to start up automatically when power is restored after a power failure?  All the x86-based tutorials indicate that BIOS settings control this behavior... is there an equivalent setting in the Apple openFirmware? some other way to do this?

Any help is greatly appreciated.

--MW

---

### Post by ssam on 2005-11-28
there is a setting in the mac os x control panel to reboot after a power failier. if you still have mac os x installed you could try that. i assume it store that setting in PRAM. you may be able to change the setting from the open firmware.

that might be enough info to help you find an answer.

otherwise if you have some electronics knowledge and a spare apple keyboard with a power key then you could probably work something out.

---

### Post by mwnovak on 2005-11-29
Okay, a little more digging trough the repositories led me to "powerpc-utils (1.1.3-16)" which includes an "autoboot" utility.  From the man page, autoboot is a "tool for setting/resetting servermode booting of PowerMacs."  This is exactly what I need, but...

...here's what I get when I run the utility:

```

mwnovak@myserver:~$ sudo autoboot on
autoboot: write returned -1

```

I can't find any information on "write returned -1", but I'm guessing it means the utility didn't work: when I kill/restore power to the machine, I still have to manually press the power button to get it running again.

Suggestions?

--MW

---

### Post by ssam on 2005-11-29
thats an intersting package, thanks for finding it.

try emailing the package maintainer,
```
sudo apt-cache show powerpc-utils
```

```
autoboot: write returned -1
```

yes, returning a non zero number is unix speak for error. but it could mean anything.

update:
read man nvsetenv, that might be more useful for modern (open firmware) macs.

```
sudo nvsetenv
```
prints out a list of all the variables (the last one on mine contains a ascii control character or something and mangles my terminal display, use "reset" to fix it.)

one of the values on mine is
```
auto-boot?=true
```
that could be what your after.

please be careful (maybe do some more research). i think making mistakes here could make your system very unbootable.

---

### Post by mwnovak on 2005-11-29
I emailed Rich Johnson, the listed maintainer for the autoboot utility.  Here's what he had to say:

> 
autoboot,  as currently implemented, only works on powermacs with
the CUDA peripheral controller.   These are older nubus and  pci
powermacs with an ADB.    It needs to be modified to support
powermacs with PMU99 chips (such as the Cube).    Unfortunatey, I
don't have such a machine running Linux, but I will poke around a bit
to see what I can find out.   I do know that it _can_ be done.  See
([http://www.versiontracker.com/dyn/moreinfo/macosx/19830](http://www.versiontracker.com/dyn/moreinfo/macosx/19830) and http://
[www.versiontracker.com/dyn/moreinfo/macosx/16555](www.versiontracker.com/dyn/moreinfo/macosx/16555))

You also point out another bug:  ''autoboot: write returned -1" is
neither friendly nor informative.   It should read more like
"Unsupported Machine"


As suggested by ssam, I'm going to do some research on the "nvsetenv" utility and see if there's any traction there.  I'll also see if I can find info about doing autoBoot via Open Firmware.

If I find anything useful, I'll post back here.

EDIT: I checked up on the auto-boot variable of nvsetenv.  "auto-boot = false" will cause the machine to boot directly into Open Firmware and wait for input; "auto-boot = true" lets the the boot process move through OF and actually load the OS.  That's not quite what I'm looking for... but it seems like there should be another OF variable that'll do the trick.  Updates to follow...  

--MW

---

### Post by mwnovak on 2005-11-29
A little more information ... might spark something.

As already mentioned, OSX has a feature called "Restart automatically after a power failure" that creates the behavior I'm looking for.  So I started messing with this option on my 10.4 Powerbook to see what I could learn.

I'm not sure that the "restart after power failure" behavior is actually happening through Open Firmware.  Here's what I did:

"nvram" seems to be the OSX counterpart to Ubuntu's "nvsetenv" utility: it can print or set OF variables.  To dump the OF variables into a text file, I ran: ```
nvram -p > pre.txt"
```  I then enabled OSX's "restart after power failure" option (Sys. Prefs. - Energy Saver - Options tab), before dumping the variables again: ```
nvram -p > post.txt
```  Then I compared the two files: ```
diff pre.txt post.txt
```The files were identical, indicating that the "restart after power failure" option didn't alter any of the OF variables returned by nvram.

"Restart after power failure" *is*, however, flagging the "autorestart" variable of pmset (the command-line power management tool under OSX).  I believe the analogous tools for Ubuntu are the apm and/or pmud packages... anyone know if either has a "restart after power failure" option?

--MW

---

### Post by mwnovak on 2005-11-29
Rich Johnson, the maintainer of the "autoboot" utility, pointed me in the right direction here...

**/proc/pmu/options** contains the following variable: **server_mode=0**

Setting that variable to "1" (**echo 'server_mode=1' > /proc/pmu/options**) allows the Cube to restart automatically after a power failure.

However, I still can't get this to work in the context of a UPS.  

Setting "server_mode=1" lets the machine restart when power returns after a power failure.  That is, when I pull the plug on the Cube while it's running (which is *such* a bad idea, I know), wait a bit, and plug it back in ... the machine automatically starts again.

Wonderful.

However, when I issue any type of graceful shutdown command ("shutdown -h now", "halt", "halt -f") and subsequently pull the plug ... the machine will not automatically start when I restore power at the plug.  I've even tried setting "HALT=halt" (instead of "poweroff") in /etc/default/halt.  No joy.

Though he didn't find a solution, I did at least find someone with the same problem: [http://lists.debian.org/debian-powerpc/2005/04/msg00019.html](http://lists.debian.org/debian-powerpc/2005/04/msg00019.html)

Does anyone have suggestions for an appropriate shutdown command that will halt the Cube without cutting power?

--MW

---

