---
title: "X quits, how to debug?"
date: 2006-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rob_Frohne on 2006-02-05
Hi,
I would like to use qsstv, gpredict, glife and a bunch of other programs that all do the same thing when I start them, they crash my X session and I have to login again.  I have looked in the logs and found messages like this from the kdm log.

  SetClientVersion: 0 9
  QImage::convertDepth: Image is a null image
  QImage::smoothScale: Image is a null image
  *** glibc detected *** double free or corruption (out): 0x0fe88be0 ***

and in the message log:

localhost gconfd (root-5440) Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
localhost gconfd (root-5440) Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
localhost gconfd (root-5440) Exiting
localhost gconfd (frohro-5383) SIGHUP received, reloading all databases

and from the syslog

localhost gconfd (frohro-5383) SIGHUP received, reloading all databases
localhost gconfd (frohro-5383) Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
localhost gconfd (frohro-5383) Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
localhost gconfd (frohro-5383) Resolved address "xml:readwrite:/home/frohro/.gconf" to a writable configuration source at position 2
localhost gconfd (frohro-5383) Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
localhost gconfd (frohro-5383) Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
localhost gconfd (frohro-5383) Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
localhost gconfd (frohro-5383) Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
localhost gconfd (frohro-5383) Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
localhost kdm[4102] X server for display :0 terminated unexpectedly
localhost gconfd (frohro-5383) Received signal 15, shutting down cleanly
localhost gconfd (frohro-5383) Exiting
localhost kdm_greet[6447] Can't open default user face
localhost ivman Ivman started in system mode
localhost gconfd (frohro-6735) starting (version 2.12.0), pid 6735 user 'frohro'

It appears that glibc is crashing, but I am under the impression that practically everything uses glibc.  I want to know what is calling that library that causes the crash.  In OS X there is a crash log that you can examine to find out what called what, etc.  I'm new to Linux, and don't know how to find the next clue.  Can you point me in the right direction?

Some other notes that might help.  I started with Kubuntu and then loaded the ubuntu-desktop package.  I have these crashes in bothGnome or KDE, and even when I use the failsafe windowing environment.  

Thanks,

Rob

---

### Post by ssam on 2006-02-05
there might be something useful in
```
/var/log/Xorg.0.log
```

if you file a bug at [https://launchpad.net/malone](https://launchpad.net/malone) the the developers will probably talk you through getting some more detailed debugging info.

you should probably also post the contents of
```
/etc/X11/xorg.conf
```

have you turned on any extra xorg options such as composite? that can be quite buggy (should be a lot better in dapper)

---

### Post by Rob_Frohne on 2006-02-05
Thanks for the ideas.  I did examine XOrg.0.log, but I can't see anything in it that I'm sure corresponds to the crash.  I wish it would time stamp things, but it doesn't.

Rob

---

