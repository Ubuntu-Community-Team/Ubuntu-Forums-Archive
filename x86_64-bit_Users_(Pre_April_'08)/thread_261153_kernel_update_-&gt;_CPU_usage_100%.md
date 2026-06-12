---
title: "kernel update -&gt; CPU usage 100%"
date: 2006-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by fancyydk on 2006-09-19
Hello,

I was just browsing the net when a little balloon popped up saying there is an update that needs to be installed. So I noticed that one of the update items was a Linux kernel header, although I'm still not sure if that has anything to do with this. Anyway, after I updated my system, I turned my computer off. A few hours later, I turned it back on and noticed that my CPU usage is constantly 100% from the very start, like even before I log on to Ubuntu. The CPU fan keeps running constantly and it makes a loud noise. One of the many reasons I use Ubuntu is that it boots faster and keeps my computer relatively quiet, compared to Windows, but now it's noisy and annoying. Is this because of the update? I can only guess that it is because that's the VERY last thing I did before this happened. Please help me! Thanks!

---

### Post by Echo35 on 2006-09-20
Grub holds previous kernel versions in the boot loader as well, so try using an older kernel and see if that fixes the problem. If not, then it's probably not a kernel problem. That would be my guess anyway.

---

### Post by fancyydk on 2006-09-20
Ok, I just rebooted using 2.6.15-23-amd64-generic instead of 2.6.15.27-amd64-generic. CPU usage is still 100%. So it must be something else. I still think it's one of the updated programs because that's the only thing I did before this happened.

Hmm... now the problem gets a lot more complicated. Do I have to reformat? I lost the 64bit version of Ubuntu CD... Any help will be appeciated.

---

### Post by fancyydk on 2006-09-20
ok, I opened a terminal and typed "top" to find out what exactly is eating up my CPU resources. It's a process called "atieventsd." Now that I know what's causing this, I feel relieved. But I have to go to class in 20 minutes, so I'll try to fix this tonight. If any of you have any advice, please post and let me know. Thanks!

---

### Post by fancyydk on 2006-09-20
problem solved. I had to reinstall the ATI driver.

---

### Post by Echo35 on 2006-09-21
You know, on my old PC, I had an ATI card, and I tried the driver and it messed up a lot of stuff. I smply removed it and it worked just fine. Reasons why I support nVidia...

---

