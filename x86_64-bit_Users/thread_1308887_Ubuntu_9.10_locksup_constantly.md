---
title: "Ubuntu 9.10 locksup constantly"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by noob707 on 2009-11-01
I have had this problem since 9.04 64-bit ubuntu. 9.04 would lock-up every 2mins or so. Coming around to the 9.10 release 64-bit Ubuntu, it locks-up and i have to hard reset every 10mins or so or during certain tasks that trigger it.When it usually locks-up.

this is a fresh install of 9.10 so no graphic drivers and other stuff installed. I have an nvidia graphics card.

* Update manager
* when another application is open/running and i launch firefox
* firefox while browsing or flash applications
* games
* extensive tasks

I used linux mint 7 for a few months to try it out and it never locked-up on me once during the whole time on the same machine.

---

### Post by edantes on 2009-11-01
Look for suspicious activity at the syslog. 

System->Administration->Log FileViewer->syslog


For example, I had a similar problem with unexplained lockups with 9.04.  It turned out to be ath5k wireless driver misbehaving with my hardware.

---

### Post by noob707 on 2009-11-01
It locks up always when i try to download something like synaptic, ubuntu software centre, internet, update manager and etc. The syslog seems fine as i dont knwo what to look for but after it does all the routine start-up taks, if continues to cycle through this:

Nov  1 14:03:06 max-laptop kernel: [   56.860021] eth0: auto-negotiating...
Nov  1 14:03:14 max-laptop wpa_supplicant[1475]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 14:03:16 max-laptop kernel: [   66.920021] eth0: auto-negotiating...
Nov  1 14:03:26 max-laptop kernel: [   76.980024] eth0: auto-negotiating...
Nov  1 14:03:36 max-laptop kernel: [   87.040041] eth0: auto-negotiating...
Nov  1 14:03:46 max-laptop kernel: [   97.100027] eth0: auto-negotiating...
Nov  1 14:03:54 max-laptop wpa_supplicant[1475]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 14:03:56 max-laptop kernel: [  107.170030] eth0: auto-negotiating...
Nov  1 14:04:06 max-laptop kernel: [  117.230106] eth0: auto-negotiating...
Nov  1 14:04:16 max-laptop kernel: [  127.290022] eth0: auto-negotiating...
Nov  1 14:04:26 max-laptop kernel: [  137.350022] eth0: auto-negotiating...
Nov  1 14:04:36 max-laptop kernel: [  147.410020] eth0: auto-negotiating...
Nov  1 14:04:46 max-laptop kernel: [  157.470023] eth0: auto-negotiating...
Nov  1 14:04:54 max-laptop wpa_supplicant[1475]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 14:04:56 max-laptop kernel: [  167.530025] eth0: auto-negotiating...
Nov  1 14:05:06 max-laptop kernel: [  177.590024] eth0: auto-negotiating...
Nov  1 14:05:16 max-laptop kernel: [  187.650034] eth0: auto-negotiating...
Nov  1 14:05:26 max-laptop kernel: [  197.710019] eth0: auto-negotiating...
Nov  1 14:05:37 max-laptop kernel: [  207.770022] eth0: auto-negotiating...

I am using the atk9k driver with the kernel.

---

