---
title: "I need help with MSXML"
date: 2008-08-04
forum: Wine
---

### Post by rmainard on 2008-08-04
I am a realtor in San Diego and am trying to completely convert to Linux. The problem is that when I try to access the San Diego MLS it requires Internet Explorer 6 or better because the website runs on MSXML. I have installed ies4linux and can get in but it doesn't show all the images or the links to the tools on the navigation header. Has anyone found a solution to this? The MLS we use is Tempo 5, it actually says I need IE 6 or Higher, I tried the User Agent switch in Firefox but the website returns a message saying MSXML 3 or later is required. I know IE 6 has this but for some reason it just doesn't work right, is there a way to update the MSXML in ies4linux? Please please please help!

---

### Post by dmn_clown on 2008-08-05
> **rmainard said:**
> I know IE 6 has this but for some reason it just doesn't work right, is there a way to update the MSXML in ies4linux? Please please please help!

I would suggest updating to wine 1.1.2 which had a plethora of msxml fixes/updates [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by rmainard on 2008-08-06
Thanks for the advice dmn_clown I gave it a try and I still have the same problem. I thought that it might be a Java issue so I installed that as well but it didn't work either. If anyone else has a possible solution please let me know.

---

### Post by rmainard on 2008-12-15
Well the only way to run the San Diego MLS Website is through Internet Explorer, period, there is no way around it. I have a solution but it is not one I really like as it means using software developed by a company I personally hate. So I use virtualbox ose and a VM of windows XP this seems to work pretty good and just as smooth as if I was actually running windows as the primary OS on my computer, better than QEMU and is cheaper than VMWARE, it is free. I hope this helps someone else down the road.

---

