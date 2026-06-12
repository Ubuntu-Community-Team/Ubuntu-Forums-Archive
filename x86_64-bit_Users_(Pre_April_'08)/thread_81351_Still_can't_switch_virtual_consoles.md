---
title: "Still can't switch virtual consoles"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by calum on 2005-10-24
For months I've been unable to switch virtual consoles using Ctrl+Alt+F<n> on my Powerbook G4.  Have tried the suggestions given [here]("http://ubuntuforums.org/showthread.php?t=55661") but to no avail.   The consoles exist, because I can switch to them using 'sudo chvt <n>'.  Same problem whether or not I choose (in powerprefs) to require the Fn key to use the brightness/volume controls on F1-F5.

Anyone got any other ideas?

---

### Post by Joe_lurker on 2005-10-24
What happens when you press Ctrl+Alt+F1?  Nothing?  Blank screen?

You can try disabling 'splash' and 'quiet' from /etc/yaboot.conf.  Just comment out the 'append=quiet splash' line.  You will have to run 'sudo ybin' to reload the boot loader.  Reboot and see if that helps.

Joe

---

### Post by calum on 2005-10-25
[QUOTE=Joe_lurker]What happens when you press Ctrl+Alt+F1?  Nothing?  Blank screen?[/QUOTE]

Nothing at all.  Sounds like [http://bugzilla.ubuntu.com/show_bug.cgi?id=17921]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17921"), I guess I'll follow it up there.

---

### Post by calum on 2005-10-28
[QUOTE=calum]Nothing at all.  Sounds like [http://bugzilla.ubuntu.com/show_bug.cgi?id=17921]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17921"), I guess I'll follow it up there.[/QUOTE]

FWIW, one of two things appears to have fixed this for me: upgrading to Dapper, and/or changing "UseFBDev" from true to false in my xorg.conf.

---

