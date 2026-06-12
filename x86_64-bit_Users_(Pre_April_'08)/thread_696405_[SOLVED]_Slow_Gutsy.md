---
title: "[SOLVED] Slow Gutsy"
date: 2008-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by A Pragmaticist on 2008-02-14
I recently installed Gutsy, and now my comp runs very slowly.  I have disabled desktop effects in appearances, but it makes no noticeable difference.

I have an HP Pavilion dv6436nr laptop, with 2x AMD Turion 64 x2, Nvidia GeForce Go 6150, running at 1.8 GHz.

At first I just upgraded to Gutsy in 32, and had the same problem.  No one on IRC seemed to be able to help, so I tried installing the Gutsy 64 to see if it would work; someone informed me that flash is not a problem like I thought, so I thought "why not".

Unfortunately, it seems to make no difference, it runs just as slow, whether it is internet applications or regular apps.  When I open a terminal, it takes a a few seconds for my user name to show up.  Firefox usually takes a minute if not two or three to start popping up.  Surfing the net is painfully slow, I suffer from what seems to be a whole lot of lag; as I type, once every few minutes it will take a few seconds for my typing to take effect, not my normal experience in Feisty.  For some reason scrolling seems to be exaggerated now, the scroll button is very sensitive.

I hope someone can help me with this, I have not had any luck for a week now with this problem.

---

### Post by khensucat on 2008-02-14
Just in my personal experience, whenever I've had a problem that included things like scroll-dragging, it was invariably a video-driver problem ;-)

---

### Post by osman s borutecene on 2008-02-14
any cpu eaters like trackerd?

---

### Post by njparton on 2008-02-14
Try uninstalling compiz (completely) and then setting metacity as your default window manager.

---

### Post by firefly76 on 2008-02-14
If you're machine can't resolve localhost properly then you will experience latency while browsing and even when opening applications.  Everything uses the network in Linux...

Could you post the contents of /etc/hosts please?

Do you have an internal network, router?  Provide the IPs if so.

Using DHCP?

What did you name your linux machine?

---

### Post by A Pragmaticist on 2008-02-14
I am not sure if I should have mentioned, but I do have to add "noapic" line to be able to boot up.

Khensucat: I was having these problems before I installed a restricted driver from Nvidia -- the Nvidia accelerated graphics driver (latest cards) --, so I do not think it is the video-driver.  Unless this is not what you were referring to?  Or maybe it simply failed to do what it was supposed to do?

osman s borutecene:  I ran "top", but if anything, it seems as if nothing at all takes up all that much processing.  Trackerd barely does a thing, in fact it is always sleeping.  Sometimes the processor is busy though, but for instance with firefox.  I dont know if it matters, but when it is busy the total percentage of the processor when being used by various programs goes above 100 by a few percentage points; I am guessing it is somewhat inexact though.

njparton: How do I *completely* uninstall compiz?  And could you help me with further instruction on setting up metacity and so forth?  I've never done anything like that before.

Firefly76:

Contents of /etc/hosts:

"127.0.0.1       localhost
127.0.1.1       ubuntu101

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts"

I am wired to a cable modem, although it is also for wireless; not sure if it counts as a router since I have it directly wired; also, how would I find out the IP for it if it were?  Same with internal network, I do not think I have one but if you could tell me where I should find it (since I can't find it) and how to get the IP for it, then I will post it.

I am not sure if I am using dhcp or not, can't seem to find that out either; again, if you could help me with finding it, I will post it.

 I named it ubuntu101

---

### Post by firefly76 on 2008-02-15
> **A Pragmaticist said:**
> 
Contents of /etc/hosts:

"127.0.0.1       localhost
127.0.1.1       ubuntu101



Is that quote actually in the /etc/hosts file or did you typo that?  That will definately give you trouble if it is in there.

---

### Post by firefly76 on 2008-02-15
Actually, you have two problems there.  There should be no quote on the 127.0.0.1 line (if you have one), plus the 127.0.1.1 is not an Ubuntu requirement IIRC.

You should change:

```

"127.0.0.1 localhost
127.0.1.1 ubuntu101
```

to this:

```

127.0.0.1 localhost ubuntu101
#127.0.1.1 ubuntu101
```

You can comment out the 127.0.1.1 line like I've shown or just plain remove it, up to you.  Hopefully you'll have better results.

Restart you networking after BTW...

---

### Post by A Pragmaticist on 2008-02-15
firefly76: Quotes were not there or at the bottom, sorry.  I commented out the 127.0.1.1, and restarted the computer, but it made no difference.

---

### Post by A Pragmaticist on 2008-02-15
I found out something related to networking.  When I disable networking the first time, suddenly everything is fine (except, of course, the internet applications).  Then when I enable it, everything is slow again.  But when I disable it the second time, it makes no difference; everything is still slow.  I tried to enable it and then for the third time disable networking, but it is still slow.  Only when I disable it the first time does everything work fine at good speed; I tried out nautilus and the calculator accessory as test programs, both were fine after the first disable, and both were really slow again after enabling and disabling beyond that.

So maybe it is something to do with the networking?

---

### Post by A Pragmaticist on 2008-02-15
Alright, now I am positive that it is something to do with the networking: the wireless networking.  I disabled wireless, and now everything is great.  Any ideas why the wireless would have been causing my problem?

---

### Post by Yellow Pasque on 2008-02-17
> **A Pragmaticist said:**
> Alright, now I am positive that it is something to do with the networking: the wireless networking.  I disabled wireless, and now everything is great.  Any ideas why the wireless would have been causing my problem?
Maybe the wireless kernel module was a CPU hog?

---

### Post by A Pragmaticist on 2008-02-17
I am not sure that it was a cpu hog, but I suppose I am not sure how to find out whether it was or not.  "Top" does not show anything that consistently hogs the processors or memory.

Anyways, I am going to change this to "Solved" since I at least figured out that its a wireless networking problem, and will just start a new post in Networking and Wireless.

---

