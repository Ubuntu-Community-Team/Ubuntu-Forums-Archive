---
title: "firefox is freezing my system"
date: 2008-10-14
forum: x86 64-bit Users
---

### Post by coldcut on 2008-10-14
Hi you guys

I'm having problems with my newly installed Ubuntu 8.04 (64-bit).
Everytime I use Firefox(version 3) it freezes the system and the only solution is to hit the restart button on my computer. The system also freezes if I have been using Firefox and than I exit it and do something else, doesn't matter what.

Does anyone have a clue as to what I have to do to fix it, 'cause it's kind of annoying as you can imagine.

P.S. I'm from Iceland so please don't criticize my English if it's bad.

---

### Post by altonbr on 2008-10-14
Can you tell us the specifications of your computer? Does it at least have 256MB of RAM? Is it a Pentium III or newer?

There are light-weight browsers you can try, alternatives if you will, such as 'epiphany-browser', 'midori', 'kazehakase', etc.

Try those, and tell us what you think!

---

### Post by coldcut on 2008-10-14
I have a Q6600 processor, 4gb ram, 8800gts videocard so I don't think that my computer is the problem =/

given my specs do you still think I should try those light-weight browsers?

---

### Post by altonbr on 2008-10-14
> **coldcut said:**
> I have a Q6600 processor, 4gb ram, 8800gts videocard so I don't think that my computer is the problem =/

given my specs do you still think I should try those light-weight browsers?

Sorry mate, I have no experience with x86-64, I just saw your thread and thought I would help out!

I've used that same setup before (different mobo I'm sure) with x86 and it seemed to work fine. Maybe try running Firefox in a terminal (Applications > Accessories > Terminal) by running this:
```
firefox > firefox.log.txt 2>&1
```
Then run Firefox until it crashes and you have to reboot. When that's done, firefox.log.txt should hopefully have some information for you. If not, then you'll have to wait for a more experienced x86-64 user. Sorry.

Since you're working with Ubuntu 8.04 and not the unstable 8.10, we can't blame it on that either...

If it has anything to do with Flash, this thread might help: [http://sudan.ubuntuforums.com/showthread.php?t=927379](http://sudan.ubuntuforums.com/showthread.php?t=927379)

It also might be your Firefox profile that is crashing. You can try backing up .mozilla in your home directory (hit Ctrl + H to see it) by renaming it to .mozilla-bak and then running Firefox again. This way Firefox will create a new user profile for you, taking away your bookmarks, preferences, add-ons, etc. If that works, then it was your old profile. We can then restore your old profile and try to fix it or if you're fine without it, just use the new one!

---

### Post by Moleverine on 2008-10-15
What kind of pages are you viewing in Firefox?  I've had similar problems occasionally, and I'm starting to think it's Flash related.  Adobe's 64-bit version of Flash seems to be buggy.

EDIT: And I see I missed Altonbr's mention of Flash.  Didn't mean to be redundant.

---

### Post by xouns on 2008-10-15
Firefox did the same to my computer (P2Core 1.6Ghz, 2GbRam, 8400GS video) by really using the hard drive intensively. Oh well, it didn't really freeze, but made it really slow (think of badly reacting mouse and keys sticking, writing loooooooooong words) until I switched from Pulse to Alsa drivers for my soundcard and installed the updates for today and yesterday. I don't know if it makes a difference, but it seemed to have worked for me.

---

### Post by briandu on 2008-10-15
xouns,

did you upgrade today?

I have similar spec pc and firefox does give trouble on the .21 kernel.

When booting up and u see grub - press enter and then choose the .19 kernel and u should be OK

u can change the grub to point to the older version for a short while

---

### Post by Artemis3 on 2008-10-16
Is your entire machine freezing, as in the mouse pointer is not moving anymore? alt tab, alt f1 do nothing?

Does it freeze if you do something else, like playing a 3dgame?

---

### Post by coldcut on 2008-10-16
thanks for the replies. I'm going to try these advices on my computer tonight (haven't been home the last couple of days). 

Artemis3: no I haven't tried playing 3D games, haven't been able to download anything ;) and yes everything is frozen =/

---

