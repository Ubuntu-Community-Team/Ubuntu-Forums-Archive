---
title: "Odd Last-Exit error"
date: 2006-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sykil on 2006-07-10
Compiled [last-exit](http://www.o-hand.com/~iain/last-exit/) and everything went fine, but when I go to start it, I get an error that I can't understand (which happens a good bit :P):
```
stephen@astarael:~$ last-exit

Unhandled Exception: GConf.NoSuchKeyException: Key '/apps/lastexit/first_run' not found in GConf
in <0x00113> GConf.Client:Get (System.String key)
in <0x0002f> LastExit.Config:get_FirstRun ()
in <0x000fc> LastExit.Driver:Main (System.String[] args)
```
Any help?

---

### Post by twisted_steel on 2006-07-12
What version of last-exit did you compile?  I recall having that error from an older version or an early release in CVS.  The current version is 1.0 and can be downloaded from this page: [http://www.o-hand.com/~iain/last-exit/]("http://www.o-hand.com/%7Eiain/last-exit/").  If you are using this newer version and still have the problem, I believe I added the missing key to gconf.  To do this, open up the editor from a terminal:
```
stephen@astarael:~$ gconf-editor
``` Navigate to apps -> lastexit if it exists. Once you have apps -> lastexit selected, right-click in the right pane and select New Key.  Name it first_run, with a type of boolean.  Now you should be able to open up last-exit without any problems.

If this doesn't work, you may want to take a look at this thread: [http://ubuntuforums.org/showthread.php?t=149018](http://ubuntuforums.org/showthread.php?t=149018), which talks about fixing that error.

---

