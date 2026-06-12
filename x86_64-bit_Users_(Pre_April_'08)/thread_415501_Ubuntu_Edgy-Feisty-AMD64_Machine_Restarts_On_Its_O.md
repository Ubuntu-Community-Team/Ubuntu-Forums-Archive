---
title: "Ubuntu Edgy-Feisty-AMD64 Machine Restarts On Its Own"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by harshad on 2007-04-20
I have been running Edgy on my AMD Athlon 64 Processor 3000+ for quite some time without any issues. 

However since a couple of days my machine restarts a few times everyday for no apparent reason. It seems like this happens more often in the first few minutes after starting the machine.

I was hoping that upgrading to Feisty Fawn would fix the issue for me but unfortunately that hasn't happened.

I thought of the possibility of my CPU fan not working and so the CPU overheating and restarting. But the CPU fan seems to be working fine.

Also if I am lucky, the machine at times works for many hours without automatically restarting. So I don't think it's an issue related to CPU overheating.

There's one possibility that my UPS isn't working as it should be, but the other Intel+Windows machines running on the same UPS don't have any problems or restarts.

Am at a loss of ideas. Any suggestions are most welcome.

thanks,
harshad

---

### Post by harshad on 2007-07-23
Are there no suggestions that the community can make?

I have changed my RAM, checked my SMPS, Removed the 915resolution tool. Pulled out all cables and placed them again....and yet my ubuntu machine keeps restarting automatically and suddenly at random intervals. Sometimes it restarts multiple times right at startup. Sometimes it restarts 1 hr after it has started.

Which log should I check for errors that might have occurred just before restart?

Have no idea what's going wrong. 

Switching back to Windows unfortunately looks like the only solution available.

---

### Post by rajeev1204 on 2007-07-23
I had  a similar issue and it turned out to be my RAM . Luckily i just had to clean it with silver polish! on the back of the ram ( not the contacts but the metal on the PCB ) 

Try changing ur SMPS since u have already changed ur RAM . And if u have recently purchased a new graphics card , maybe the SMPS cant supply sufficient power to it ..

COuld be anything really .

---

### Post by bigken on 2007-07-23
also check your bios settings ie boot from lan ect

---

### Post by _simon_ on 2007-07-23
I would be suspecting the PSU (power supply unit), got a spare to try?

---

### Post by Cappy on 2007-07-23
I also had this problem before and it was my PSU. Check in your bios to make sure your voltages aren't over and below 10%. So, for instance, your 12V shouldn't be higher than 13.2 or lower than 10.8

Oh, and the reason my PSU voltage went wack and this problem started in the first place was that a stupid fan screw had fallen on my video card. I'm lucky it didn't short it out =P

If you end up needing a new PSU I would go for this one:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139002](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139002)
You can actually buy it $20-$30 cheaper at a place like zipzoomfly or maybe somewhere else.
It's expensive but it's completely silent and it has a 5 year warranty on it. It will last longer than a computer =p

---

### Post by crjackson on 2007-07-23
I too think it's the PSU.  I've built MANY systems and had a few PSU failures.  This is a common symptom of PSU failure.  Other hardware issues can also show the same symptom but the PSU is by far the most likly suspect.

As to a replacement PSU...  It's really hard to make a sound recommendation without knowing ALL you hardware specifics.  There are PSU calculators online that can help you determin your output requirements.  Just be sure to buy a QUALITY unit.

---

### Post by gunnerman on 2007-07-23
It to me as well is a psu issue, I had the same problem a couple years ago with a amd barton core cpu.  My mobo was reporting to me that it was my cpu which had the problem, after I took the system apart I found out one of the rails on my psu litterly burned up and fused to the connector on the board.

---

### Post by rajeev1204 on 2007-07-24
> **gunnerman said:**
> It to me as well is a psu issue, I had the same problem a couple years ago with a amd barton core cpu.  My mobo was reporting to me that it was my cpu which had the problem, after I took the system apart I found out one of the rails on my psu litterly burned up and fused to the connector on the board.


Hmm ya and since he is in india  , most of us ( including me ) go for all the good configurations and ignore the PSU .(SMPS ) 

I had a an ugly cheap one and it fried both my mobo and CPU .

Got a nice brand called Powersafe ( almost 3 times the price) but comes with a 3 year warranty :)      Highly recommended

---

