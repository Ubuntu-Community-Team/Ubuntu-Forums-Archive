---
title: "sshd dies under heavy load"
date: 2006-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by capitol on 2006-09-14
Hi, i'm running an dell poweredge 2850 as a webserver and sshd stops working under heavy load.

Today my graphs show that we had a load of about 30 and then *bang* sshd dies.

Does anyone else have this problem or do i have a hardware problem?

---

### Post by capitol on 2006-12-14
Today it happened again, but i had a ssh session running when it happened, i tried to restart the sshd deamon, but that didn't work.

After some heavy googling i found that i could (almost) login if i started the like this:
 /usr/sbin/sshd -dddD -r

it gives a lot of output but finishes with this:
debug1: PAM: setting PAM_TTY to "/dev/pts/4"
debug1: PAM: establishing credentials
debug1: Setting controlling tty using TIOCSCTTY.
debug2: fd 4 setting TCP_NODELAY
debug2: channel 0: rfd 7 isatty
debug2: fd 7 setting O_NONBLOCK
debug3: fd 6 is O_NONBLOCK

to me it looked like the daemon had troubles binding port 22 when i tried to start it again.

---

### Post by jaakan on 2006-12-14
What does your webserver do? Whats normally eating up your chip %? what apps are running? Has that server had any heat issues or drives or hardware fail?

---

### Post by capitol on 2006-12-15
After a tip from a friend i realized that we might have been bitten by this:

[http://www.debian.org/security/2006/dsa-1212](http://www.debian.org/security/2006/dsa-1212)

I exchanged ssh daemon to lsh, 30 minutes ago, and i haven't had any problems since. Is that security bug maybe something ubuntu have missed? I didn't have any outstanding security packages to install.

---

