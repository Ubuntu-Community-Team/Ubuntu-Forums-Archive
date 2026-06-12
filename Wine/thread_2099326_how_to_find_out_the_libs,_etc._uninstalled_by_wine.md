---
title: "how to find out the libs, etc. uninstalled by wine"
date: 2012-12-29
forum: Wine
---

### Post by tlee on 2012-12-29
Greetings--

I recently tried to install WINE from the command line using apt-get.  It didn't work, and that's okay because I found a different solution to the problem that prompted me to try installing it.  But in the attempted installation, it needed to uninstall a long list of items.  This resulted in some new problems, so I'd like to find out what that list comprised and reinstall them.  Any thoughts on how to do that?


Thanks!

---

### Post by Toz on 2012-12-29
You can either have a look at the History section of the Software Centre or the /var/log/apt/history.log file for this information.

---

### Post by tlee on 2012-12-29
Great, thank you!

---

