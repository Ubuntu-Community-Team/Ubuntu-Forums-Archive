---
title: "Gnome Power Manager &amp; Related Issues"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by Melk79 on 2008-05-15
I don't think this is a 64-bit issue, but I'm running 64-bit so I'll start here.  G-P-M issues seem to be pretty common and after some searching I found many similar troubles, but no exact matches.  This is the situation:

- I was trying to fix an issue where my screen would turn white with a movable pointer after resume from sleep.  Troubleshooting that led me to posts claiming Nvidia as the culprit.  The fix included adding a third part repository to SPM and installing some updates (mostly for Compiz).  This did seem to fix the white screen issue.

- The trouble is now G-P-M (or perhaps ACPI, etc.) doesn't respond correctly.  If I unplug the AC cord, the icon will change to battery and the brightness will dim (which is good), but if you hold the mouse over the icon, it still thinks it's on AC power.  So, my setting for the computer to sleep on lid close while on battery isn't working.  As a workaround, I changed it to sleep on lid close while on AC power.

- With the cord unplugged, I reinstalled G-P-M and all ACPI packages from SPM.  That "fixed" the problem and the computer knew it was on battery.  However, once I plugged and unplugged the AC, the same issue reocurred.

This is kind of annoying because I want to use my laptop as a laptop... carry it around, make it sleep and wake up, etc.  Does anyone have any thoughts or can anyone point me to the right place?  Google searches on Ubuntu, Power, Battery, ACPI, etc return tons of results, but no exact matches.

---

### Post by Melk79 on 2008-05-16
Bump

---

### Post by Yellow Pasque on 2008-05-16
See if you can find any useful settings in apps -> gnome-power-manager when you run:
```
gconf-editor
```

---

### Post by Melk79 on 2008-05-16
Now that I've looked at those settings, perhaps this is an ACPI or HAL issue.  Also, for reasons unknown, now my computer is basically operating backwards.  Unplug the power and it brightens the screen (but changes to the battery icon).  Plug it in and it dims.  I tried reinstalling all HAL, ACPI and GPM packages, but it didn't fix the problem.

---

### Post by markbuntu on 2008-05-21
It is definitely ACPI:

May 21 06:31:07 mark-desktop kernel: [16866.500474] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
May 21 06:31:07 mark-desktop kernel: [16866.595036] ACPI: PCI interrupt for device 0000:02:03.0 disabled
May 21 06:31:07 mark-desktop kernel: [16866.778838] Syncing filesystems ... done.
May 21 06:31:07 mark-desktop kernel: [16866.778913] PM: Preparing system for mem sleep
May 21 06:31:23 mark-desktop kernel: [16866.779131] Freezing user space processes ... (elapsed 0.00 seconds) done.
May 21 06:31:23 mark-desktop kernel: [16866.780034] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
May 21 06:31:23 mark-desktop kernel: [16866.874461] PM: Entering mem sleep
May 21 06:31:23 mark-desktop kernel: [16866.874463] Suspending console(s)
May 21 06:31:23 mark-desktop kernel: [16866.938723] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
May 21 06:31:23 mark-desktop kernel: [16866.938880] sd 1:0:0:0: [sdb] Stopping disk
May 21 06:31:23 mark-desktop kernel: [16867.283183] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May 21 06:31:23 mark-desktop kernel: [16867.283359] sd 0:0:0:0: [sda] Stopping disk
May 21 06:31:23 mark-desktop kernel: [16868.451406] ACPI handle has no context!
May 21 06:31:23 mark-desktop kernel: [16868.451579] parport_pc 00:07: disabled
May 21 06:31:23 mark-desktop kernel: [16868.456729] ACPI handle has no context!
May 21 06:31:23 mark-desktop kernel: [16868.487155] ACPI: PCI interrupt for device 0000:01:00.1 disabled
May 21 06:31:23 mark-desktop kernel: [16868.487185] ACPI handle has no context!
May 21 06:31:23 mark-desktop kernel: [16868.503161] [fglrx] firegl_gps_setpowerdown .
May 21 06:31:23 mark-desktop kernel: [16868.639668] ACPI: PCI interrupt for device 0000:01:00.0 disabled
May 21 06:31:23 mark-desktop kernel: [16868.639920] ACPI: PCI interrupt for device 0000:00:14.5 disabled
May 21 06:31:23 mark-desktop kernel: [16868.640161] ACPI: PCI interrupt for device 0000:00:13.2 disabled
May 21 06:31:23 mark-desktop kernel: [16868.654882] ACPI: PCI interrupt for device 0000:00:13.1 disabled
May 21 06:31:23 mark-desktop kernel: [16868.654935] ACPI: PCI interrupt for device 0000:00:13.0 disabled
May 21 06:31:23 mark-desktop kernel: [16868.655026] ACPI: PCI interrupt for device 0000:00:12.0 disabled
May 21 06:31:23 mark-desktop kernel: [16868.671070] Disabling non-boot CPUs ...
May 21 06:31:23 mark-desktop kernel: [    0.272028] Back to C!
May 21 06:31:23 mark-desktop kernel: [    0.297451] ACPI: Unable to turn cooling device [ffff8100bb23d220] 'off'

---

### Post by Melk79 on 2008-05-21
Thanks.  I tried reinstalling those ACPI packages again and again.  Rebooted a few times with various methods (cord in restart, cord out restart, lid down, lid up, etc.) Eventually it healed itself. Unfortunately it wasn't my most precise troubleshoot, so I don't have any exact steps to report back.  It was one of those problems that drives you crazy enough, you just try anything.  Thanks again.

---

