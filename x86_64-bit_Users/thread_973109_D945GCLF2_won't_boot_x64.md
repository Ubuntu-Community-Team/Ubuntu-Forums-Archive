---
title: "D945GCLF2 won't boot x64"
date: 2008-11-06
forum: x86 64-bit Users
---

### Post by kazooless on 2008-11-06
I have a D945GCLF2. With Hardy, it was working just fine with the AMD64 server install, except that I had to connect it to a 10/100 switch. Connected to Gigabit wouldn't give me any connectivity at all and a ton of dropped rx packets in the ifconfig -a results.

Anyway, I upgraded to Intrepid Server and the next boot was a kernel panic. (2.928474 Kernel panic not syncing attempted to kill init). This was a hard lock. No response to keyboard (ctrl-alt-del, num lock light wouldn't toggle, etc).

So, I burned all the new CD's, x64 & i386. The only ones that can boot past the boot menu are the i386 disks.

Since 2GB is the max ram, and the installation of several things I use required extra work, I am fairly certain I am just going to install the i386 server from scratch and be done with it. But I thought I should post this as well.

I'm happy to try things out if it will help the community. I'm also happy to post this elsewhere if there is a better place. However, I'm not a developer (by far!) so I probably just don't know any better. :)

Kazooless

---

### Post by Christobevii3 on 2008-11-06
I'm getting the same thing with almost all amd64 distros.

---

### Post by Christobevii3 on 2008-11-06
Seems mine was caused by the 8400gs pci card, hopefully I can get it working later.

---

### Post by kazooless on 2008-11-07
Well, I'm glad I re-installed from scratch. I have a basic server system that installed the pieces very nicely in i386 compared to amd64. I remember when I got amd64 up and running it was a royal pain. This time with i386 it flew by.

Seems really stable and fast. I did have to install the correct driver for the NIC, however. This site has the answer to the NIC problem: [http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

I had to install it manually though, since the script wasn't updated for the newer driver version and also maybe because I have a base load of server, so it might have needed some dependencies.

Anyway, following his manual steps with the newer driver worked great. I found the driver here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Hope that helps a bunch of people.

Kazooless

---

