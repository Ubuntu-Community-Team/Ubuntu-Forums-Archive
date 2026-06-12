---
title: "Weird Connectivity Problems in 7.04 / 64bit"
date: 2007-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by leemind on 2007-05-08
Hi, quasi-newbie post here, so please bear with me.

I have an 'offsite' machine that used to run 6.06 brilliantly.  I brought it home the other day and I figured whilst I have fast internet connectivity I would update it to the latest and greatest.  I upgraded from 6.06 -> 6.10 -> 7.04 pretty smoothly, all via my network connection.

However, when I had finished the upgrade, I tried to update a few other packages and noticed apt-get and package manager just hung on 'waiting for headers', so I googled from Firefox.  The google query came back with a result but I could not connect to any other websites.  Anyway, I gave up messing around and burned a 7.04 installation disk (from my Mac) and did a complete fresh install.

Same thing -- I can get google's homepage but that is about it.  If I click on any other URL it just sits there "waiting for xyz.com".  I assumed there was some DNS oddity going on (maybe some caching at my router??) but I can traceroute to othersites like [www.bbc.co.uk](www.bbc.co.uk) and ping various sites so DNS must be working.  

I don't think it is the hardware, as it worked just fine under 6.06 and 6.10 (since I did a network upgrade)

(Its worth noting that I can see everything on my Mac which is on the same network)

If nothing at all was working that would be one thing, but how can I get (say) google but nothing else?

Completely stumped of London

any ideas much appreciated

Cheers

David

---

### Post by dfreer on 2007-05-08
check out posts about disabling ipv6. i think you basically:
(1) edit /etc/modprobe.d/aliases comment out the line that has ipv6 in it
(2) add "blacklist ipv6" to /etc/modprobe.d/blacklist
(3) reboot.
That's from memory, I know kilz has a link in his signiture that tells you how to disable ipv6.

---

### Post by leemind on 2007-05-08
Thank you very much for your quick reply.

I thought "darn, that's it" but it didn't fix anything - same problem

HOWEVER, during my search for IPV6 DISABLE I came across this thread:

[http://ubuntuforums.org/showthread.php?t=418144&highlight=disable+ipv6](http://ubuntuforums.org/showthread.php?t=418144&highlight=disable+ipv6)

which then lead me onto this:

[http://articles.techrepublic.com.com/5100-1035_11-6174075.html](http://articles.techrepublic.com.com/5100-1035_11-6174075.html)

and ker'ching! I fixed it from there.  Read the 2nd link for juicy details of WINDOW SIZES and 2.6.17 and greater kernels

Follow the link that someone posted as a follow up for UBUNTU problems and apply the fix.

Happy of London :-)

---

### Post by dfreer on 2007-05-08
nice googling! I've never heard of this problem before, I just thought it was the ipv6 problem most people have been having. glad you got it fixed!

---

