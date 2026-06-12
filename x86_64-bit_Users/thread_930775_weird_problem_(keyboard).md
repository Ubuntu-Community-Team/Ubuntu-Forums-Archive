---
title: "weird problem (keyboard?)"
date: 2008-09-26
forum: x86 64-bit Users
---

### Post by pablosanchezuy on 2008-09-26
Hi there.
The problem has started some days ago. 

Suddenly, when i open any app, as i press any key, the app shuts down : any key.

Also num lock, caps lock stop working.

There's no way to stop this, just restart the computer.

It may show at any time, 30 minutes, 1 hour, 6 hours, just restart it and begin to work again. 

It's not a stuck key.
I'm using two keyboard layouts, english and spanish (since several months) .


#uname -a

Linux "myhostname" 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux

I'm also running vmware, with a windows os as a guest, which is not affected anyway .


Here are some log entries, from /var/log/messages :

Sep 26 13:20:45 "myhostname" kernel: [ 3402.929243] gnome-terminal[9377]: segfault at 2a rip 7ff5c9c6a4b4 rsp 7fffd404b268 error 4
Sep 26 13:23:22 "myhostname" kernel: [ 3560.575272] gucharmap[9511]: segfault at 2a rip 7f8ca0f964b4 rsp 7fffa9f532a8 error 4
Sep 26 13:34:12 "myhostname" kernel: [ 4210.259958] polkit-gnome-ma[10164]: segfault at 1d rip 7fe8b3bcd4b4 rsp 7fffbc811788 error 4
Sep 26 13:34:12 "myhostname" kernel: [ 4210.342658] network-admin[10063]: segfault at 1d rip 7fa60b1044b4 rsp 7fff13b38698 error 4
Sep 26 13:39:49 "myhostname" kernel: [ 4546.733862] nautilus[6378]: segfault at f6000034 rip 7f1ff0024f0f rsp 7ffffb5d29a0 error 4
Sep 26 13:40:01 "myhostname" kernel: [ 4558.634586] xrdp[5468]: segfault at 348 rip 404979 rsp 7fffa6fc4ba0 error 6

I can't find any logs for, firefox "segfaulting" but it shuts down as any other app.

Any ideas are welcome


regards,
pablo

---

### Post by pablosanchezuy on 2008-11-19
FYI, [http://ubuntuforums.org/showthread.php?t=852744](http://ubuntuforums.org/showthread.php?t=852744) , post # 8 .

That's it.

Pablo .

---

### Post by wilkenw on 2008-11-22
I am running Ubuntu 8.10 with VMWare 1.7 in 32-bit mode.  From time-to-time, my keyboard cannot produce any upper case letters on Ubuntu, but can always produce upper case letters on my Windows XP Pro virtual machine.  Rebooting Ubuntu always fixes the problem.  Go figure.  I never had this problem, however, when running Ubuntu 8.04.

---

