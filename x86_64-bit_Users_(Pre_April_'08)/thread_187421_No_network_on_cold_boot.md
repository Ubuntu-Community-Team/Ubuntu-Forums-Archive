---
title: "No network on cold boot"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by glowplug on 2006-06-02
Symptoms:

Cold boot: 
 * no eth0 IP address.
 * deactivate/activate brings up eth0 address but no connection to router.
 
Warm boot:
 * Normal network/internet activation.
 
This only happens on home connection and only after installing ubuntu while on work connection.

The previous few times (being new to linux) I reinstalled while on home connection and all was fine...
...cold boot fully activates on either home or work connections/networks.

Home connection - netcom router.
Work connection - non-domain network hosted by win2003 server through switch.

I had to reinstall for first time in months due to a silly mistake I made a few days ago.
At the time I could only get onto the work connection.

It seems a bit drastic to reinstall (while on home connection) just to solve this problem.

I've tried searching google and here but I'm probably using the wrong words.
Either that or I haven't recognised any leads to a solution.

I've upgraded from Breezy 64 to Dapper (while on home connection) since but no change.

Thanks in advance for any help/suggestions

---

### Post by Patsoe on 2006-06-03
Very curious stuff, I don't have any idea how a cold boot would be different from a warm boot for this... 

An idea might be to check out [https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager) - which should bring up connections on the fly...

Ofcourse it wouldn't answer the question what is going wrong right now - I'm very curious about that!

Btw, there's very few things that need something as drastic as a reinstall to fix them.

---

### Post by glowplug on 2006-06-03
Thanks Patsoe - that should be enough to get me going in the right direction and track it down.

I would have liked to have repaired instead of reinstalling this last time.
I meant to type rm ./* but didn't press . hard enough or check before pressing Enter.
Was cleaning out old web site files in a /var sub directory - fortunately I didn't use the directory switch.

I have /var on it's own partition so I'm curious as to which files would have been deleted that corrupted the system. 

I tried an undelete tool but couldn't make sense of the results so just reinstalled.

---

