---
title: "firmware updater, how to debug problem?"
date: 2008-05-27
forum: Wine
---

### Post by PadreSol on 2008-05-27
Trying to run a firmware updater for the cd/dvd drive but when I run it under Wine there's no output to stdout and no indication of anything really.  How can I see what's happening?  I tried strace but that didn't light any lightbulbs.

---

### Post by cogadh on 2008-05-27
Never run a Windows based firmware updater in Wine, it is very likely to "brick" your hardware.

---

### Post by PadreSol on 2008-05-28
> **cogadh said:**
> Never run a Windows based firmware updater in Wine, it is very likely to "brick" your hardware.

So no way to debug/trace an app that runs inside Wine?


...I tried to preserve my windows partition but the vers. 8 installer put my laptop to sleep in the middle of creating the partition for vers. 8.  Buh-bye windows partition.  Not a nice feature.

---

### Post by cogadh on 2008-05-28
Sure you can debug/trace Wine:
```
WINEDEBUG=+trace1,+trace2,-trace3 wine your_program.exe &> /tmp/output.txt
```
You can find the list of available debug channels [here](http://wiki.winehq.org/DebugChannels).

But again, I really don't recommend you continue with this. Wine does not have the necessary hardware access to update firmware properly. At best, it won't work at all, at worst it will screw up the firmware and leave you with a non-functional drive. You would be much better off downloading a bootdisk style firmware updater from the manufacturer.

---

### Post by PadreSol on 2008-05-28
> **cogadh said:**
> Sure you can debug/trace Wine:
```
WINEDEBUG=+trace1,+trace2,-trace3 wine your_program.exe &> /tmp/output.txt
```
You can find the list of available debug channels [here](http://wiki.winehq.org/DebugChannels).

But again, I really don't recommend you continue with this. Wine does not have the necessary hardware access to update firmware properly. At best, it won't work at all, at worst it will screw up the firmware and leave you with a non-functional drive. You would be much better off downloading a bootdisk style firmware updater from the manufacturer.

Ok, cool, thanks. It's an older drive and there's no other firmware update.
I will try to figure out how to make a bootable windows cd and try running it from that.

---

### Post by cogadh on 2008-05-28
If you are talking about making a "live" Windows CD, that can't be done. What make and model is the CD/DVD drive? Is there a particular reason you need to update the firmware? Generally speaking, unless the firmware update specifically fixes some particular problem you are having, you really shouldn't update it.

---

