---
title: "building my first 64"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Guns90 on 2006-08-28
Hi guys,  I'm trying to decide on components for my first home built 64.  I've decided on the Athlon 64 X2  4200.  What I've read on it is that it has a pretty bad heat sink.  I'd like some recommendations as to what would you do to keep it cool?

---

### Post by helmet on 2006-08-28
are you talking AM2? i have a 3800+ X2 overclocked to 4200 speeds and it's fine. it's only 89W...you can get the EE version which is 65W i think

---

### Post by Guns90 on 2006-08-28
Maybe I should explain myself a little better.  Like I said, this is going to be my first build.  All of the knowledge that I have I have from reading various articles like from epinions, Tom's Hardware, and Newegg customer reviews.  Maybe I'm relying on the customer comments too much (Maybe they're just a bunch of gaming fanatics doing every possible thing to their machines to get speed out of it), but a lot of them complain about the heatsinks on the AM2.

---

### Post by dbenhur on 2006-08-28
> **Guns90 said:**
> All of the knowledge that I have I have from reading various articles like from epinions, Tom's Hardware, and Newegg customer reviews.  Maybe I'm relying on the customer comments too much (Maybe they're just a bunch of gaming fanatics doing every possible thing to their machines to get speed out of it), but a lot of them complain about the heatsinks on the AM2.

If you're seriously overclocking (> 15-20% rated clock push), you usually want to upgrade the default sink and fan.  I've never encountered a problem with the retail boxed amd coolers when running at rated speed or modest overclock though.

If you're shooting for X2 4200, you could just buy an X2 3800 and overclocking it.  All the 3800s (2.0GHz) easily overclock to 4200 speed (2.2GHz), many will go as high as 2.4-2.5GHz with the stock cooler.

I went with an MSI K8NGM2-FID with X2 3800.  It's been rock solid for three months @ 2.35GHz.  [This Anandtech thread]("http://forums.anandtech.com/messageview.cfm?catid=29&threadid=1803985") was an easy guide for the tweaking.

Of course the processor prices have halved in the last three months and they're switching to Socket AM2, so YMMV.

---

### Post by Guns90 on 2006-08-28
Thanks dbenhur.  To me this was one of those things that makes you scratch your head at first and wonder why AMD would make a product that was deficient out of the box, but then my Chevy died two days after I bought it, so who knows?  That's why I rely on forum people for the straight scoop.  Thanks Again.

---

### Post by mw888 on 2006-08-29
I like the Zalman CNPS9500.

---

### Post by hajk on 2006-08-30
Three heat issues: (1) the processor; (2) the Northbridge chipset; and (3) the case itself.

As to the processor, I found that a "boxed set" from AMD (Opteron, see my
sig) complete with high-quality fan works OK: fan almost silent, normally
running at around 1100rpm, processor temperature around 40 degrees Celsius.

As to the Northbridge chipset: it came with its own little 40mm fan, a
cheap affair that became very noisy after a few weeks. I ripped it out 
(two darts, just pull and twist them hard), and replaced it with an
aluminum passive heat sink, a Zalman NB47J is both cheap and effective,
and above all silent. The fins will be hot to the touch, but you won't 
get burned. Do get some high-quality heat paste, though.

An additional 80mm case fan (or two) will also help, but make sure to 
put in a hand-tunable Zalman adjustable resistor in the power cable, 
so as to prevent this fan from running at noisy full speed: around
1000rpm is effective and reasonably silent (your mobo may be able to
control this too). Keeps temperature inside the case about 4 degrees
Celsius above ambient.

Installing these things early in the building process is easiest.

Good luck!

---

### Post by thoffland on 2006-08-31
I have an 4400+ X2 (not overclocked) and I use a Zalman 7700 fan on it. I had to remove the mount off the motherboard (gigabyte gak8n ultra 9 nforce 4), but it was fairly simple once I figured out how. I had a 3200+ in there before that I oc'd and it kept it really cool. Just make sure you have room for the fan.. it's big!! 

Good luck!

---

### Post by eutley on 2006-08-31
can anyone tell me how to determine if a desktop has a 64bit processor with ubuntu?

---

### Post by thoffland on 2006-08-31
> **eutley said:**
> can anyone tell me how to determine if a desktop has a 64bit processor with ubuntu?
In a terminal window type:

cat /proc/cpuinfo

:cool:

---

