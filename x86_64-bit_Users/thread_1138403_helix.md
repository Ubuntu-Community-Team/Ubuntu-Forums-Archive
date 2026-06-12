---
title: "helix"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by jayanramesh on 2009-04-26
Dear buddies,
Helix player is not working in jaunty 64 bit.Could anybody help me to fix this?

Thank you.

---

### Post by John.Michael.Kane on 2009-04-26
> **jayanramesh said:**
> Dear buddies,
Helix player is not working in jaunty 64 bit.Could anybody help me to fix this?

Thank you.

What exactly is not working with Helix? 

Also forum members are going to need a bit more info, such as errors given etc.

To see if any errors are given. Try starting the program from the terminal using the below command.

```
hxplay
```

---

### Post by jayanramesh on 2009-04-27
Dear John.Michael.Kane,
I 've got the reply from terminal as 'Segmentation fault".Even after double click on helix icon it refuses to start at all.
Thank you.

---

### Post by Arup on 2009-04-27
> **jayanramesh said:**
> Dear John.Michael.Kane,
I 've got the reply from terminal as 'Segmentation fault".Even after double click on helix icon it refuses to start at all.
Thank you.

Did you install from the repos? I use the realplayer from the repos on my Jaunty x64 and it works fine, I also tried Helix and it had no issues as well.

---

### Post by jayanramesh on 2009-04-27
Dear Arup,
I installed it from synaptic package manager.

---

### Post by locketine on 2009-05-02
> **jayanramesh said:**
> Dear Arup,
I installed it from synaptic package manager.
Thank you

Did that fix the problem? Why are you saying thank you? I installed helix from Applications>Add/Remove and it segfaults while it's starting up.

---

### Post by alex.pujols on 2009-05-04
Same issues here....

System  - Jaunty 9.04 64
Repos    - OS Default
PKGs     - Helix Player / Helix Mozilla Plugin
Browser - Firefox 3.0.10

** A manual launch with hxplay fails with the following output from dmesg.

[  523.622511] hxplay.bin[4122]: segfault at 40 ip 00007f67c9f79a2a sp 00007fffd49e69f0 error 4 in libpthread-2.9.so[7f67c9f71000+17000]


** When trying to play a *.ram file from Real Networks test site

Firefox crashes and clears my bookmarks and browser history.


I'm in the process as at looking as libpthread and some of the existing symbolic links.  It's looking like this is a bug.  Can anyone confirm or provide some assistance.

Alex

---

### Post by indigodog on 2009-05-07
> **alex.pujols said:**
> 


  It's looking like this is a bug.  Can anyone confirm or provide some assistance.

Alex



Very similar bug here in 32bit - Fx crashes, but with the crashed Fx session restored all settings are intact. 

Package: Helix installed via official repos Synaptics manager UI
System: 9.04 32bit, patched to the minute

Symptoms:  Crash any instance of hxplay, either as a plugin which crashes Fx or the standalone hxplay.

Used the real test files from here: [http://service.real.com/test/](http://service.real.com/test/) to test the plugin behaviour.
Ran a terminal opening of hxplay - reported "segmentation fault" and wouldn't begin.

---

### Post by Ferannia on 2009-05-14
It seems to me it is not only a bug in AMD64, the same issue I got here on an older Athlon i386 compatible; installed helix-player_1.0.9-0ubuntu6_i386
which segfaults with a message (from syslog):
```
[657396.263229] hxplay.bin[3419]: segfault at 53656d71 ip b78899e0 sp bfd55824 error 4 in libpthread-2.9.so[b7882000+15000]
```

It can't even start up, much less play anything. It can't start by command line, it can't start from menu.

Logged as root, unable to start up, it segfaults again just as when starting the helix regularly as a user.

However, when starting up Helix with sudo, it does bring up a configuration dialog, and after configuring it plays an audio .ogg stream, but returning to user will crash the helix again.

Frustrated with this, I uninstalled Jaunti's helix package and mozilla plugin, downloaded a precompiled .bin installation archive Helix 11.0.0.4052(Gold) from [https://player.helixcommunity.org](https://player.helixcommunity.org) - installation quick and smooth, and the player works out of the box.

---

### Post by ronacc on 2009-05-15
same result with karmic koala alpha1 . Hxplay segfaults in libthread .

---

### Post by Pale Chapter on 2009-05-17
Same problem; I'm new to Linux, but I know enough to get a bit faint when I see a segfault--and it seems like everyone using AMD 64 is getting the same problem. Compatibility issues, maybe?

---

### Post by pixel :-) on 2009-05-17
A dirty work around

dig up an other version of 
libpthread-2.9.so

By version i mean, officially the same, but internals are different

override the lib just for that executable with

/lib/ld-linux.so.2 --library-path PATH EXECUTABLE

or the bellow wrapper

 #!/bin/sh
  export LD_LIBRARY_PATH=PATH_OF_LIB:$LD_LIBRARY_PATH
  exec /usr/bin/my_program.orig $*

Since i'm not using helix, its up to you to do the actual digging for the lib.

---

### Post by talent03 on 2009-06-04
I would just like to comment real quickly about this. I think it may be with the install process because I do get the seg fault but when I run it as root, for example with sudo, the program works. That is all the time I could give it right now, so I hope somebody can report this bug and work it out more.

---

### Post by Pale Chapter on 2009-06-04
Hey, it works--but now it segfaults every time I turn it *off*. Which is a marked improvement, but...

---

