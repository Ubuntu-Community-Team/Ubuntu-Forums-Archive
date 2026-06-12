---
title: "cpu scaling brakes powerful processors"
date: 2007-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by kiev on 2007-11-24
I install cpufrequtils, and run cpufreq-info and surprised - is frequency of processor in 2.6 times below working and rises very rarely - for example in different videos, and in ordinary work of atlon x2 5000 works on frequency only 1&#1043;&#1043;&#1094; in place of 2.6&#1043;&#1043;&#1094; - that more than in 2 times slower.

For the correction of it - I added in /etc/rc.local line
/usr/bin/cpufreq-set -g performance (before exit 0)
and was surprised - all began to work in 2 times quick!!! all indeed became quick and it very much notedly

---

