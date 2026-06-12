---
title: "video driver fuzzy compared to 32bit"
date: 2006-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxted on 2006-01-05
Has anyone noticed that the video looks fuzzy on 64bit Breezy vs the 32version?

Also I was able to use the nvidia-glx in synaptic for 32... is it available for 64?


Thanks

---

### Post by gil-galad on 2006-01-05
[QUOTE=linuxted]
Also I was able to use the nvidia-glx in synaptic for 32... is it available for 64?
[/QUOTE]

Yes.  Install and use the nvidia driver and see if you still have problems.

---

### Post by linuxted on 2006-01-07
[QUOTE=gil-galad]Yes.  Install and use the nvidia driver and see if you still have problems.[/QUOTE]


Just to be clear, you are saying the nvidia stuff in Synaptic should be sufficient to get things working right?


Thanks

---

### Post by linuxted on 2006-01-07
[QUOTE=gil-galad]Yes.  Install and use the nvidia driver and see if you still have problems.[/QUOTE]

Well it is installed and enabled (sudo nvidia-glx-config enable  plus a reboot), but the results are still fuzzy.  Do I need to do some tweaking in config files???


Thanks

---

### Post by linuxted on 2006-01-07
[QUOTE=linuxted]Well it is installed and enabled (sudo nvidia-glx-config enable  plus a reboot), but the results are still fuzzy.  Do I need to do some tweaking in config files???


Thanks[/QUOTE]

I ended up tweaking my /etc/X11/xorg.conf file such that the refresh rates were in the range of my monitor (75Hz).  I suspect there is a difference in the xorg.conf files in 32 and 64bit installs.  

Works great now

---

