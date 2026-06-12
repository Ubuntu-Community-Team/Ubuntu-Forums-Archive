---
title: "So how's about some help with this CraZZy yaboot ."
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by OMG.teh.Interweb on 2006-02-22
Hay Guyz,

I've just installed Ubuntu 5.10 on my Mac Mini.  'tis one of the best distros I've used and it runs DAMN well on my mac.  Installation was a breeze!

Now here comes the problem, or not really a problem, just an annoyance.

I have a cheap dell monitor that seems to take years to warm up and by the time i get a display, yaboot has done it's thing and selected the defult os, meaning if i want to boot OSX i need to make a preemptive strike and that's a pain.

So guyz, how do I remove the timer from yaboot and make it wait for me?  I'd like to keep the menu until i make a decision.

This may have been addressed before and if it has, i apologise, i searched and could not find.

---

### Post by DrFunkenstein on 2006-02-22
I'm not on my ppc machine right now, so take this with a grain of salt.

I think there's a timeout option in /etc/yaboot.conf. Simply setting this to a higher number should fix your problem.

After you have done this make sure to run ybin as root. IIRC this is needed for the new settings to take effect.

Hope this helps.

---

### Post by penguain on 2006-02-22
i can answer this more exactly
```
sudo nano /etc/yaboot.conf
```
change timeout=50 to something else like timeout=100 or such...
then save then
```
sudo ybin
```

---

### Post by OMG.teh.Interweb on 2006-02-22
Yep, That bout does it, thank you both.

One comment, when changing the timeout value i found out that it is measured in 1/10 of a second, not seconds.  That makes a bit of a difference.  I was hoping there was an infinite value but i guess that's just life.  Thanks again

---

### Post by linear on 2006-02-22
[quote=OMG.teh.Interweb]I was hoping there was an infinite value but i guess that's just life.[/quote]
What happens if you remove the "timeout=" line from yaboot.conf?

---

### Post by OMG.teh.Interweb on 2006-02-22
[QUOTE=linear]What happens if you remove the "timeout=" line from yaboot.conf?[/QUOTE]

Damn, that's logical....... so logical it just might not work.. hmmm:-k 

I will be sure to try that asap.

---

### Post by ssam on 2006-02-23
lots of places in linux use a timeout value of zero to indicate waiting forever.

if you think the measureing time in tenths os seconds is crazy then you should see how hdparm takes vales for its disk spindown time. have read of man hdparm the paragraph about -S :-)

---

### Post by Ptero-4 on 2006-02-23
set the timeout to 0 in /etc/crapboot.conf (err. I mean /etc/yaboot.conf)

---

### Post by OMG.teh.Interweb on 2006-02-25
[QUOTE=Ptero-4]set the timeout to 0 in /etc/crapboot.conf (err. I mean /etc/yaboot.conf)[/QUOTE]

Being used to GRUB and LILO zero was the first value i tried.  With a value of zero it displays the menu for zero seconds.... *high five for being literal yaboot*  I guess i'll just have to use a really high number, works fine for me.  Thanks everyone for the help!

---

