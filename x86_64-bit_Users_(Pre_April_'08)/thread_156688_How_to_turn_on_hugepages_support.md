---
title: "How to turn on hugepages support?"
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by ivangotoy on 2006-04-07
i have cpu sempron 3000+ and ubuntu 5.10 amd64 installed
i needed to mount hugetlbfs in one directory for a server to make use of huge pages  
that is the result:
root@ubuntu-amd64:/home/ivan# mount -t hugetlbfs none /huge
mount: unknown filesystem type 'hugetlbfs'

---

### Post by skylark on 2006-04-07
I'm guessing hugetlbfs is not on by default in the Kernel packages for Breezy (maybe there is a server one where is on, I haven't checked). To get it working you might look at this guide:  [http://linux.inet.hr/oracle10g_on_debian.html](http://linux.inet.hr/oracle10g_on_debian.html)  note the section: ```
To enable hugetlbpages, first you need 2.6 kernel, and then you need to recompile it with the following config options enabled:
CONFIG_HUGETLB_PAGE=y
```

PS: you might get more info if you post in the server forum too since normal desktop users won't care about hugepages!

---

