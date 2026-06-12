---
title: "Firefox32 add-ons problem"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by _mOrgoth_ on 2008-05-04
Hi... I installed firefox32 using this script on Ubuntu8.04x64.(this how to:[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)) It works fine but when I try to install add-ons it always produce error -203(unexpected installation error). Is there any solution??

---

### Post by BatmansGehilfe on 2008-06-02
Hi there

I'm experiencing the same problem. As I was unable to find a solution for this, I would be glad for any help! I'm using Hardy 64 and I've installed firefox32 and swiftweasel with the script located [here]("http://ubuntuforums.org/showthread.php?p=1174435"). Unfortunately they both don't work. Also, they seem to share the profile folder with the ff3 I'm using for the usual browsing. The add on I'm trying to run is a bluetooth-syncing applet for scheduleworld found [here]("http://wiki.scheduleworld.com/wiki/FireFox_Configuration"). It seems only to run on ff32, that's why I installed it.

Thanks in advance!

---

### Post by Kilz on 2008-06-02
> **_mOrgoth_ said:**
> Hi... I installed firefox32 using this script on Ubuntu8.04x64.(this how to:[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)) It works fine but when I try to install add-ons it always produce error -203(unexpected installation error). Is there any solution??

> **BatmansGehilfe said:**
> Hi there

I'm experiencing the same problem. As I was unable to find a solution for this, I would be glad for any help! I'm using Hardy 64 and I've installed firefox32 and swiftweasel with the script located [here]("http://ubuntuforums.org/showthread.php?p=1174435"). Unfortunately they both don't work. Also, they seem to share the profile folder with the ff3 I'm using for the usual browsing. The add on I'm trying to run is a bluetooth-syncing applet for scheduleworld found [here]("http://wiki.scheduleworld.com/wiki/FireFox_Configuration"). It seems only to run on ff32, that's why I installed it.

Thanks in advance!

Its possible that firefox is sharing a profile folder with firefox 3. That is a problem when you want to add extensions written for firefox 2. Firefox32 is still based on Firefox 2 untill Firefox 3 is released. I will not make packages for a buggy pre release and then have to support the bugs.
But swiftweasel32 does not share a profile or settings folder with any firefox. You should be bale to install the extension to it.

---

### Post by BatmansGehilfe on 2008-06-03
Thanks a lot for the answer. First Swiftweasel seemed to share the profile-folder with ff. But then I deleted the swiftweasel-folder in .mozilla, and restarted the browser. It still didnt work, but at least swiftewasel now didn't have the same addons as ff3 anymore. Then I deleted anything that had to do with "extension" within the .mozilla/swiftweasel folder and it worked like a charm. Just in case anyone has the same problem.

Cheers

---

