---
title: "Installing Lm-sensors."
date: 2007-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-06-19
Ok well I've been trying to follow the how to: guide but I'm just not getting it.

This is the guide: [http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors+install](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors+install)

I've followed it as well as I can but I only come out with this 

```

dagger@dagger-desktop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +29°C
Core1 Temp:
             +35°C


```

I knows its got to be part of adding the sensors but I don't really get what I'm doing wrong.

---

### Post by _simon_ on 2007-06-19
Not sure what you're asking, it's obviously working as you can see your core temps....

If you're after the applet on a panel then you need to install sensors-applet then right click on a panel and add it.

---

### Post by nss0000 on 2007-06-19
BigD:

You wanted temps ya got temps. Consider yourself lucky to get anything. Lots of new(er) mobos are not supported whatsoever.

---

### Post by DaGGer on 2007-06-19
well I thought that it was suppose to show me voltiage and everything. I thought I messed it up. I know that I can get all the temps, and voltage as I've done it through windows so thats why I thought I messed something up.  Well then thanks. I thought I missed something.

---

### Post by dabl on 2007-06-19
I'm kinda new on Ubuntu, and haven't fooled with the sensors thing. But you sure get a lot more than just CPU temps out of lm-sensors in Kubuntu!  I don't know if you need "themes" or what, but surely some of the other sensor outputs can be displayed on the Ubuntu desktop if you want them.

---

### Post by DaGGer on 2007-06-19
you know what, I just installed xsensors so I can have a graphic verson to use.  It has all the voltage and fan speeds, and temperatures. They are all right (check with it versus the bios sensors)

---

### Post by dabl on 2007-06-19
Excellent -- xsensors works great.  Here's a screenshot -- guess I need to hook up those other fans, huh?  :D

---

### Post by DaGGer on 2007-06-19
Yea, mine didn't come up with all the sensors when I installed it but with xsensors it works fine.

I really need to dust out my computer. Its running a bit hotter than it should. It should be at like 30 degrees when doing nothing and like 40 when its playing a game.

---

### Post by fakie_flip on 2007-06-25
What is Temp3? I noticed other people have that too.

---

### Post by fakie_flip on 2007-06-25
xsensors is nice. you can also try installing ksensors and gkrellm. i couldnt get sensors-applet to show my gpu temp even though it shows with nvidia-settings :(

if you want to monitor your temperatures in real time, you could do this in a terminal.

watch sensors -f

---

### Post by DaGGer on 2007-06-26
Ok thanks, I think the temp3 is the ambiant temp inside the case but I can't be sure.

---

