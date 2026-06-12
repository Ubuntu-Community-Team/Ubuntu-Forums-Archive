---
title: "[SOLVED] Does wine slow down ubuntu?"
date: 2008-01-15
forum: Wine
---

### Post by linksolo74 on 2008-01-15
If i install wine will it slow down ubuntu? I'm dual booting right now so i don't have to have it, but it would be kind of nice. Yet i don't want to slow down ubuntu, cause i love how quick it is. and does wine make linux have a lot of problems that windows have? Thanks

---

### Post by hikaricore on 2008-01-15
WINE does not "slow down" Linux persay, however if you're running several applications under WINE which will take up processing power and ram, the system could slow low at this time.
It will not be a permenant thing and on most systems you have to be running some heavy applications for it to become an issue.

WINE will not cause your system to have any ***dows like problems such as risk of virus/hijacker infections.
However in the most recent version of WINE, applications that have options to start when the system starts may cause this behavior when a WINE session is loaded.

Other than that, you shouldn't have any troubles.

Bear in mind that not all software runs properly under WINE and you should not expect it to.
WINE still is and has long been Beta software, but it's getting better all the time.

Be sure to check the [WINE Application Database]("http://appdb.winehq.org") to see what software runs under WINE and for installation/troubleshooting tips.

---

### Post by linksolo74 on 2008-01-15
Well i also heard that it doesn't work to well with ATI cards (which is what i have), is this true?

---

### Post by CCNA_student on 2008-01-15
Wine works fine on my ATI X300.

---

### Post by aoanla on 2008-01-16
The "issue" with ATI cards is more that *some versions* of the ATI proprietary driver appear to have issues with *some versions* of Wine, on *some cards*.

I could never get my X1950 working with the then-current ATI drivers with the then-current Wine, but it worked quite well with certain older releases of Wine. Conversely, I know that some people found that the newest ATI release has improved their experience, and some people have found that they've always been okay. 

So, it's a difficult question to answer, really. I'd imagine that things will only get better, though...

---

### Post by favadi on 2008-01-16
Wine is very good app for windows. But cedega is the best choice for gaming...

---

### Post by linksolo74 on 2008-01-16
isn't cedega just a edited version of wine? and don't you have to pay a subscription for it? 
[I][B]

[I]The "issue" with ATI cards is more that some versions of the ATI proprietary driver appear to have issues with some versions of Wine, on some cards.

I could never get my X1950 working with the then-current ATI drivers with the then-current Wine, but it worked quite well with certain older releases of Wine. Conversely, I know that some people found that the newest ATI release has improved their experience, and some people have found that they've always been okay.

So, it's a difficult question to answer, really. I'd imagine that things will only get better, though...
__________________[/I][/B][/I]

 thanks for the info on ATI, and do you know if this applies to a radeon 9600?

---

### Post by Whiffle on 2008-01-16
Cedega is hit and miss.  So is wine.  The best bet is to do some google research on what you're trying to run to see how it behaves in wine.  Some apps work great, some not so much.  I have a friend who had a Cedega subscription and cancelled it because for his games it wasn't much better than plain old wine.  

It won't slow down your computer though, it only runs when you're running a windows program.

---

### Post by hikaricore on 2008-01-16
> **favadi said:**
> Wine is very good app for windows. But cedega is the best choice for gaming...

**....NO**

---

### Post by morganpatrick on 2009-07-13
Does your computer take a performance hit only when wine is running? I have vmware but I would like to run a couple things in wine just so i don't have to boot all the way into vmware all the time. Supposing your computer does slow down from wine, this would presumably only be when it's running, right?

---

### Post by Bios Element on 2009-07-13
> **morganpatrick said:**
> Does your computer take a performance hit only when wine is running? I have vmware but I would like to run a couple things in wine just so i don't have to boot all the way into vmware all the time. Supposing your computer does slow down from wine, this would presumably only be when it's running, right?

Yes, As was said a few times. Wine is a program, Just like everything else.

---

### Post by morganpatrick on 2009-07-14
I know, sounds like a dumb/redundant question. What I was asking was whether simply having it installed slows down the system. Like, if there are sevices or dependancies that start up when ubuntu starts, when wine is installed, to make it function when a windows program is executed, or whether it simply starts the layer when an executable is started, and shuts itself down afterwards.

---

### Post by diggedy on 2009-07-14
> **morganpatrick said:**
> Does your computer take a performance hit only when wine is running? I have vmware but I would like to run a couple things in wine just so i don't have to boot all the way into vmware all the time. Supposing your computer does slow down from wine, this would presumably only be when it's running, right?

correct and it only acts like any other program, it uses resources as does the programs running within it. As far as im aware it does not run in the background unless you start a program up which requires it (a windows based program) and it closes when you close the windows program. I play games using wine and I have no issues other than the compatibility ones.

in a very late response to one of the other posts, I wouldnt consider cedega. playonlinux works well as does wine on its own and both are free. Cedega is 45 quid for a year and imo has no improvements over wine other than the GUI but then you have playonlinux for that. If your gonna pay 45 quid a year you might as well buy windows and run dual boot

---

