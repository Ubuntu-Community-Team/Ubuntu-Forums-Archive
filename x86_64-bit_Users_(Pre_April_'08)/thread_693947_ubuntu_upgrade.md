---
title: "ubuntu upgrade"
date: 2008-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by seaofpepsi48456 on 2008-02-11
I just upgraded to 64 bit ubuntu,when i try to run Update Manager here is what i get...

E: Could not get lock/var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)

E: Unable to lock the download directory

what does this mean?

---

### Post by Artemis3 on 2008-02-11
[list][*]You are not using sudo (if using the command line)
[*]You have another apt program open (synaptic, adept, gebi, update-manager..)
[*]Your system crashed while in the use of one of these programs, so you have to delete the suggested file.[/list]

---

### Post by seaofpepsi48456 on 2008-02-11
where do i find this file?

---

### Post by Kilz on 2008-02-11
> **seaofpepsi48456 said:**
> where do i find this file?

/var/cache/apt/archives/lock

---

### Post by seaofpepsi48456 on 2008-02-12
Now i'm having java problems...what do i need to play yahoo games?

---

