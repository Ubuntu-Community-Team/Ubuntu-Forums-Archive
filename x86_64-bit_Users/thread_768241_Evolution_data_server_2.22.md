---
title: "Evolution data server 2.22"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by call2 on 2008-04-26
I've just run an upgrade from 7.10 to 8.04 and I notice that evolution data server 2.22 is using 50% of my cpu resources. I'm running Folding@Home and wondered why the frame times had suddenly increased so looked at the running processes.

I stopped the evolution-data-server process, but wondered why it was running at 50% when I don't use evolution. I can see that removing it might affect other programs that I might use, so I've left well alone until I can get some answers. Any ideas?

---

### Post by Tearlow on 2008-04-26
That makes us two then. I've also upgraded but mine is peaking at 80-88% although my Laptop's processor is quite weak as it is. As for all I know Evolution is fairly safe to remove (Personally use Thunderbird most of the time).

EDIT: Wanted to add that it's no problem at all to remove Evolution completely.

> - evolution-exchange-storage, evolution-data-server-2.22, evolution-alarm-notify, ...

Only useful if you are using evolution as mailer. Else remove all evolution packages.
If you only use evolution for reading your emails then you may want to try a standalone mailer (thunderbird,...)

[http://ubuntuforums.org/showthread.php?p=4568105](http://ubuntuforums.org/showthread.php?p=4568105)

Thread about many Processes in 8.04 might be some interesting reading?

The question still remains though, why. I'll toss in a report later today when I'm home.

---

### Post by Pomo on 2008-04-26
> **call2 said:**
> I've just run an upgrade from 7.10 to 8.04 and I notice that evolution data server 2.22 is using 50% of my cpu resources. I'm running Folding@Home and wondered why the frame times had suddenly increased so looked at the running processes.

I stopped the evolution-data-server process, but wondered why it was running at 50% when I don't use evolution. I can see that removing it might affect other programs that I might use, so I've left well alone until I can get some answers. Any ideas?

Just kill the process. It is a well known and documented bug, with no other current solution.
[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/151536](https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/151536)

---

### Post by call2 on 2008-04-26
Thanks a million for the info fellas. I couldn't find any links to the reported bug so I couldn't have looked hard enough. Good info though, and I'll try and sort something out now.
Cheers.

---

### Post by Marky-Mark47 on 2008-05-07
> **call2 said:**
> I've just run an upgrade from 7.10 to 8.04 and I notice that evolution data server 2.22 is using 50% of my cpu resources. I'm running Folding@Home and wondered why the frame times had suddenly increased so looked at the running processes.

I stopped the evolution-data-server process, but wondered why it was running at 50% when I don't use evolution. I can see that removing it might affect other programs that I might use, so I've left well alone until I can get some answers. Any ideas?

To resolve this problem, end the Evolution data server 2.22 process using System Monitor, then go to System -> Preferences -> Sessions, click the Session Options button, then click the Remember Currently-Running Applications button, and this will prevent Evolution data server 2.22 starting up at boot. If you want to start each session with a clean desktop, it might be a good idea to close your other apps before hitting the Remember Currently-Running Applications button.

---

