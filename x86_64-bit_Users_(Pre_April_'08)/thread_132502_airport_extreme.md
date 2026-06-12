---
title: "airport extreme"
date: 2006-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by erimar77 on 2006-02-18
i've almost got the airport extreme working.  i can iwlist "eth1 scan" and it shows the list of access points in the area.  i've tried everything i can think of... edited resolv.conf, staticly assigned IP's, tried to use dhclient... 

any other ideas?

---

### Post by erimar77 on 2006-02-18
ok, i think i got it, i'm posting this from my mac!

```

iwconfig eth1 channel 6
iwconfig eth1 rate 11MB
iwconfig eth1 essid wlan01

```

that's what i did to finally make it work.  to anyone that attempts this.. keep on trucking... read, read, re-read, re-re-read all the threads on the airport extreme and it will work.

---

### Post by erimar77 on 2006-02-18
oh, what sucks is... this is the live cd!!!  

:( its all gone when i reboot :(

---

### Post by aimislame15 on 2006-02-18
So you're saying you got your Airport Extreme to work with Linux? If so, can you please be more detailed about how you did it? Thanks, Eric

---

### Post by erimar77 on 2006-02-18
yeah, when i get a chance, i'll write some stuff down.... 

the connection seems to die after about 15 minutes, so i'll have to look into why it's doing that

---

### Post by erimar77 on 2006-02-18
hmm.. it won't seem to let me delete these

---

### Post by kyle_soule on 2006-02-22
I just wanted to thank you for posting your solution. I was in the same boat and it worked for me, too! AWESOME :)

---

### Post by spaceballl on 2006-02-24
Congrats on getting it working. I got it up and running a couple weeks ago. I thought it was great, but unfortunately still not completely stable or reliable. I'm on the mailing list for bcm43xx driver development and they're working on these things daily so I would venture that while Dapper won't have out of box support for AE, I really think the next version will...

---

### Post by erimar77 on 2006-02-25
i'll have to agree with you on that...  it's nowhere near stable ..  i can't get it to work right on the lastest dapper release.. i'm still using a daily cd from earlier in february.

---

### Post by erimar77 on 2006-02-28
sorry guys... my powerbook seems to have died this weekend :(

i just ordered a replacement dell laptop.. i know it's a dell.. but work is buying it and i can't run ubuntu on the new macbook yet.. so it looks like a fully supported linux laptop for me!

---

### Post by tomislavmedak on 2006-02-28
when i recently installed the dapper over breezy on my ibook g4 12", i've tried couple of instructions in ubuntu and gentoo forums, but found this one on bcm43xx list pretty straight forward for debian/ubuntu users:

[http://bcm43xx.spugna.org/index.php?topic=13.0](http://bcm43xx.spugna.org/index.php?topic=13.0)

---

### Post by charlesboesel on 2006-03-01
Did these instructions work?

Running Breezy on a 12" Powerbook 1.33 GHz G4, 768 MB RAM 60 GB HD
:confused:

---

### Post by refdoc on 2006-03-01
I am using AE wireless now for ther last two weeks or so without any crashes, clashes or freezes. Since one week on WEP.  WEP took me a while to figure out, but more dt my lack of understanding.

---

### Post by tomislavmedak on 2006-03-01
i had problems downloading softmac source that would compile properly with the links i found on ubuntu and gentoo forums.

so, i tried that solution and it worked like a charm. my airport extreme is working pretty stable. at times i have to reboot to get a lock on when i change the APs. though i haven't tried encryption yet.

---

### Post by Paranoid Randroid on 2006-03-02
Is there any possibility of the Broadcom driver being available for Dapper?  I'm not too keen on the idea of Kernel recompilation ...

---

### Post by erimar77 on 2006-03-02
you don't need to recompile the kernel.. the foundation of what you need is already in the current dapper releases...  you just need some "help" using some of the other threads in this ppc forum

---

### Post by aimislame15 on 2006-03-10
[QUOTE=erimar77]you don't need to recompile the kernel.. the foundation of what you need is already in the current dapper releases...  you just need some "help" using some of the other threads in this ppc forum[/QUOTE]

OK, this is pissing me off, after many hours working with it to get it working on Dapper, I can't, can you please explain what I need to do to get my Airport Extreme working with the latest release of Dapper Flight 4? Thanks, Eric

P.S. I've read, and re-read every thread to no avail. PLEASE HELP!

---

