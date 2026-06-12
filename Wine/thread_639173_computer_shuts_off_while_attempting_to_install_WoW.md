---
title: "computer shuts off while attempting to install WoW"
date: 2007-12-12
forum: Wine
---

### Post by tysonh on 2007-12-12
I was following the How-to install WoW with wine and my computer just   shuts off about mid install.

Its not over heating.  I wasn't doing anything but the install so I can't figure out whats causing it.

---

### Post by hikaricore on 2007-12-12
You'll need to be more specific about your hardware in this case I'm betting.

---

### Post by tysonh on 2007-12-13
I have a older abit kv600 motherboard and a nvidia 256mb 6200 series video card.  AMD Socket A 2800 cpu.  I ran WoW fairly easy on XP.  I'm using wine 0.9.5.0

---

### Post by hikaricore on 2007-12-13
Have you installed the proper video drivers for your card?
Also please post any errors you might be seeing when running the installer from a terminal before the crash.

---

### Post by tysonh on 2007-12-13
Yes I have the nvidia drivers installed.  The installation process goes very smooth until the pc just turns off.  There is no freezing or hanging or crashing it just turns off.

I followed the "how to" to the letter so I don't think  the installation is the problem.  When it just turns off I don't really have a way of seeing what went wrong.  

I was hoping someone else may have had the same problem.

---

### Post by hikaricore on 2007-12-13
You could check the contents of:

/var/log/syslog
/var/log/syslog.0

After such a crash to see if anything from around the time looks abnormal.

---

### Post by tysonh on 2007-12-13
okay im going to start the install again and see if I can get it to shut off then I'll post the out put from the log.

---

### Post by tysonh on 2007-12-13
when i start the install from terminal this pops up.  I don't know what it means or if its causing a problem.

war@war-desktop:~/Desktop/wow_install$ fixme:font:CreateScalableFontResourceW (1,0xd0e108,0xd0a208,(nil)): stub
fixme:bidi:mirror stub: mirroring of characters not yet implemented

---

### Post by tysonh on 2007-12-13
PC just shut off again I checked the log this time and found this:

Dec 13 00:07:37 war-desktop kernel: [    5.148000] Marking TSC unstable due to: possible TSC halt in C2.

Dec 13 00:07:37 war-desktop kernel: [   37.205733] VP_IDE: not 100%% native mode: will probe irqs later

Dec 13 00:07:39 war-desktop NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running!

Dec 12 21:15:56 war-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  

Dec 13 00:07:37 war-desktop kernel: No module symbols loaded - kernel modules not enabled.

these are the only things I really noticed but I don't really know what im looking for..

---

### Post by tysonh on 2007-12-13
i looked in a debug log and it said after it restarted I guess that it recovered from a hard disk fail.

Will hard disk failure cause your computer to shut off?

---

