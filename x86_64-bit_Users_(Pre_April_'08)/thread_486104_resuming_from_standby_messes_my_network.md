---
title: "resuming from standby messes my network"
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by carniolus on 2007-06-27
I accidentally found out this issue:
When I standby my system it all goes fine.
But when I resume, my network is real messy.
Normally I have eth0 as my primary networking device and none other.
But when I resume this device disappears and instead of it I now have eth1.
I use broadband internet connection.

Any ideas?

ps:its not bothering me, I'm just curios.

---

### Post by carniolus on 2007-06-29
anyone?

---

### Post by carniolus on 2007-06-29
none really?

---

### Post by digitalbenji on 2007-06-29
I believe this is a known issue.  I have the same problem.  Hopefully someone will post some easy fix.

---

### Post by alextud on 2007-06-30
Same to me, I have a nvidia network card that use forcedeth driver. I have added MODULES_WHITELIST="forcedeth" in file /etc/default/acpi-support, and it works. Also after suspending I'm unable to burn cd/dvd.
If its help, my /etc/default/acpi-support looks like:

ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="forcedeth"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false #true is default

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=false

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false #true is default

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=false

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
#LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

---

### Post by carniolus on 2007-06-30
Interesting mine is nvidia too...
I'll try this and come back with results.

---

