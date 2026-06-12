---
title: "Turning off &quot;cool and quiet&quot; on demand"
date: 2007-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by misteral on 2007-03-31
Hi All

When I bought my AMD64 I thought this frequency scaling was the coolest thing. IT still is - but there's one thing I'd like to do. Some times I'd just like to tell it to scale up, keep at that level 'till I'm done. When I'm running VMWare for example, I'd just like to keep the full CPU available.

I've seen some threads about turning cool and quiet off in the BIOS, but what I'd really like to know is.. is there a way I can do this manually? If I have to edit some config files every time that's cool, if it's something I can script to turn on/off, that would be better.

Any one have any thoughts?

Thanks!!

---

### Post by shanepardue on 2007-03-31
What exactly does "Cool and Quiet" do? I don't know the answer to your question, but I saw it in my bios and was curious.

---

### Post by misteral on 2007-03-31
What I thought it was... was the scaling functionality. I.E. when your system's not under load it scales back to say 1ghz, but under load it scales up to 2ghz, or full cpu potential.

---

### Post by wuzzerd on 2007-03-31
This should work:
```
sudo echo 'ondemand' > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

---

### Post by Biker on 2007-04-01
Install package cpufrequtils. When starting a Virtual Machine excecute 'sudo cpufreq-set -g performance' and after closing de VM execute 'sudo cpufreq-set -g ondemand' in a script.

---

### Post by kerry_s on 2007-04-01
right click the panel and check if theres a frequency control app, there's 1 in gnome but i don't know about kubuntu.

---

### Post by misteral on 2007-04-07
> **Biker said:**
> Install package cpufrequtils. When starting a Virtual Machine excecute 'sudo cpufreq-set -g performance' and after closing de VM execute 'sudo cpufreq-set -g ondemand' in a script.

Biker, that is exactly what I was looking for! Thank You!

---

### Post by a-musing amazon on 2007-04-07
One simple (to enable and then to use) method to obtain control of CPU frequency scaling is to allow gnome-applets to run suid root. 

That is, if you are already running the CPU frequency scaling monitor in your menu bar this allows you to, as well as monitor, to change both frequncy or the governer (usespace, powesave, ondemand, conservative, performance).

To do this run the command 

 sudo dpkg-reconfigure gnome-applets

in a terminal and answer 'yes'. There are some security issues in enabling this and the command warns you:

 &#9474;  Configuring gnome-applets 
 &#9474;                                                                                
 &#9474; You have the option of installing a component of the CPU Frequency     
 &#9474; Scaling Monitor (cpufreq-selector) with the SUID bit set.             
 &#9474;                                                                        
 &#9474; If you make cpufreq-selector SUID, any user can then set the CPU's clock
 &#9474; frequency without needing any additional privileges. This could,       
 &#9474; however, potentially allow it to be used during a security attack on
 &#9474; your computer. If in doubt, it is suggested that you install it without  
 &#9474; SUID.                                                                    
 &#9474;                                                                          
 &#9474; The applet will continue to work if you choose to disable SUID for      
 &#9474; cpufreq-selector, but only for monitoring the CPU clock frequency. You  
 &#9474; may need to restart this applet before this decision takes effect.     
 &#9474;                                                                           
 &#9474; If you change your mind later, run "dpkg-reconfigure gnome-applets" 

When you have done this left clicking on the applet icon give you the choice of governor or of frequency to use.

---

