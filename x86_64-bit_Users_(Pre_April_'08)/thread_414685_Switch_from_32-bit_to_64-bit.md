---
title: "Switch from 32-bit to 64-bit"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by arie.k on 2007-04-20
Our server is currently running 32-bit version of Ubuntu Edgy, but it has Pentium D processor. After I read some of the posts in this forum, we are thinking to switch it to 64-bit version.

Can the upgrade process be done without major downtime?

---

### Post by viciouslime on 2007-04-20
Unfortunately, there is no way to just upgrade you need to do a fresh install. If you have all your served files on a different partition though, as I imagine you will. You could just back-up all your config files (/etc) do a fresh install and then copy them all back. This would probably equate to 30/40mins downtime.

---

### Post by Jussi Kukkonen on 2007-04-20
Well, that depends on your definition of major. The bad news is that you can't dist-upgrade between architectures (back when apt was designed no-one thought that would ever be an issue). So you'll have to install from scratch.

You can of course install on another partition, and keep the old version intact -- that way you should be able to keep the downtime in "maintenance windows"...

---

