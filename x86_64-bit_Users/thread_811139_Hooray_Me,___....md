---
title: "Hooray Me,   ...?"
date: 2008-05-28
forum: x86 64-bit Users
---

### Post by yergeht on 2008-05-28
Ok so I just switched over to Ubuntu Hardy Heron and I love it, kinda. I love the fact that it's not microsoft and it looks sleek. I use to have redhat 7... something anyways it was strange and on a laptop and I was young and neive... So I got rid of it and went back to microsoft.  ](*,) <br> When I first went to college(there's been a couple) I was a CS major... and soon realized I'm a concept man... not a numbers guy. I soon switched to Sociology where you find me know. I've been born and breed on MicrZ. Since windows 3.1 and 3.11. :mrgreen: So I know a little bit, but know onto my problem... <br> Oh bty high it's nice to meet all of you on the unbutu formus.. ):P I'm sure we'll come to know each other well

I usually hate simely's but I felt... ehhh

Ok but seriously I'm currently running this on the windows side of my machine.:-( I currently did a clean install of Hardy Heron  on my secondary hard drive. I separated the hard drive (a 160 Gig seagate 7200 RPM IDE) which had 60 gigs left into two partitions one being NTFS and the other being ext3 I installed the OS into the ext3 partition but I failed to make a swap drive. I don't really want to make a swap file but If I have to then fine(tell me how?) but now I can't repartition the drive, it says nevermind I'm in windows. But even in windows it won't let me (XP(home(don't ask) sp2)I used partition magic 8.0 and that what's giving me the error... But I digress the reason this is kindof important is because I've noticed a kind of noticeable slowdown with Ubuntu and that makes me sad. Hold on I'm getting a belarc advisory now. See attachment. Now I'm doing this as a test run bc I want to make sure I can get everything I want working properly Before I make the full switch. And then I'm gong to make my 250 gig sata the master. After I transfer the bulk of music(200+gigs) over to the other partition somehow... I did burn it all back to DVD but I'd like to try something different if possible. (160(2 partitions) around 30 gigs free on each partition) IDE / 200 SATA) HMMMM? Anyways, I've been surfing and photobucket and youtube and alot of other sites, even firefox in general, it seems are running alot slower than they should be. I installed one add one. If I was linux I'd give you the dump of my plugins but It's only one and it's some search thingy, the name eludes me at the moment ... I read about the flash plugin issue and when I reboot I'm going to go do that but in the mean time I've always got another issue with my sound. I've got two sound cards and I'm getting static on the line and rythmbox takes for ever to load. Is it a 64bit app? Again I'd tell you all the settings(not in ubuntu) I'm getting on both outs' they are right next to each other in the sense of the mobo. I'm getting the same static within winamp(windows) but it seems to be aggravated by my wireless mouse(whenever I move it and the like). Any thoughts?

Oh where the hell was I.... Oh yea, full switch, I wanna but can you help me... I don't know if I'm ready yet... I downloaded the cheat sheet and that was pretty helpful... I'm going to read some  more forum stuff and get acquainted some more...

Again any help would be greatly appreciated :biggrin:

---

### Post by tamoneya on 2008-05-28
this should solve your swap problems:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by bford16 on 2008-05-30
You may have trouble making the SATA drive your master; Hardy has a kernel bug <https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209454> which prevents it from recognizing SATA drives properly.  There are a number of possible workarounds; I use "pci=nomsi" in the boot parameters.

---

