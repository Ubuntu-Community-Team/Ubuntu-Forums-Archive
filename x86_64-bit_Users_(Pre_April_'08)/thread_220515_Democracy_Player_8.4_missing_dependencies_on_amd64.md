---
title: "Democracy Player 8.4 missing dependencies on amd64"
date: 2006-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by dbenhur on 2006-07-21
I tried installing with force-architecture, but the package is missing dependencies.

[Ubuntu Democracy package download]("http://www.getdemocracy.com/downloads/ubuntu.php"), [Installation Notes]("https://develop.participatoryculture.org/projects/democracy/wiki/LinuxNotes")

Has anyone succeeded in getting the 32bit player installed under amd64?

I've opened a ticket at [ParticipatoryCulture.org]("http:////develop.participatoryculture.org/projects/democracy/ticket/3174")

---

### Post by Kilz on 2006-07-21
> **dbenhur said:**
> I tried installing with force-architecture, but the package is missing dependencies.

[Ubuntu Democracy package download]("http://www.getdemocracy.com/downloads/ubuntu.php"), [Installation Notes]("https://develop.participatoryculture.org/projects/democracy/wiki/LinuxNotes")

Has anyone succeeded in getting the 32bit player installed under amd64?

I've opened a ticket at [ParticipatoryCulture.org]("http:////develop.participatoryculture.org/projects/democracy/ticket/3174")

[I have a page]("http://www.tghc.org/staticpages/index.php/32bitapplications") that will show you how to install 32bit applications and take care of the dependancies.

---

### Post by professor_b on 2006-07-22
I installed the missing dependency, and then installed with --force-architecture, but I get this problem:

```

Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 14, in ?
    import config
  File "/usr/lib/python2.4/site-packages/democracy/config.py", line 8, in ?
    import eventloop
  File "/usr/lib/python2.4/site-packages/democracy/eventloop.py", line 17, in ?
    import database
ImportError: /usr/lib/python2.4/site-packages/democracy/database.so: cannot open shared object file: No such file or directory

```

The odd part? The file that it says is missing is there, at that path. Weird.

(I also have all of the goodies installed that Kilz recommends)

---

### Post by Kilz on 2006-07-22
> **professor_b said:**
> I installed the missing dependency, and then installed with --force-architecture, but I get this problem:

```

Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 14, in ?
    import config
  File "/usr/lib/python2.4/site-packages/democracy/config.py", line 8, in ?
    import eventloop
  File "/usr/lib/python2.4/site-packages/democracy/eventloop.py", line 17, in ?
    import database
ImportError: /usr/lib/python2.4/site-packages/democracy/database.so: cannot open shared object file: No such file or directory

```

The odd part? The file that it says is missing is there, at that path. Weird.

(I also have all of the goodies installed that Kilz recommends)
You could try to copy that over to /lib32, if not you may want to setup [a chroot]("http://www.ubuntuforums.org/showthread.php?t=157412"). 32bit Media players can be a real pain to get running.

---

### Post by dlanor78 on 2006-08-06
Anyone get this working (hopefully without chroot)?

---

### Post by darkshadow on 2006-08-07
This looks like a neat program so I tried getting it but decided to try it but decided on a native 64bit compile so I got it compiled from the latest source tarball but when I run it shows up but crashes when I do something. (sometimes just blinks for a second then crashes).

It says "No such file or directory" in the output so I must be missing something so how would I find out what it is.



DTV: Starting up Democracy Player
DTV: Version:  0.8.5
DTV: Revision: unknown
DTV: Loading preferences...
DTV: Restoring database...
DTV: Recomputing filters...
DTV: Spawning global feed dtv:manualFeed
DTV: Spawning global feed dtv:search
DTV: Spawning global feed dtv:searchDownloads
DTV: Spawning Channel Guide...
DTV: Spawning global feed dtv:directoryfeed
DTV: Spawning auto downloader...
DTV: Spawning idle notifier
DTV: idle notifier running
DTV: Displaying main frame...
DTV: Starting event loop thread
*** Launching Democracy Downloader Daemon ****
*** Daemon ready ***
DTV: updating the Guide
INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

System error?:: No such file or directory
downloader: connection closed -- quitting
Shutting down downloaders...

---

### Post by darkshadow on 2006-08-07
Well I got it figured out I had to remove j2re1.4 not just make sun-java5 the default. I am downloading my first video and this program seems fun,

My suggestion just compile it from source. I had to use synaptic for some dependencies but it was not that hard. (Then again I have done some Linux From Scratch" installs so it may be a little harder for some people to figure out the dependencies. I will help with what I can if you try compiling

---

### Post by babwe on 2006-10-05
> **dlanor78 said:**
> Anyone get this working (hopefully without chroot)?

this worked for me :KS 
[http://www.ubuntuforums.org/showthread.php?t=269951](http://www.ubuntuforums.org/showthread.php?t=269951)

---

