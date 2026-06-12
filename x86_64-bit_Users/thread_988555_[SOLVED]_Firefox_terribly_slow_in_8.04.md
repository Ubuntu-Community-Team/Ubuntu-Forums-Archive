---
title: "[SOLVED] Firefox terribly slow in 8.04"
date: 2008-11-20
forum: x86 64-bit Users
---

### Post by WildeBeest on 2008-11-20
Ever since last week, firefox has been extremely slow. I mean minutes to load a web site.
Goes grey.

I have 64 bit Hardy and firefox 3.0.4.

Any help would really be appreciated.

By the way, Opera runs great, except the occasional crashes.
No issues with pidgin or skype.

---

### Post by aysiu on 2008-11-20
Have you tried closing Firefox, running ```
firefox -profile-manager
``` and trying out a fresh profile? If Opera, Pidgin, and Skype are working well, it's clearly not a network issue, which makes me think it's Firefox profile-related.

---

### Post by WildeBeest on 2008-11-20
Haven't tried that.

I'll get you the output as soon as it finishes loading.
It has 22 tabs to load. Before last week, these tabs would load in less than 2 minutes.

I using Opera for this.

---

### Post by WildeBeest on 2008-11-20
Here's a portion of the output.

Don't know how to put it in a list box.

GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
*** NSPlugin Viewer  *** ERROR: NP_Initialize() get args: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Message timeout
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return

---

### Post by aysiu on 2008-11-20
All that NSPlugin stuff makes me think this is somehow Flash-related.

How did you install Flash, and which version of it did you install?

I'm also going to move this to the 64-bit forum, because I suspect it has more to do with the 64-bit Flash than it has to do with networking.

---

### Post by WildeBeest on 2008-11-21
I have version 10 installed.

It was installed by this: [http://www.howtoforge.com/installing-adobe-flash-10-on-a-64bit-ubuntu-8.04](http://www.howtoforge.com/installing-adobe-flash-10-on-a-64bit-ubuntu-8.04)

Youtube wasn't working for me so I followed a thread on here which worked, but I had no sound.

So I followed psyke83's HOWTO: PulseAudio Fixes & System-Wide Equalizer Support, that fixed the sound issue and also reinstalled flash 10.

I believe since then I had the firefox issue.

---

### Post by spiregrain on 2008-11-21
Hi,

What stage does firefox appear to stall at?  I'm finding that mine stalls at the "Looking up (website)" stage.  I can't work out why.

---

### Post by WildeBeest on 2008-11-21
Mine stalls with the message at the bottom "waiting for [www.xxx.yyy](www.xxx.yyy).

---

### Post by steveneddy on 2008-11-21
First try this web site:

[http://howto.helpero.com/howto/Speed-Up-Firefox_31.html](http://howto.helpero.com/howto/Speed-Up-Firefox_31.html)

Next you might try uninstalling anything Flash.

If that helps, try the new 64 bit alpha version of Flash for Linux.

Look here for more Flash help.

[http://ubuntuforums.org/showpost.php?p=6216638&postcount=3](http://ubuntuforums.org/showpost.php?p=6216638&postcount=3)

I use 64 bit Ubuntu and these are the fixes I made and FF3.04 runs very well on my machine.

---

### Post by buyyourall3 on 2008-11-22
Hello, are you looking for Nokia and other [chinese mobile phones](http://www.buyyourall.com)?  pleease click [[color=Red]**HERE**[/color]](http://www.buyyourall.com) you can find lots of [chinese mobile phones ](http://www.buyyourall.com)there

---

### Post by WildeBeest on 2008-11-22
I followed this thread to fix the problem.

[http://ubuntuforums.org/showthread.php?t=985479](http://ubuntuforums.org/showthread.php?t=985479)

It definitely was flash related.

---

### Post by steveneddy on 2008-11-23
> **WildeBeest said:**
> I followed this thread to fix the problem.

[http://ubuntuforums.org/showthread.php?t=985479](http://ubuntuforums.org/showthread.php?t=985479)

It definitely was flash related.

Sweet! that's great.

Let's mark this as solved.

---

