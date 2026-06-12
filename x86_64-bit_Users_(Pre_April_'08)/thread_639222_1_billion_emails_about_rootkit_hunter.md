---
title: "1 billion emails about rootkit hunter"
date: 2007-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-12-12
How can I stop getting emails about rootkit hunter without stopping it from running automatically? These are the emails I get constantly.

```
-N  - 486/493: root                   [rkhunter] Daily run             -- (all)
Date: Mon,  3 Dec 2007 22:51:37 -0600 (CST)
From: root <root@ubuntu>
To: undisclosed-recipients: ;
Subject: [rkhunter] Daily run

Warning: Found enabled xinetd service: /etc/xinetd.d/vmware-authd
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /etc/.bash.bashrc.swp: Vim swap file, version 7.0

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)







i:Exit  -:PrevPg  <Space>:NextPg v:View Attachm.  d:Del  r:Reply  j:Next ?:Help
```

---

### Post by Jouke74 on 2007-12-13
Uhhh... remove your email address from the configuration, or alter the configuration file not to send you anything?

---

### Post by go_beep_yourself on 2007-12-13
I did not put my email address in the configuration. Look again. It says the email was sent to root@ubuntu and that's not in the configuration either.

---

### Post by Jouke74 on 2007-12-13
I looked again and it says from "root@ubuntu" to "undisclosed-recipients"... :lolflag:

Try a "grep" command in the rkhunter directory to find either.

---

### Post by praxis22 on 2007-12-13
There's a program called procmail that will allow you to filter mail on the fly, try looking at that. Failing that you could redirect all root mail to the /dev/null but that will mean you get no root mail at all. I don't use root kit hunter so I can't help you with that.

---

### Post by Jouke74 on 2007-12-13
I think you saw this one already? 

[http://forums.debian.net/viewtopic.php?p=118771&sid=861b5cf354f7a4ac25f8df67601a7fa7](http://forums.debian.net/viewtopic.php?p=118771&sid=861b5cf354f7a4ac25f8df67601a7fa7)

[http://www.linux-mag.com/id/2212](http://www.linux-mag.com/id/2212)

Ok enough now...

---

