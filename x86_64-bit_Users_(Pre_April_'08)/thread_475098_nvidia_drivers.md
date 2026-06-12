---
title: "nvidia drivers"
date: 2007-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Trew on 2007-06-15
i've been trying to install dirvers for my geforce go6150.

but i'm running into a problem. 
I've been reading the README file from the Nvidia site but i dont understand the following:

Currently, the NVIDIA driver will attempt to detect edge triggered interrupts and X will purposely fail to start (to avoid stability issues). This behavior can be overridden by setting the "NVreg_RMEdgeIntrCheck" NVIDIA Linux kernel module parameter. This parameter defaults to "1", which enables the edge triggered interrupt detection. Set this parameter to "0" to disable this detection.

now i have to set the paramet to "0"...but i wouldnt know how :-)

this is the link to the readme.

[http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.09/README/chapter-08.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.09/README/chapter-08.html)

gr 
Trew

---

### Post by fabertawe on 2007-06-16
I presume you're getting the "interrupt for NVIDIA graphics device PCI:x:x:x appears to be edge-triggered" error in the X log. Is this with 'nvidia-glx-new' from the repository? And have you tried booting with either or both of the 'irqpoll' and 'noapic' options as mentioned in the readme?

Paul

---

### Post by Trew on 2007-06-16
yes to all the three questions :-)

gr trew

---

### Post by fabertawe on 2007-06-16
Take a look at '/etc/modprobe.d/nvidia-kernel-nkc'. To edit (apologies if you already know this ;))...
```
gksudo gedit /etc/modprobe.d/nvidia-kernel-nkc
```and add the parameter to 'options'. Hopefully that should do it :)

Paul

---

### Post by Trew on 2007-06-16
hmmm...if i open the file all i see is the following:

alias char-major-195* nvidia

so where do i ad the parameter?

gr tre

---

### Post by fabertawe on 2007-06-16
Trew, mine looks like this...
```
alias char-major-195* nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```
So yours should look like this
```
alias char-major-195* nvidia
options nvidia NVreg_RMEdgeIntrCheck=0
```

Paul

---

### Post by Trew on 2007-06-17
ah wel...thanks for your help Paul. It was a good try but......it stil doesnt work. :-(

Every thing is working just fine on my hp paivilion dv6132eu.......exept my graphics card. its realy to bad becouse ubutnu could of been my first choice os. but untile my graphics card doesnt work, its stil windows i think.

But...i wil keep trying, if i find a way to let it work i wil post it here :-)

And paul, if you have any new insights, just let me know and post in this thread :-)

gr trew

---

### Post by Ocxic on 2007-06-17
try using a program called envy to install the nvidia drivers, it worked perfecly for me, even with the propitary ones, thanks to that program, i no loger have to re-install the drivers after a kernel upgrade.

---

### Post by fabertawe on 2007-06-18
> **Trew said:**
> ah wel...thanks for your help Paul. It was a good try but......it stil doesnt work. :-(

Every thing is working just fine on my hp paivilion dv6132eu.......exept my graphics card. its realy to bad becouse ubutnu could of been my first choice os. but untile my graphics card doesnt work, its stil windows i think.

But...i wil keep trying, if i find a way to let it work i wil post it here :-)

And paul, if you have any new insights, just let me know and post in this thread :-)

gr trew

I can imagine how frustrating this is for you :( Please do let us know if you find a solution.

The only other thing you can do is try the latest Nvidia driver from their website (100.14.09 as of writing this) and do a manual install. This is a newer version than Envy uses (Envy didn't work for me with one of the drivers over 100.* anyway and I had to manually install for my card). Although I'm not sure if this is overkill for a go6150 or even required but if you have nothing else to lose it might be worth a shot. If you try this you will have to remove the installed nvidia driver first and X **may** die as other bits might need to be cleaned out also. If you fancy a crack at it I will try and find all the info you need. X isn't so scary when you've grappled with it a few times!

Paul

---

### Post by Trew on 2007-06-18
Hi Paul,

Its done! I've reinstalled Ubuntu, and the first thing i did was to install the video drivers.  They work now. Only thing left is the wireles network adapter.

i have to start ubuntu with the following kernel parameters: NOAPCI NOAPIC irqfixup
if i dont do this, it wont start. But even with these parameters Ubuntu sometimes freezes.

Its not the perfect installation, but where getting there.

And thanks for your help.  I'll let you know when the whole thing works

gr
Trew

---

### Post by fabertawe on 2007-06-19
Excellent news :D

I was having freezes with 2.6.20-15-generic until I switched to the lowlatency kernel but then 2.6.20-16-generic is fine for me. So you may find your freezing problem just goes away at some point.

Paul

---

### Post by Trew on 2007-06-19
> **Trew said:**
> Hi Paul,

Its done! I've reinstalled Ubuntu, and the first thing i did was to install the video drivers.  They work now. Only thing left is the wireles network adapter.

i have to start ubuntu with the following kernel parameters: NOAPCI NOAPIC irqfixup
if i dont do this, it wont start. But even with these parameters Ubuntu sometimes freezes.

Its not the perfect installation, but where getting there.

And thanks for your help.  I'll let you know when the whole thing works

gr
Trew

forget the 'NOAPCI NOAPCI irqfixup' parameters

i've changed it to 'noapic nolapic' 

gr 
trew

---

