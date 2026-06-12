---
title: "64 bit version of Ubuntu with Thunderbird/Lightning and Provider for Google Calendar"
date: 2008-07-30
forum: x86 64-bit Users
---

### Post by thenetduck on 2008-07-30
Hi
I am looking for a solution and was wondering if there was one yet. I am using Hardy Heron 64 bit and would like to sync my calendar with google calendar. Does anyone know if there is such a solution available as of yet? 

Thanks 
The Net Duck

See this thread... solution semi found. 

[http://ubuntuforums.org/showthread.php?t=746637](http://ubuntuforums.org/showthread.php?t=746637)

---

### Post by sunny_nwho on 2008-07-30
I would suggest using swiftdove an optimised version of Thunderbird. It comes with lightning, so syncing with google calendar should not be a problem

check [http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/) you can find the apt lines there

---

### Post by hotrod6657 on 2008-08-04
Post number 6 in the linked threat is gold!

I installed that version of lightening and provider for google worked like a charm.  Hope it works for you too.

hotrod

---

### Post by 1011101 on 2009-03-31
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.9/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.9/contrib/linux-x86_64/)

---

### Post by gewitty on 2009-05-14
> **1011101 said:**
> [http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.9/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.9/contrib/linux-x86_64/)

Just installed this to get Lightning/Google Calendar working in Thunderbird. However, when I restarted Thunderbird I got the follwoing error message: 

"The calendar data in your profile was updated by a newer version of Lightning and continuing will probably cause the information to be lost or corrupted. Thunderbird [*I think they actually mean Lightning*] will be disabled and Thunderbird restarted."

Since I recently moved from using Hardy on a 32 bit machine, to using Jaunty on a 64 bit machine, I'm guessing that the Thunderbird profile I brought across is somehow incompatible (or at least the Lightning bit is). 

I'm not sure how to clear this problem though. Can anyone suggest a solution?

---

### Post by catalina on 2009-05-28
Here is a possible solution.  
1.  Go to synaptic package manager and uninstall the lightening extension that may be enabled.
2.  Go to "Tools" "Add-ons" "Extensions" and disable any occurrence of Lightening.
3.  Go here [http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.9/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.9/contrib/linux-x86_64/) and download 64 bit copy of lightening and install.

***You may need to uninstall any extensions that depend on lightening ie. Google Calendar provider.

My problem was I had lightening installed from synaptic which is not compatible with the version or profiles of lightening that I had installed.  After doing this I could access all the calendar apps I had installed.  I reinstalled google calendar provider and all my calendar settings were in tact.

Hope it helps.
Dean.

---

### Post by gewitty on 2009-05-29
Thanks a lot Catalina. That solution worked!

---

