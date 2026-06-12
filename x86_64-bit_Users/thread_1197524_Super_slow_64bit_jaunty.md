---
title: "Super slow 64bit jaunty"
date: 2009-06-26
forum: x86 64-bit Users
---

### Post by msvalente24 on 2009-06-26
Hi Guys

I just recently upgraded to juanty 64 bit, here are my system specs

core 2 duo
2gb ram
intel video card
dell d630
uxa enabled
compiz enabled
updates - 100% up to date - including the intel driver update

My machine would fly on previous versions of ubuntu, i could have virtual machines running with several apps simultaneaously running. However now when ever my system reaches 1gb ram usage (50%) it starts to slow down to an unusable state and eventually freezes causing me to hard reboot. The worst is when I run a wine app, just one wine app and the ram shoots to 60% causing my pc to freeze. Im sure 2gb of ram is generous and should be able to handle all of this and i cant understand this sudden unexpected behaviour.

I have crawled google and couldn't find much of use to my situation

Is there any setting or configurations that I have gotten wrong, as in previous versions I never saw my machine freeze once, it was extremely efficient and fast. :(

I understand the recent blacklisting of the intel video card but i recently installed the update for it, could this be the reason or has the recent update addressed the blacklisting situation??

Thanks in advance for your assistance

---

### Post by Th3_uN1Qu3 on 2009-06-26
First try disabling Compiz as it can be a lot of trouble.

---

### Post by markharding557 on 2009-06-27
you may be better off reistalling intrepid and then upgrading to jaunty but retain intrepids kernel to boot from

---

### Post by msvalente24 on 2009-06-29
Thanks, I thought tho that clean installes are always better. Is this not the case with jaunty

---

### Post by markharding557 on 2009-07-06
> **msvalente24 said:**
> Thanks, I thought tho that clean installes are always better. Is this not the case with jaunty

it is normally but in this case the idea was to see if the problem happens using intrepids older kernel which can only be done via upgrading to jaunty

---

### Post by msvalente24 on 2009-07-06
just recently installed the kernal updates over the weekend and the problem seems to have been fixed. So it was probably the kernal as you said. Thank you for you assistance.

---

