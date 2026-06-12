---
title: "I thought I wasn't supposed to have 3-d capability yet"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by Torqumada286 on 2008-12-06
With my Radeon 4870?  I thought the official ATI drivers hadn't got that capability yet?  I spent a few hours last night playing City of Heroes with no problems.  I even stressed the system by going to several zombie invasions.  I'm not complaining, just curious.

Torqumada

---

### Post by soxs on 2008-12-06
I have radeon 4870 aswell and it works almost fine with fglrx driver. (except video playback, especially HD videos are ugly and unwathcabel( :-/
Which one are you using?

Post the outpur from ```
glxinfo|grep direct
```

---

### Post by jocko on 2008-12-06
> **Torqumada286 said:**
> With my Radeon 4870?  I thought the official ATI drivers hadn't got that capability yet?  I spent a few hours last night playing City of Heroes with no problems.  I even stressed the system by going to several zombie invasions.  I'm not complaining, just curious.

Torqumada

Where (or rather when?) did you get that information? According to [ati's release notes]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html#173867") the 4800 series was officially supported in catalyst 8.7 (released in Juli), and in [this article at phoronix]("http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4870&num=1") they tested the then brand new radeon 4850 and 4870 cards with catalyst 8.6... so even if the release notes for catalyst 8.6 did not mention it, the driver supported cards that weren't even released yet when the driver was released...

---

### Post by Npl on 2008-12-06
> **Torqumada286 said:**
> With my Radeon 4870?  I thought the official ATI drivers hadn't got that capability yet?  I spent a few hours last night playing City of Heroes with no problems.  I even stressed the system by going to several zombie invasions.  I'm not complaining, just curious.

TorqumadaThere are ATIs binary drivers which support all Radeons (newer than R300) soon after (or even before) the cards release nowadays.

What you probably heard about is the opensource-drivers (there are 2 of them) which only provide 2D for many Cards.

---

### Post by Torqumada286 on 2008-12-06
> **jocko said:**
> Where (or rather when?) did you get that information? According to [ati's release notes]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html#173867") the 4800 series was officially supported in catalyst 8.7 (released in Juli), and in [this article at phoronix]("http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4870&num=1") they tested the then brand new radeon 4850 and 4870 cards with catalyst 8.6... so even if the release notes for catalyst 8.6 did not mention it, the driver supported cards that weren't even released yet when the driver was released...

That's the article I remember reading months ago when I got the card.

> **Npl said:**
> There are ATIs binary drivers which support all Radeons (newer than R300) soon after (or even before) the cards release nowadays.

What you probably heard about is the opensource-drivers (there are 2 of them) which only provide 2D for many Cards.

I may be confusing the two.  I kept having problems under Heron, but they work fine under Ibex.

Torqumada

---

### Post by Torqumada286 on 2008-12-06
> **soxs said:**
> I have radeon 4870 aswell and it works almost fine with fglrx driver. (except video playback, especially HD videos are ugly and unwathcabel( :-/
Which one are you using?

Post the outpur from ```
glxinfo|grep direct
```

> 
direct rendering: Yes


Torqumada

---

### Post by soxs on 2008-12-07
This says you have working 3D acceleration (aka direct rendering throug your gpu)

---

