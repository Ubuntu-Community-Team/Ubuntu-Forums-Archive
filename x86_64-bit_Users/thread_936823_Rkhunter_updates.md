---
title: "Rkhunter updates"
date: 2008-10-03
forum: x86 64-bit Users
---

### Post by Maintech on 2008-10-03
I run x64 on a dual core and on a quad core. I also run x32 on several different computers. I have noticed that rkhunter runs slower and finds less on the x32 to complain about than on the x64. After every system update on the x64 I have several new "warnings". I don't get that with the x32. I have not been able to get a single update for rkhunter since installing the long term Ubuntu. No updates for x64 nor for x32. This is not the same as it has been in the past. Rkhunter will continue to give warnings after every update until the MD5 sums are updated in Rkhunter to reflect the updates in programs that Ubuntu has released. This lack of updates for Rkhunter poses many issues but in particular causes confusion in determining whether the security of the system has been breached.

Is this Rkhunter's fault or Ubuntu's? Why is this important package not kept up to date? Chkrootkit is ok but is very limited.

---

### Post by Yellow Pasque on 2008-10-03
The devs of rkhunter don't decide what version gets into Ubuntu or when it's updated. If you're unsatisfied with Ubuntu's update frequency, then build it from source. [http://sourceforge.net/project/showfiles.php?group_id=155034&package_id=172567](http://sourceforge.net/project/showfiles.php?group_id=155034&package_id=172567)
Before you do that, run this to get the dependencies:
```
sudo apt-get build-dep rkhunter
```

---

