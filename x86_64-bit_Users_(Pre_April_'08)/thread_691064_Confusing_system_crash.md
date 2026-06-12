---
title: "Confusing system crash"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by A.T on 2008-02-08
Hi

My system: Xubuntu, Gutsy, fglrx (ati x1900xtx), amd64.

The problem: My system crashes randomly after ~(10-15 minutes ) of usage in X.

What happens:
The monitor receives 'no signal' and then goes to standby mode (red light). The system doesn't respond to any keyboard commands, sound output quits a few seconds after the monitor goes to standby mode.
Only a hard reboot works.

I have tried the following:
Upgrade to the latest fglrx drivers
Boot system with options noacpi and acpi = off from grub
Disable screensavers. 
Remove gnome-screensaver and xscreensaver.
Set "0" in ServerFlags for options such as suspendtime,Offtime,Blanktime,Standbytime.
Disable DPMS, blanking, expose using xset
Upgrade to the latest motherboard bios.
Disabled atieventd
Confirmed that the CPU temp is stable
Compared GPU fan speed (based on the noise) from windows and concluded that the fan speed is running at 100% in xubuntu too, hence it's not a overheating problem.
Read my monitor manual and set correct refresh rate and resolution.
Tried to run the system with the VESA drivers.

I should also point out,:

The system doesn't crash when I run recovery mode(console), but as soon as i start X (startx) from recovery mode. The problem occurs.

The system shows me correct and accurate information when i run fglrxinfo, glxinfo , glxgears and  flg_glxgears.

The system works in windows, hence I draw the conclusion that there cannot be any hardware faults.

When i run 'aticonfig --lsp'. I only receive one mode (default) there is no underclock or overclock mode from the output.


I've looked through syslog, xorg logs after a hardreboot , but I cannot find any errors.

I am thankful for any suggestions on solving this problem.

---

### Post by shane2peru on 2008-02-10
Wow, this sounds like a serious problem!  I know this isn't a direct solution, but have you tried installing Gnome to see if you have the same problems in Gnome.  This has got to be a config file somewhere that is causing this problem, and if it is only xfce desktop, then we can narrow it down some, if it is an xserver problem, that isn't good.  Try Gnome.  The fact that you can boot into recovery mode is good, we just need to narrow it down more.  Also do you have anything like Compiz, Beryl installed or running?  

Shane

---

