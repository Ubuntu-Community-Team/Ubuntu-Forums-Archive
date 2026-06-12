---
title: "No Monitor Display after upgrading graphic card"
date: 2008-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by lninjo on 2008-02-28
Ok ive searched all the forums and I think this problem will be a new thread. I am running kubuntu 7.10 64 bit Os. What happened was i installed a new graphics card it is a pny geforce 6800gt 512m. After installing and rebooting i have no display. I reinstalled the os thinking maybe kubuntu couldnt recongize it from the old drivers which are both the nividia accelerated drivers. And after installing nothing. I can see my desktop when installing from live. but once i reboot from the hard drive nothing help out a fellow compuser and give me some ideas

---

### Post by Yellow Pasque on 2008-02-28
Can you get to a terminal from Ctrl+Alt+F1? If not, boot into recovery mode and try:
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

---

