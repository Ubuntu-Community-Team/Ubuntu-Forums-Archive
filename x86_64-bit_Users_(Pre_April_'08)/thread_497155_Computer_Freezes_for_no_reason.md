---
title: "Computer Freezes for no reason"
date: 2007-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by HRCerqueira on 2007-07-09
Hello all,

I'm running ubuntu 7.04 on a asus f3jc laptop, core duo T5500. Randomly, the computer completely freezes, just the mouse keeps moving. The rest completely freezes, i try to hit ctrl + alt + f#, alt + sys req (i read somewhere that this sometimes unfreeze the computer), not even the caps lock and similar keys do nothing (usually, the associated led should switch state). The only way i have is to use the power button to shutdown the computer and start again. At first i thougth this was an hardware issue, but i have another linux distro (a SUSE based one) on another partition, and this doesn't happen.

I'm not looking for you to know the solution,  i just want to have a clue for where to start looking for a possible problem, any log file, or hardware driver, anything...

Any help would be greatly appreciated. Cheers,
Hernâni

---

### Post by Cappy on 2007-07-09
I assume you mean Control+Alt+backspace. Try adding boot parameter 
```
noapic nolapic
```

more instructions if needed:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by HRCerqueira on 2007-07-09
I was not talking about ctrl alt backspace, although i tried that to. Wath does that parameter do actually?

---

### Post by mariosbar on 2007-07-09
Well first of check to how many processes you have running its possible your chip (or chips could be over heating) have you defragmented ur drive also check to make sure ur fan is working that that u have enuf ram memory fir ut operating system.

[www.marios-bar.com](www.marios-bar.com)

---

### Post by HRCerqueira on 2007-07-10
Hum, about the ram i have 2gbs of it, and 512mb video ram. About the processes, it's a bit hard to find that out, because when the system freezes i can't see them, but i guess that's not the problem also, because the problem is very random, it can happen a few minutes after booting, or just some hours after. Sometimes I'm just browsing, other times I'm working, and i do some heavy stuff on the computer. And i don't think the problem is over heating, I've pondered that before, but as I said, i have another linux distro on my computer and it works flawlessly for many hours.

My main guess is some driver issue,  but i don't know how to check on that, although i use linux since debian rex, I'm not an expert in any ways, every time i have a problem I try to fix it googling or asking on forums, but i easily forget the solution and wath i did.

---

### Post by HRCerqueira on 2007-07-10
> **Cappy said:**
> I assume you mean Control+Alt+backspace. Try adding boot parameter 
```
noapic nolapic
```

more instructions if needed:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Thanks, worked like a charm... Many many thanks...

Cheers,
Hernâni

---

### Post by fhco on 2007-07-11
I was actually having this exact same issue, and indeed adding the boot parameter "noapic nolapic" stopped the errors that were showing up in syslog as well as the crashes. The only problem is, my second core (Core 2 Duo) is not showing up in my process monitor. Is there a way to fix that? Does that mean that my second core is not being utilized?

---

### Post by zero244 on 2007-07-11
Does it freeze when your running a particular program like Firefox.
I was having freeze problems and it was a defective video card. But it could be just about anything including a conflict with a hardware driver or a malfunctioning device etc.
You need to trace back to before you were having problems and see if you've done something or changed something before the freeze ups started.
Good Luck

---

### Post by HRCerqueira on 2007-07-11
> **zero244 said:**
> ...You need to trace back to before you were having problems and see if you've done something or changed something before the freeze ups started.
Good Luck

Now that you mention it, I'm not sure of wath I am about to say, but between the so fresh install and the nvidia drivers installation at least two days have passed, and i guess that between that time the computer never freezed... But in general i had the problem almost since the beginning, just it never annoyed me so much as it was annoying me now because i was slowly migrating from my old linux distro. But as i said before, the boot parameters fixed it.

---

