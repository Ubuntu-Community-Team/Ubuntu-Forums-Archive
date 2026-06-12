---
title: "iBook switching off mysteriously..."
date: 2005-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rxke on 2005-11-04
This is a weird one, just asking around if anyone has had this behavour too...

I have been running Hoary for quite a while, no problems at all, then a bit before the official release did an apt-get upgrade to Breezy, which went smoothly.

Then, about a week ago, i finally decided to nuke my harddrive to get rid of the OSX partition and do a clean install. Worked a breeze (lame pun intended)

However...

Something weird started to happen: my iBook would just shut down, or rather switch off, once or twice a day. Just... Switch off, like the battery got yanked or something like that. Quite unnerving, but so far without any bad effect when starting up again... 
My iBook runs days on end, normally, I never or very rarely reboot, just closing the lid to put it to sleep.... I'm not a power-user, mainly surfing and writing stuff, no multimedia whatsoever etc... Oh, and using it as an accesspoint for my desktop computer for net access.  There were never problems, so I don't think it's hardware related, but won't rule that out, 'cause my machine is a rather olde cluncker ;)

I think 9 out of ten 'switch-offs' were during 'menu-related' things: changing preferences, etc, esp. while adding/tweaking stuff in the panel. I really suspected it had something to do with that, for I never had added stuff on the panel before.

And... Now, the last 2-3 days it isn't shutting off anymore. Good, but weird... Like it took the olde iBook some time to 'settle'

So, my -rambling- question: anyone familiar with this?

---

### Post by mert on 2005-11-06
I wonder...Could it be your logic board battery?  I had an old mac (a 6100, I think, shaped like a pizza box)  that started to act very erratically  finally I tracked it down to a fading battery on the main board.

Another possibility - could it be overheating?  I had ubuntu on my powerbook for some time and it seemed to run hotter than OS X.  (had to reinstall OS X and reformat the HD.  Now I'm missing my linux so I'm downloading ubuntu 5.10)

Well, if the problem comes back, post a message and I'm sure someone here will help you out.
cheers
mert

---

### Post by Rxke on 2005-11-06
Thanks for the ideas
As far as I remember, tthe first gen iBook doesn't have a logic-board battery. I once completely dismantled it, to check out what's wrong with my video (turned out the video-chip itself is half-knackered) and I think I did not see backup-battery... Good point, though.
Heat: improbable, it was not running very hot at those instances...

Anyway, the problem fixed itself... Dang those intraceable intermittent problems, heehee... They keep nagging in the back of one's head: "will it happen again? When? Why? How?" :confused: 

Oh, one more: I thought maybe having done ```
sudo hdparm -B 1 /dev/hda

```  (in tandem with laptop-mode and hdparm -S 1 /dev/hda...) which is a quite agressive powermanagement tweak, was the culprit, so I switched to hdparm -B 2 /dev/hda (marginally less agressive) which I thought solved it... But now going back to hdparm -B 1 /dev/hda still doesn't seem to replicate the 'switch-off' behaviour... Uptime 3 days, four hours so far...

---

### Post by geertdeg on 2005-12-12
I have exactly the same problem. iBook G3/300 suddenly switches off. I didn't have this behavior with Gentoo kernel 2.6.14-r2 on the same machine. Could there be something wrong with Ubuntu's current kernel?

---

### Post by Rxke on 2005-12-13
how frequently? Mine seems to do this after around q little of two weeks, initially it was more frquent, had it once three times in several hours..
uptime now 16 days... 'should' happen every moment now...

---

