---
title: "su error message"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by kurbacik on 2006-06-03
I don't know if this is just an amd64-related issue or not, but this is the ubuntu version I use. Every time I use su to become root I get this error message.

configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)

Has anybody else received a similar message and does anybody know how to fix it?
:confused:

---

### Post by tonyr on 2006-06-03
How do you become root?  Are you simply typing **su** on the command line?  
The standard way to become root in Ubuntu is to type **sudo su** and then enter 
**your** password.  See [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo").

---

### Post by kurbacik on 2006-06-03
I login as root with su, but the proble appears with sudo su too. I found a solution from the Debian bug report logs. The problem is caused by upgrading package login. apt-get for some reason doesn't remove FAIL_DELAY etc. from /etc/login.defs eventhough they are not needed anymore (and may not exist in that file). If you manually comment out those lines, everything should work. Thanks for the answer anyways.

---

### Post by kurbacik on 2006-06-03
[QUOTE=kurbacik]I login as root with su, but the proble appears with sudo su too. I found a solution from the Debian bug report logs. The problem is caused by upgrading package login. apt-get for some reason doesn't remove FAIL_DELAY etc. from /etc/login.defs eventhough they are not needed anymore (and may not exist in that file). If you manually comment out those lines, everything should work. Thanks for the answer anyways.[/QUOTE]

Sorry, I was too quick in my answer. I still have the same problem.

---

### Post by kurbacik on 2006-06-03
The soultion is posted here:

[http://lists.debian.org/debian-user/2005/10/msg00587.html](http://lists.debian.org/debian-user/2005/10/msg00587.html)

;)

---

