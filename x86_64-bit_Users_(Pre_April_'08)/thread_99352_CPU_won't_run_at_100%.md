---
title: "CPU won't run at 100%"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by loupy on 2005-12-05
I have an AMD64 3400+ and am running kubuntu 5.10.  in the power monitor it says I am running at 2.2ghz but when I do a cat /proc/cpuinfo it shows I am only at 801mhz.  Even when I try to change the performance profile it never goes above 1.6ghz.  Is there a known issue with acpi in the 64bit distro? Am I doing something wrong?

---

### Post by 23meg on 2005-12-05
See if ```
sudo killall powernowd
``` changes anything. If so, it's most likely a dynamic speed scaling problem.

---

### Post by loupy on 2005-12-05
Sorry - I should've mentioned that without powernowd it does run at 100%.  But then my battery will get clobbered when I am not plugged in.  Is there anyway to get the frequency scaling to work right?

---

### Post by 23meg on 2005-12-05
Well, you also didn't mention that you were using a laptop. See if you can find anything by doing a search in the forums and the wiki; I recall seeing this issue come up a few times but don't have a solution myself since I don't use AMD64.

---

### Post by loupy on 2005-12-05
I did an extensive search and came up empty, which is why I posted my question.

In terms of not mentioning a laptop - who would need powernowd and stepping on a desktop or server??

This mode of communication does not serve well for vocal inflections, but I took your tone as rude.  The one thing I like about Ubuntu and this forum is the helpful, courteous atmosphere - I found your last reply to be less than that.

Nonetheless, I thank you for attempting to help me.

---

### Post by manzuk on 2005-12-07
Ok, I'm a totally newbie, but as far as i know, powernowd can be used in desktops so as to take advantage of AMD coolNquiet technology... Your processor works at a lower speed, so it needs less power, what means less heat, less fans RPM, and less noise...
Correct me if i'm mistaken.
Love kubuntu! bye...

---

