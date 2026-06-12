---
title: "audio doesn't work on Ubuntu 12.10: threading model error"
date: 2012-12-01
forum: Wine
---

### Post by rclocher3 on 2012-12-01
Hi all,

I have a Lenovo S10-3 ideapad (netbook).  I installed Wine (version 1.4.1) yesterday on Ubuntu 12.10 via the Software Center, and right out of the box the audio doesn't work.  When I click "Test Sound" in winecfg, this error message pops up in the terminal:

```
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
```The selected audio driver is winealsa.drv.  The output device is "(System default)"; I tried changing it to "HDA Intel - ALC272 Analog", with no improvement.

I've done hours of Google searching, and not knowing any better, I tried the advice from this thread [http://ubuntuforums.org/showthread.php?t=2010239](http://ubuntuforums.org/showthread.php?t=2010239)
which had me install the "ia32-libs-multiarch" package, which I installed via "apt-get".  That didn't seem to have any effect either.

I tried running a relatively simple Windows application, and everything worked fine but the sound.

I found this forum thread: [http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599) , and being a superstitious person I followed these instructions without being sure whether they applied to me:[INDENT]"Q: I want to know if a sound related bug is caused by winepulse or not.
A: Go to winecfg, in the tab 'libraries', enter 'winepulse.drv' in the  box and click on add, click yes on the warning. Select winepulse.drv and  change load order to 'disabled'. Now try to trigger your bug again, if  it was a winepulse bug it shouldn't trigger any more. To undo the  change: select 'winepulse.drv' and click 'delete'."
[/INDENT]Unfortunately that didn't work: the "Test Sound" button still had no effect.

Can anyone suggest what to try next to solve this problem?  Should I report it as a bug?

- Rob

---

### Post by rclocher3 on 2012-12-06
I decided to report this issue as a Wine bug:
[http://bugs.winehq.org/show_bug.cgi?id=32378](http://bugs.winehq.org/show_bug.cgi?id=32378)

---

