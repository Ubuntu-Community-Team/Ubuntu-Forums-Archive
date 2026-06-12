---
title: "Graphics Driver gone wrong"
date: 2009-08-24
forum: x86 64-bit Users
---

### Post by NoaHall on 2009-08-24
I have a nvidia card pci express that's my main, but I tried to use the onboard ati card , installed the driver through the ubuntu menu, and now I can't get a gui or a command line. When I boot into recovery mode, I can do things - but the net+root doesn't work - it won't connect. I tried repairing xorg.conf, but it doesn't work. I used sudo dpkg-reconfigure -phigh xserver-xorg, but it still doesn't work. Help? :)

Never mind - solved.
sudo apt-get remove --purge xorg-video=driver-fglrx

---

