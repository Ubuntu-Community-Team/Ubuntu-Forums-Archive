---
title: "Skype is locking up my machine"
date: 2008-09-25
forum: x86 64-bit Users
---

### Post by RFXCasey on 2008-09-25
I started using skype recently. I figured out how to set the sound up and things work pretty good most of the time however sometimes when starting skype or placing a call my machine will freeze solid requiring a hard reset. I had read that some older versions of Skype had lockup problems in other versions or Ubuntu but haven't found anything related to Heron 8.04. It doesn't always happen but skype seems to be the best VOIP chat I have seen for Ubuntu and I would really hate to have to stop using it. Thanks.:confused:

---

### Post by Sef on 2008-09-25
1) what version of skype are you running?

2) what are your system specs?

---

### Post by RFXCasey on 2008-09-26
I'm at work right now but when I get home tonight I will gather that info up and post it.

---

### Post by RFXCasey on 2008-09-30
skype 2.0.0.72
skype common 2.0.0.72
skype gnome 1.3.0.53
Ubuntu 8.04 (hardy)
Gnome 2.22.3
Kernel 2.6.24-21-generic
AMD 64 X2 3800 2Ghz @2.4Ghz 2Gb ram
ASRock 939 Dual Sata 2 Motherboard
Leadtek 6800 TDH 128Meg
Sound Blaster Live 5.1 Platinum
Leadtek TV2000 Pro

Let me know if you need any more information.

---

### Post by Prometheum on 2008-09-30
Skype is non-free software; there's nothing anyone on this forum can do to make it work better on your system, and given its track record on amd64, nothing the skype devs will do either.

I struggled with skype for almost a year before realizing it would never be as stable, secure, and _good_ as the free software alternatives. I use Ekiga now and everything works great.

---

### Post by Crafty Kisses on 2008-09-30
While Skype is on, go in the Terminal and type the following:
```
top
```
Then post the results here.

---

### Post by RFXCasey on 2008-09-30
I'm at work right now so I'll post that info as soon as I get home tonight(tomorrow morning). I think I may want to start using Ekiga, I'll give it a shot. Is it compatible with skype, can you talk between the two?

---

### Post by cam381 on 2008-09-30
Yes it is compatible and comes with ubuntu.

---

### Post by aoanla on 2008-10-01
> **cam381 said:**
> Yes it is compatible and comes with ubuntu.

No, it isn't directly Skype compatible - nothing but Skype can be, as their protocols are all closed and proprietary.

From Ekiga's own faq:

 Which programs don't work with Ekiga ?

Skype, MSN, Google talk

    * Google talk have a "plan to support SIP"... 

    * Ekiga is not compatible with Skype or MSN and will never be as long as their protocol will stay proprietary. We do not think using closed protocols for communications is a good thing. 


Can I connect to a SIP server with Skype?

In short: no.

Skype has a service called "SkypeOut" which allows users to call the public switched telephone network. As Ekiga can do the same using the right provider, Skype and Ekiga users can talk each other, but it will cost.

---

