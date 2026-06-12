---
title: "Kpowersave, on-demand, and a slow handbrake transcode?"
date: 2009-05-06
forum: x86 64-bit Users
---

### Post by markley268 on 2009-05-06
so my basic problem is that i just upped my hardware to the new 955 AMD phenom II chip, 3.2GHz, and my handbrake transcodes are only maxing out at around 75% cpu util.....w/ some of the cores not at the full 3.2GHz.  What gives?  On ya, i also recently upped from 8.10 x64 server to the new 9.04 x64 server.

Kpowersave says the current cpu frequency policy is 'unknown'

cpufreq-info says the following for all 4 cores, w/ various 'current' cpu speeds ranging from the 2.5 to 3.2 during the handbrake operation:

analyzing CPU 3:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 3
  hardware limits: 800 MHz - 3.20 GHz
  available frequency steps: 3.20 GHz, 2.50 GHz, 2.10 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 3.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 3.20 GHz:6.85%, 2.50 GHz:2.25%, 2.10 GHz:38.69%, 800 MHz:52.21%  (813)

system settings - power management tells me that cpu frequency scaling is not supported, and that powerdevil was compiled without xext support.

supported cpu policies: no methods found
supported schemes: performance, powersaving

in the 'view activity' window for handbrake, the x264 info says it's only using two special instructions....MMX2 and SSE2Fast


The whole idea of upping my hardware was so i could transcode many times faster than previously w/ my x2 3800+, but i'm only averaging around 33fps on an apple universal encode from mpeg2.

Any ideas?

---

### Post by Yellow Pasque on 2009-05-07
> **markley268 said:**
> w/ some of the cores not at the full 3.2GHz.
The cores should all operate at the same speed (hardware limitation)

> in the 'view activity' window for handbrake, the x264 info says it's only using two special instructions....MMX2 and SSE2Fast
What do you want it to use? If it's using SSE2, that's probably as much optimization as you're going to get without building from source and using specific compile flags (like -O3 or -O6)

> Any ideas?
See if the CPU scaling is slowing you down. Before your next transcode, use:
```
sudo cpufreq-set -G performance
```
(You can set it back to CPU scaling with the same command using 'ondemand' instead of 'performance')

---

### Post by markley268 on 2009-05-07
Ok, so with the performance setting.....i encoded a 30min "my name is earl" show, starting at 7:32:04 and finishing at 7:48:20, about 16 minutes, but the responsiveness of my 'top' and kde window went to crap, and i still never saw the 'top' report a cpu util over 80%

the same encoding with the ondemand setting took from 7:52:24 to 8:14:32, so 22 minutes.....

---

### Post by markley268 on 2009-05-07
> **Temüjin said:**
> The cores should all operate at the same speed (hardware limitation)



Then Kpowersave & cpufreq-info aren't showing me what's really going on, cause they both clearly shows that some cores are operating at one frequency and others at a different frequency....for example (during an 'ondemand' encode....)

server:~$ cpufreq-info
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@lists.linux.org.uk[/email], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 3.20 GHz
  available frequency steps: 3.20 GHz, 2.50 GHz, 2.10 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 3.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
 ** current CPU frequency is 3.20 GHz.**
  cpufreq stats: 3.20 GHz:85.02%, 2.50 GHz:0.19%, 2.10 GHz:2.93%, 800 MHz:11.87%  (846)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 800 MHz - 3.20 GHz
  available frequency steps: 3.20 GHz, 2.50 GHz, 2.10 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 3.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  **current CPU frequency is 2.10 GHz.**
  cpufreq stats: 3.20 GHz:85.17%, 2.50 GHz:0.19%, 2.10 GHz:2.93%, 800 MHz:11.71%  (934)
analyzing CPU 2:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 2
  hardware limits: 800 MHz - 3.20 GHz
  available frequency steps: 3.20 GHz, 2.50 GHz, 2.10 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 3.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  **current CPU frequency is 2.50 GHz.**
  cpufreq stats: 3.20 GHz:85.23%, 2.50 GHz:0.19%, 2.10 GHz:2.95%, 800 MHz:11.63%  (934)
analyzing CPU 3:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 3
  hardware limits: 800 MHz - 3.20 GHz
  available frequency steps: 3.20 GHz, 2.50 GHz, 2.10 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 3.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  **current CPU frequency is 2.10 GHz.**
  cpufreq stats: 3.20 GHz:85.24%, 2.50 GHz:0.21%, 2.10 GHz:2.90%, 800 MHz:11.65%  (1040)

---

