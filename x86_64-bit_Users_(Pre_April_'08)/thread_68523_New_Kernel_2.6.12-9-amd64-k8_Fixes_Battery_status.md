---
title: "New Kernel 2.6.12-9-amd64-k8 Fixes Battery status"
date: 2005-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by jshein on 2005-09-23
**Informational post**

I installed the new 2.6.12-9-amd64-k8 kernel this morning and I now have battery status!

Acer TravelMate 4400
AMD Turion64 ML-30

Now if only I could get ndiswrapper and the madwifi drivers to work...

---

### Post by GuyveR800 on 2005-09-23
Same here on Acer Aspire 5024WLMi! Additionally, the time is no longer running too fast! (No more need for noapic or no_timer_check boot options)

Thanks, whoever :)

---

### Post by bdaw on 2005-09-24
Yeah... I'm happy with acer 5025WLMi and new kernel too!

Any idea how to make hibernation working? :) 

I used to have blank screen after power on - now it halts douring hibernating with some acpi errors....

---

### Post by Confuse on 2005-09-25
You mean that you no longer have to load a hacked DSDT? I'm running the same kernel version but not sure if its due to my putting my dsdt in /etc/mkinitrd folder. Any info would be highly appreciated. I'm running an Acer Aspire 3000 which is similar to the 5000 model.

---

### Post by GuyveR800 on 2005-09-25
[QUOTE=Confuse]You mean that you no longer have to load a hacked DSDT? I'm running the same kernel version but not sure if its due to my putting my dsdt in /etc/mkinitrd folder. Any info would be highly appreciated. I'm running an Acer Aspire 3000 which is similar to the 5000 model.[/QUOTE]
 While an Aspire 3000 and 5000 are indeed similar, they use a different chipset than the 3020 and 5020.
3000/5000 have a SIS760 chipset, while the 3020/5020 have an ATI chipset.

But it doesn't hurt to try, does it? :)

---

### Post by jshein on 2005-09-26
Update:

Hibernate works for me if **noapic** is used as a kernel boot option. I did about 20 consecutive hibernate / resumes to ensure.

Suspend to ram partially works, but crashes X upon starting up again.

---

