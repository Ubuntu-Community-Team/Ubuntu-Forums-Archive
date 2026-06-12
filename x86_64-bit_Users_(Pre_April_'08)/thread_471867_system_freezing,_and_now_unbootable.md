---
title: "system freezing, and now unbootable"
date: 2007-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by antiemptyv on 2007-06-12
**overview**
i had been running a perfectly fine system up until a few days ago.  i'm not sure if it was an upgrade or what, but all of a sudden, i began having problems with feisty freezing during wireless config and then while booting.

**background**
i booted up my computer and the orange progress bar stopped at about 75% and didn't budge ever.  not knowing anything else to do, i reinstalled.  the new reinstall booted up fine.  thinking that the freezing situation was due to some upgrade i did, i did not upgrade anything while i searched these and other forums for a solution.  i couldn't find any problem that described mine exactly.  then upon reboot, it happened again--orange bar making it to about 75% the ceasing.  OK, this time reinstall.  i vowed to not upgrade anything or reboot until further progress.

except this time when i configured my wireless connection, it froze.  i had been needing to turn off roaming mode and manually put in the ESSID.  I'm using a Linksys WMP54G PCI Card.  the system was completely frozen, no mouse motion or keys were recognized.  reboot.  orange bar 75%...again.  reinstalled again.  same thing.  reinstalled again, boot into Same GNOME Terminal.  i ran network-manager, configured the connection, restarted the networking, and i connected to the internet again.  finally.  i thought maybe that if i booted into GNOME now with it configured the networking would be working fine.  nope.

**hopefully helpful details**
OK so i booted again into Recovery Mode.  the freezing is happening right after this output:

```

*Checking file systems...
fsck 1.40-WIP (14-NOV-2006)
*Mounting local filesystems...
*Activating swapfile swap...
*Configuring Network interfaces...
*Setting up console font and keymap...
[41.891303] BUG: soft lockup detected on CPU#0!
```

i repeated this a few times, and it freezes after the same messages, but the number in brackets are never the same.  this happens if i boot with kernel 2.6.20-16-generic (recovery mode) and kernel 2.6.20-15-generic (recovery mode).

**help?**
i hope there's some out there.  thanks!

---

### Post by dannyboy79 on 2007-06-12
i found the solution right here within the forums, a search would be something you will want to try before posting next time. Don't take what I have said the wrong way either, it's merely an FYI.

[http://ubuntuforums.org/showthread.php?t=251944&page=9](http://ubuntuforums.org/showthread.php?t=251944&page=9)

---

### Post by antiemptyv on 2007-06-12
well, i have added "blacklist rt61" to "/etc/modprobe.d/blacklist"

it has booted up.  but now how do i connect to a wireless network?  it's not listed in the network admin anymore.

my card is, however, recognized when i run lspci:

01:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI

---

### Post by antiemptyv on 2007-06-12
ahh, i used ndiswrapper to install the driver that came with the linksys wmp54g pci card.  it actually came with 2 drivers.  rt61 has been blacklisted, and i've installed the other one rt2500.  everything seems to be working fine.  [fingers crossed] 

thanks for the help on blacklisting the rt61 driver.

---

### Post by antiemptyv on 2007-06-13
ok.  i had a tiny scare of an incident.

i wasn't getting an internet connection, so i ran "/etc/init.d/networking restart" and found my system frozen again.  i rebooted, and the orange progress bar stuck ...again.  i was a little perturbed about this, as reinstalling has gotten a teensy bit old.

i rebooted into recovery mode fine the next time, and rebooted yet again, but regularly, the time after that.  aaaand everything seems to be fine now.

so if someone runs into this, don't be too alarmed.

---

