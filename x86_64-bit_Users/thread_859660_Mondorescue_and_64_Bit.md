---
title: "Mondorescue and 64 Bit"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by mdsharp24 on 2008-07-14
I really need to get mondorescue working and have found very little on the Ubuntu Forums, the developers site, or elsewhere on this.

I understand that on Debian like systems the switch -k FAILSAFE must be run in order for it to work, and this is not possible on 64 bit.

Anyone have a link to a HOWTO for mondorescue, Ubuntu 8.04, and and64?

Michael

---

### Post by Cappy on 2008-07-14
Does
```
sudo apt-get mondo
```
work?

If not, what is the output from running "mondo" or "mondoarchive" after installing?

---

### Post by mdsharp24 on 2008-07-15
From mondoarchive.log:

FATAL ERROR. Failed to get real kernel package for virtual kernel package candiate(s) linux-image-2.6-amd64. Terminating.
Please e-mail a copy of /var/log/mindi.log to the mailing list.
See [http://www.mondorescue.org](http://www.mondorescue.org) for more information.
WE CANNOT HELP unless you enclose that file.


My original switch was:

mondoarchive -OVi -F -S /home/mondo/tmp -E /home/mondo -s 4780m -9 -p mondorestore -d /home/mondo -l / 

This would make mondoarchive stall at 20% and go no further.

Then I read where in "Debain LIKE" systems you had to add the -k FAILSAFE switch and thats when it croaks.

Michael

---

### Post by mdsharp24 on 2008-07-15
OK, this is weird, tonight I re ran the command after doing two things.

First, I saw where mondo wanted /bin/arch and knowing that arch is depracted to uname -m I simply added a /bin/arch system command that runs uname -m

Second, I moved some of the switches around and before others.

I just now ran...

```
mondoarchive -OVi -9 -p mondorestore -S /home/mondo/tmp -E '/home/mondo /home/michael/Music /home/michael/Videos /home/michael/Pictures' -I / -d /home/mondo -s 4608m
```

and everything completed fine, but with some errors. I will have to test tonight when I run mondorestore in compare mode.

---

