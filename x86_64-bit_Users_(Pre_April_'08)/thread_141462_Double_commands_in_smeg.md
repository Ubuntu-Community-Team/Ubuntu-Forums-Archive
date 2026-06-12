---
title: "Double commands in smeg?"
date: 2006-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-03-08
I run Firefox in a 32-bit chroot environment on my Ubuntu-64 Breezy laptop. Everything is working great, including RealPlayer and Flash, except when I change locations. The problem is that the new connection changes the DNS server information in /etc/resolv.conf, but not in /chroot/Breezy/32bits/etc/resolv.conf. After much head scratching and asking questions I cooked up the following link command:

sudo ln -f /etc/resolv.conf /chroot/breezy/32bits/etc/resolv.conf

This overwrites the resolv.conf file in the chroot environment with the new (changed) version in the 64-bit world. So far this solution is perfect.

However, it is getting tedious. Just about every day I have to go to the university and each time I have to run this command before I can go anywhere. And when I come home where I have cable I have to run it again. I need to figure out some way to automate this.

Most of the time the first thing I launch is Firefox. The launch command is "dchroot -d firefox %u." So I tried to prepend the link command to the Firefox launch command in the menu editor (smeg), using a semicolon in between the commands. It didn't work. All I got was "firefox is loading...," then the message disappeared and nothing launched. Strangely, however, it works fine from the command line.

Someone else suggested running a cron job, but I know nothing of cron. I'd want it to run every few seconds, though, and that worries me that it might bog down the computer.

Does anyone have any idea how I can make this happen automatically every time I make a new connection?

---

