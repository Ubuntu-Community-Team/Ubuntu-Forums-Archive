---
title: "cpufreq setting the wrong upper frequency"
date: 2006-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by koshcu on 2006-11-18
I am running edgy 64bit edition and I have a dual 2218 opteron system. I was originally using powernod but that did not seem to throttle the processors very well under load so I switched to cpufreqd. I have a problem though when it starts it sets the min and max frequences to 1Ghz and the max frequency should be 2.6Ghz. I can set it manually through the sys interface and that works however

sudo /usr/bin/cpufreq-set --max 2600 --min 1000 --cpu 0

does not work. It just sets the min and max values to 1000 and that is how cpufreqd is trying to set those values.

I suppose I could just make my own init scripts to correct those values on every boot but it seems like it should just be fixed.

Would appreciate any ideas you guys have.

---

### Post by Sebastral on 2007-02-21
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

gives me three zeros more then you so try

sudo /usr/bin/cpufreq-set --max 2600000 --min 1000000 --cpu 0

---

### Post by simoncullen on 2008-02-13
One other thing: 

```
$ sudo /usr/bin/cpufreq-set --max 3000000 --min 2000000 --cpu 0
```

has no effect.  


But it will adjust to a lower max frequency, e.g., 2.6Ghz : 

```
simon@aristurtle:~$ sudo /usr/bin/cpufreq-set --max 2160000 --min 2000000 --cpu 0
```

effectively lowers the clock to 2.16Ghz.


So I don't think this is a reporting problem .... but a cpufreq/powernowd problem.

edit:  Seems like it might be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91553](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91553)

---

