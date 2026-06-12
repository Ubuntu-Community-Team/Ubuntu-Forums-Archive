---
title: "Powertop xorg"
date: 2009-02-19
forum: x86 64-bit Users
---

### Post by xigen on 2009-02-19
I am getting high cpu useage. 
AMD64, ubuntu, nvidia graphics card (vintage 2008)

After reading a thread suggesting that the culprit is most likely calls made to xorg, I ran powertop with the following result:


Wakeups-from-idle per second : 538.9    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  22.0% (136.9)      npviewer.bin : schedule_timeout (process_timeout) 
  17.3% (107.8)      <kernel IPI> : Rescheduling interrupts 
  17.0% (106.1)       <interrupt> : sata_nv, eth0 
  14.1% ( 87.8)          dropboxd : schedule_timeout (process_timeout) 
   8.4% ( 52.4)           firefox : futex_wait (hrtimer_wakeup) 
   7.5% ( 46.9)       <interrupt> : ohci1394, ICE1712 

Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config

...
and when I run top
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
 5746 root      20   0  549m 162m  16m R   67  8.1   2647:12 Xorg                                                                                   
13454 wilson    20   0  200m  64m  14m S   16  3.2 292:31.00 npviewer.bin                                                                           
25020 wilson    20   0  176m  36m  15m S    5  1.8  22:07.99 npviewer.bin                                                                           
 6455 wilson    20   0  242m  45m  12m S    5  2.2 259:38.99 gnome-system-mo                                                                        
 6481 wilson    20   0  300m  33m  13m S    1  1.7   1:51.67 gnome-terminal 

.. ouch!... 67% of my cpu going to xorg.

.....

What would make sense to change/disable? 
How do I do that?

Cheers,

MW

Here are the postings I read:
[https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972)

---

### Post by jocko on 2009-02-20
> **xigen said:**
> I am getting high cpu useage. 
AMD64, ubuntu, nvidia graphics card (vintage 2008)

After reading a thread suggesting that the culprit is most likely calls made to xorg, I ran powertop with the following result:


Wakeups-from-idle per second : 538.9    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  [COLOR=Red]22.0% (136.9)      npviewer.bin : schedule_timeout (process_timeout) [/COLOR]
  17.3% (107.8)      <kernel IPI> : Rescheduling interrupts 
  17.0% (106.1)       <interrupt> : sata_nv, eth0 
  14.1% ( 87.8)          dropboxd : schedule_timeout (process_timeout) 
   8.4% ( 52.4)           firefox : futex_wait (hrtimer_wakeup) 
   7.5% ( 46.9)       <interrupt> : ohci1394, ICE1712 

Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config

...
and when I run top
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
 5746 root      20   0  549m 162m  16m R   67  8.1   2647:12 Xorg                                                                                   
[COLOR=Red]13454 wilson    20   0  200m  64m  14m S   16  3.2 292:31.00 npviewer.bin                                                                           
25020 wilson    20   0  176m  36m  15m S    5  1.8  22:07.99 npviewer.bin                                                                           [/COLOR]
 6455 wilson    20   0  242m  45m  12m S    5  2.2 259:38.99 gnome-system-mo                                                                        
 6481 wilson    20   0  300m  33m  13m S    1  1.7   1:51.67 gnome-terminal 

.. ouch!... 67% of my cpu going to xorg.

.....

What would make sense to change/disable? 
How do I do that?

Cheers,

MW

Here are the postings I read:
[https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972)
I think npviewer.bin is nspluginwrapper (the wrapper for using the 32 bit flash plugin in 64 bit firefox).
It could very well be that npviewer does something that xorg doesn't handle very well.
Try to keep track of what you're doing before xorg starts to use a lot of cpu, specifically to see if it happens after browsing to a webpage that uses flash.
If that's it, you can probably fix it by installing the 64 bit flash plugin. An alpha version is available [here]("http://labs.adobe.com/downloads/flashplayer10.html") and works very well (= better than using nspluginwrapper and the 32 bit version), despite being labled "alpha".

---

