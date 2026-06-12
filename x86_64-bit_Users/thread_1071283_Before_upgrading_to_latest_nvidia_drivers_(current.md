---
title: "Before upgrading to latest nvidia drivers (current 180.29)"
date: 2009-02-16
forum: x86 64-bit Users
---

### Post by jet2230 on 2009-02-16
system > administration > hardware > disable any nvidia drivers if any are enabled

run:  sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
run:  sudo apt-get autoremove

test: ctrl + atl + backspace : reconfigure display - after gdm restart no gfx drivers should be in use

stop gdm: sudo /etc/init.d/gdm stop

login with normal account

sudo sh /<driver location>/NVIDIA-Linux-x86_64-180.29-pkg2.run

start gdm: sudo /etc/init.d/gdm start

180.29 finally working with my 8800 GTX !

---

