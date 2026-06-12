---
title: "~8 minutes to log in to X"
date: 2006-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by svref on 2006-02-25
After I supply my uname and password it takes a long time, say 8 minutes, for ubuntu to log me in.  During that time the display is just the black->brown top->bottom gradient.

I dinked around with the various gdm "session" options, and the only one that logs me in in a timely way is the "failsafe xterm".

/var/log/messages is uninformative to me.

Nothing is sucking up cpu cycles during the long pause.

I had a fresh install of 5.10 on an ibook.  Then I noticed the updates notifier, and installed the updates.  This included a new linux kernel, so I had to reboot.  That's when this problem first manifested itself.

Any ideas on how to fix it?

---

### Post by Trab on 2006-02-25
this has happend to me before...
next time you log out close everything else running (like firefox, gaim, anything cept for panels and other essentials...) when u get to the log out screen, click the save current setup box...
this fixed my issue...

---

### Post by svref on 2006-02-25
Hey, on 3rd look at the logs, it looks like it might be gconfd's fault:```

Feb 25 14:14:29 localhost gconfd (dave-4952): starting (version 2.12.0), pid 4952 user 'dave'
...
several messages similar to the one below
...
Feb 25 **14:14:29** localhost gconfd (dave-4952): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb 25 **14:14:29** localhost gconfd (dave-4952): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Feb 25 14:16:33 localhost gconfd (root-4818): GConf server is not in use, shutting down.
Feb 25 14:16:33 localhost gconfd (root-4818): Exiting
Feb 25 **14:20:52** localhost gconfd (dave-4952): Resolved address "xml:readwrite:/home/dave/.gconf" to a writable configuration source at position 0
```

The interesting thing is that the last gconfd resolution comes 6 mintues after its similar-looking buddies, and that's about the amount of time the login takes.  Hm...

____

I tried the save-session idea - no luck.  :(

---

### Post by svref on 2006-02-25
I had to reinstall from scratch to fix this problem, but fix it I did.

I think the problem was that I skipped the "configure network interface(s)" step of installation.  As a result my /etc/hosts was not set up in a way amenable to gnome.

What I had:
127.0.0.1 localhost localhost.localdomain umlaut umlaut.mydomain.net

What the configurator did:
127.0.0.1 localhost localhost.localdomain
192.168.24.14 umlaut umlaut.mydomain.net

Never mind the fact that this is WRONG, since that network interface may or may not be on depending on where the laptop is, its worth it if I can log in in under 5 minutes.

---

