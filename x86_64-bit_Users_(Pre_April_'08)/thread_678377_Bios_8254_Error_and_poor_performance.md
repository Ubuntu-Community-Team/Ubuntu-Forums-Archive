---
title: "Bios 8254 Error and poor performance"
date: 2008-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dual_Chikara on 2008-01-25
I have Gutsy 7.1 installed and running on my machine. The only problem is that every time I boot up, I get an error displayed reading... "MP-BIOS bug 8254 timer could not be found..." The system then boots and runs, but is twitchier than Windows. Also, Ubuntu is reading my Athlon 64 as running at one GHz, even though it can run 2.4 Ghz normally. How can I fix this error, or is it even the cause of my poor performance?

---

### Post by James79 on 2008-01-26
If Ubuntu reports your cpu speed as 1ghz it simply means that [Cool and Quiet ]("http://en.wikipedia.org/wiki/Cool'n'Quiet")is enabled and working. This is not a cause for concern and should not hinder performance.

---

### Post by Dual_Chikara on 2008-01-26
Ok, if that solves the performance issue, what is the bug doing? If at all possible I would like to fix it.

---

### Post by borissamaru on 2008-02-18
Hi,

Did you get any answers about the 8254 bug?
I am a new Ubuntu user, and got the same problem after upgrading to 7.10.

I am not sure if it has any consequences, but I know I did not use to get it on my previous version
(6.XX  Edgy ..... whotsit!).

---

### Post by lanzen on 2008-02-18
I'm getting the 8254 error since I switch to Gutsy. Apparently everything worked fine except I had the big freezes as in threads [http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905) and [http://ubuntuforums.org/showthread.php?t=585714](http://ubuntuforums.org/showthread.php?t=585714). I solved them by installing the new nvidia driver.

8254 might be a concurring cause to that, but it's otherwise not affecting performance.

---

