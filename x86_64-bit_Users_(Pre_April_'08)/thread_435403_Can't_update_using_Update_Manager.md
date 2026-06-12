---
title: "Can't update using Update Manager"
date: 2007-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by lcolson on 2007-05-06
I just installed Ubuntu 7.04 from a live cd that I recently downloaded.  It appeared that everything was working correctly, but when I tried to update using the Update Manager under the System --> Administration --> Update manager, it gives me the following message: 

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '39845891' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpSCMEun' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

I am pretty new to linux, and am not sure what to do.  I searched the forums and couldn't find a post that answered this question.  Does anyone here have an idea how I can fix this, or know what I should do?

---

### Post by rai4shu2 on 2007-05-07
A number of bugs in update manager have been fixed since release, so you may have to use a console for now:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by lcolson on 2007-05-07
Thanks,  that worked.

---

