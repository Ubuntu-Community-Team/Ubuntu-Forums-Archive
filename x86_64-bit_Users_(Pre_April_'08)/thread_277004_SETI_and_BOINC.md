---
title: "SETI and BOINC"
date: 2006-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by tenderflesh on 2006-10-13
I just installed boinc-client and boinc-manager(5.4.9-1), they both run! But, when I try to run the 'update' command in the BOINC Manager, I get the error message: "Message from server: platform 'x86_64-pc-linux-gnu' not found"...


do I have to install other stuffs like 'setiathome'? or should I edit 'app_info.xml'? Please Help!

---

### Post by sheenaramone on 2006-10-13
I guess from that message, you are using 64 bit Ubuntu.  Synaptic package manager installs 64 bit BOINC, but there are not that many projects with 64 bit applications.

I have been using 64 bit Dapper to run 32 bit BOINC and Seti.  I download it from the BOINC site and run it in the home folder.

---

### Post by tenderflesh on 2006-10-13
thanks a lot!!! the script works great on my machine!! :-D

---

### Post by orthopod on 2007-10-20
My setiathome runs are taking significantly longer, now that I';'m running gutsy. I checked and see that Im running an SMP core on my AMD 5600.  projects running at 100% but now take 12 hours instead of 4

---

### Post by Evil Blu Jedi on 2007-10-20
I have also found that boinc runs slower on my laptop under Gutsy.  I ran the boinc cpu benchmarks, and they came out half as fast as they did under Feisty.  Does anyone out there know the reason why?

---

### Post by LO Matt on 2007-10-20
> **Evil Blu Jedi said:**
> I have also found that boinc runs slower on my laptop under Gutsy.  I ran the boinc cpu benchmarks, and they came out half as fast as they did under Feisty.  Does anyone out there know the reason why?

Half as fast? check your powersaving options.  Maybe your processor is scaled down for niced processes.  I've seen CPU scaling behaviour change when upgrading distributions before.

---

### Post by Evil Blu Jedi on 2007-10-21
I checked, and sure enough it was scaled.  I changed it and ran benchmarks.  They came out to be the same as the Feisty speeds.  Thanks for your help.

---

### Post by orthopod on 2007-10-24
Looks like I had the same problem - my cpu was scaled down to only 1000 MHZ from 2800.  Now my Seti times are much better
I added to my Gnome panel the power scaling applet and did this
sudo chmod +s /usr/bin/cpufreq-selector

now I can controll the freq by left clicking on the gnome panel applet.

---

### Post by tomdkat on 2007-10-24
> **LO Matt said:**
> Half as fast? check your powersaving options.  Maybe your processor is scaled down for niced processes.  I've seen CPU scaling behaviour change when upgrading distributions before.Why would the CPU be scaled down for a "niced" process if the system is basically idle, thereby giving effective priority to the "niced" process?

Peace...

---

### Post by LO Matt on 2007-10-25
What I mean is, one of the options for powersaving is whether the cpu scales up to 100% for niced processes.  You can have it scale to 100%, or remain at a lower frequency for low priority processes . . . only scaling up for higher priority tasks. ;)

Read this for more info on "nice", it may clarify.  [Nice wiki]("http://en.wikipedia.org/wiki/Nice_(Unix)")

M

---

### Post by leona on 2008-02-20
ok, this sounds good, I have the same prob, so how can I check / correct this?

Aww not to worry I found out [here]("http://ubuntuforums.org/showpost.php?p=3980277&postcount=4")

---

