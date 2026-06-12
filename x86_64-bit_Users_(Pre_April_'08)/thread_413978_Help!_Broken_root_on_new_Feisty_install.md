---
title: "Help! Broken root on new Feisty install"
date: 2007-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-04-19
I just downloaded and installed the final of Feisty amd64 Desktop on a brand new computer this morning. Then I used the new computer to back up my Edgy amd64 laptop, preparatory to doing an apt-get dist-upgrade on the laptop. Everything was going fine on the new computer until I decided I wanted to install more software. I clicked on System > Administration > Synaptic Package Manager, expecting the little window for my root password to pop up. Instead I got a window that said:

Failed to run /usr/sbin/synaptic as user root.
Unable to copy the user's Xauthorization file.

I've been using Ubuntu amd64 on my laptop since Hoary and I've never seen anything like this. What happened, and how can I fix it? I use the same username and root password on my laptop. Should I find Xauthorization on the laptop and copy it to the new computer?

Edit: I tried logging out and back in at the suggestion of a local Linux dude. The login screen was jiggling and the Ubuntu login drums were going continuously,. Not good! So I restarted. When the login screen came up it looked normal, but when I tried to log in I got a message that it could not write to my Xauthorization file, probably because of lack of space. Then I remembered that the backup had aborted at the last minute because it ran out of space. Duh! So I booted to Recovery Mode, which automatically made me root, then deleted a bunch of big files that I really didn't need anyway. I rebooted and all is back to normal. :)

---

