---
title: "Howto Install  DemocracyPlayer In Dapper 64 bit"
date: 2006-10-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by babwe on 2006-10-02
I got democracyplayer to run on Dapper 64 bit PC, by going here [http://http://www.getdemocracy.com/downloads/]("http://http://www.getdemocracy.com/downloads/")
and then I downloaded the DataPackage and the For 64-bit systems, use this player package instead.       Then I installed as per this guide [https://develop.participatoryculture.org/projects/democracy/wiki/LinuxNotes]("https://develop.participatoryculture.org/projects/democracy/wiki/LinuxNotes")
and every thing wazz done as right click and select "Open with gdebi") on the deb files so they are opened with gdebi, first democracyplayer-data_0.8.4.1-1_all.deb and after that democracyplayer_0.8.4.1-1_i386.deb and everything worked:) :KS

---

### Post by fabertawe on 2006-10-02
Yep, you are right, installs a doddle. Interesting... I am loading an AC/DC video right now, could be fun this! Thanks for the tip :) it never ceases to amaze me the new software and projects out there that I knew nothing about!

Cheers ... Paul

---

### Post by csadowski on 2006-10-02
I try to install the amd64 package but it tells me that democracyplayer conflicts with j2re1.4

any ideas as to what I can do to solve this?

---

### Post by csadowski on 2006-10-02
disregard that last message, i got it

---

### Post by ceenvee703 on 2006-10-02
Please share what you did, as I get the exact same message about j2re1.4

---

### Post by sonni_kuba on 2006-10-03
> Please share what you did, as I get the exact same message about j2re1.4

1) Go to synaptic install j2re (Java Environment)
2) After install, go back to synaptic, and mark j2re for "complete removal"
3) Reinstall, the amd64 deb
4) Enjoy :p

---

