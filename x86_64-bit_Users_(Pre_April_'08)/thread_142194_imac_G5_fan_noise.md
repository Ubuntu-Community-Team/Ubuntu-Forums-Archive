---
title: "imac G5 fan noise"
date: 2006-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by pinkllama on 2006-03-09
hi everyone,

i have an imac G5 1.8 17" rev b running os x and have tried in vain to reduce the noise from the extremely loud fans. Could anyone who has installed ubuntu/kubuntu on an imac G5 tell me if the fan noise has decreased at all. am i right in thinking that its the operating system i.e os x or ubuntu/kubuntu that controls the fans and not some firmware in the computer?

i love os x but I'II switch in a flash if it helps.

thanks in advance

---

### Post by BoneKracker on 2006-03-10
The general answer to your question is no.  But I will qualify that with the following:

If your hardware supports it, in Linux you can choose from a number of cpu frequency profiles.  Using a conservative profile will draw less power (which turns into heat) when you are not placing a load on the processor.  If your machine varies fan speed according to temperature (typically a BIOS function), this will also reduce noise when not under load.

Let's wait and see if someone who knows your machine can answer whether cpufreq works on it.  Mine is an old Mac and my knowledge of cooling stuff is limited to PCs I've built.

Also consider:

You could also look into replacing the fans with higher-quality ones (engineered for lower noise), or larger but lower RPM ones (generally less noisy).  On some machines, placing an insulating gasket between the fan mounting and the case reduces some noise that comes from vibration.

If you are really serious about it (e.g., you are recording sound and really need it to be quiet) you could modify the computer to be liquid-cooled.  This will certainly void any warranty you have, cost hundreds of dollars, take days of time, and if you do it wrong you'll ruin your computer. Probably not worth doing on an iMac.  You could also trash it and get a Mini - I don't think they even have a fan.

---

