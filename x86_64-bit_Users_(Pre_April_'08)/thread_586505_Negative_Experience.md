---
title: "Negative Experience"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by The Caped Crusader on 2007-10-22
Or better yet, No Experience whatsoever.

I was a Feisty user and a happy one, until some of the later updates broke my compiz manager and messed up the upper taskbar. Anyway, since we were close to the 7.10 release, I backed up my stuff and uninstalled everything.

But now that 7.10 is released, I'm very disappointed with it. I can't even boot into my freshly installed Ubuntu! To be able to install it I had to pass up the 'noapic nolapic nosplash' string, and took out the 'quiet' boot option, to check out what was going on. The splash doesn't want to work. But on Feisty it was working fine. What went wrong with the new version, people?!
Then, after install, I boot into Grub, press E and I do the same to the boot params. take out 'quiet' and add 'noapic nolapic nosplash'. Nothing. It reboots and goes to post screen over and over again.
I've tried this more than a dozen times, with different string, putting the 'noapic nolapic' on different sections of the boot params.

The damn thing just doesn't like my system!! I've given up, guys, I'll just wait for somekind of official workaround or even a future official release, because Feisty was working and Gutsy simply doesn't want to comply.

The only hardware I changed before trying to install 7.10 was the video card (was using a 7600GT and now a 8800GTS) and the monitor (was using a 1280x1024 screen and now a 1680x1050), but I simply find hard to believe it's the graphic card or the monitor, because the first install screen when I boot into the Ubuntu CD appears just fine.

Just for the record, my setup is:

ASUS A8N-SLI Premium board
AMD Opteron 180 oc'd to 2600Mhz
EVGA 8800GTS 320Mb factory overclocked
2x1Gb OCZ EB Platinum DDR
1 x 80Gb IDE Hitachi (where I had previous versions of Ubuntu installed and tried to install this 7.10)
2 x 160Gb Samsung RAID0 Stripe (Windows XP installation)
1 x LITE-ON DVD-RAM Sata
Samsung SyncMaster 2232BW monitor

:(

damn, i was really excited with this release...

---

### Post by The Caped Crusader on 2007-10-22
Oh, and BTW, this is the THIRD Ubuntu CD I burn. This last one was burned with the lowest speed possible. I'm pretty sure this isn't related to bad media either. I have another machine - older one, Socket A - with Ubuntu 7.10 32bits installed, and is running just fine, installed pretty normal and I used the same media for the install CD.

This HAS to be something specific to the AMD64 version... come on Ubuntu developers, please check on this, for what I've seen here, I'm not the only one with this problem.

---

### Post by picopir8 on 2007-10-22
After you hit "e" to edit the boot command in grub, and then make your edits what do you do next?

Make sure you hit "enter" to commit the changes, hitting escape cancels them.
Once the changes have been committed, hit "b" to boot with them, hitting enter boots the unmodified command.

I know a lot of people who make modifications to the boot command and then boot not using the modifications.

If you follow this, then you should get a text boot screen and if it does fail somewhere you should be able to note the last successful line and post it here so people can help figure out what is going wrong.

---

### Post by The Caped Crusader on 2007-10-22
> **picopir8 said:**
> After you hit "e" to edit the boot command in grub, and then make your edits what do you do next?

Make sure you hit "enter" to commit the changes, hitting escape cancels them.
Once the changes have been committed, hit "b" to boot with them, hitting enter boots the unmodified command.

I know a lot of people who make modifications to the boot command and then boot not using the modifications.

If you follow this, then you should get a text boot screen and if it does fail somewhere you should be able to note the last successful line and post it here so people can help figure out what is going wrong.

I'm pretty sure I booted with 'b', and haven't escaped the options withouth the modifiers being saved. I did this a dozen times and the system won't boot, even without the 'quiet' modifier. It doesn't post anything onscreen, simply reboots to post screen.

Thanks anyway for trying to help, dude :)

---

### Post by Jouke74 on 2007-10-22
Might be a crazy suggestion, but more people seem to have problems with the 8800 video cards. What if you try the 7600 just for the heck of it? (I know that is a step back).

Or do this first: [http://ubuntuforums.org/showthread.php?t=581683](http://ubuntuforums.org/showthread.php?t=581683)

---

### Post by The Caped Crusader on 2007-10-24
No can do. Doesn't work here, period. I'm very disapointed with this... wans't this supposed to be tested with several different machine configurations? How could the developers let something like this slip by?

As for the 7600GT, I no longer have it in my possession, but even if I had it, damn, switch back to a slower GPU just to get Ubuntu running? I don't love Ubuntu THAT much, lol. Besides, I use this system with a XP dual boot just for playing games, so, taking out the 8800GTS is not an option here.

Anyway, thanks for trying to help. I'll wait and see what Ubuntu staff will come up with. And I'll probably wait for a 7.15 release or something like that, because I suspect this is a really bad issue (not just a common bug) that's leaving many many people without a proper Ubuntu installation - Unless, of course, they switch back to 7.04...

---

