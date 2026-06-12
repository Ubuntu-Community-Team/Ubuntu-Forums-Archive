---
title: "Weird Problem....Gutsy.....?????"
date: 2007-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by zeus09 on 2007-11-17
Hi all,
I have a weird problem concerning the Gutsy,
I installed gusty about two days ago and since then the computer has been constantly uploading data, but i dont know where.
The system moniter shows that SENT data is always increasing, but i am not uploading anything, as soon as i start the system the sent data starts increasing and it will go upto 5-6GB in a span of about 3 hours.......strange.
I have firestarter installed and it shows the same results regarding the sent data, and another strange thing is even if u use the Lockdown feature available with Firestarter, the computer continues to upload.
I have also used iftop, to very verify the bandwidth consumption, it does not show anything suspicious.
Should i be worried about this or is this a bug in GUTSY ?????
Please help, cause i am on the verge of uninstalling Gutsy.
Thanks
Zeus

---

### Post by ViRMiN on 2007-11-17
Run "netstat -aep" from a terminal window; that'll show you open connections and what program it is that has the connection.  It may help identify something?

---

### Post by zeus09 on 2007-11-19
> **ViRMiN said:**
> Run "netstat -aep" from a terminal window; that'll show you open connections and what program it is that has the connection.  It may help identify something?

HI,
i used netstat -aep, but i dont understand how to interpret the results
Zeus

---

