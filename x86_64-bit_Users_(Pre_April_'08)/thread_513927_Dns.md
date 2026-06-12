---
title: "Dns"
date: 2007-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by art_erickson on 2007-07-31
I have been playing with 7.10 for AMD64 and am having a wonderful time.  I read about OpenDNS and made the changes to effect it.

I modified the /etc/dhcp3/dhclient.conf file to prepend the IP addresses and to remove the nameservers from the dhcp request.  Here's the result:

prepend domain-name-servers 208.67.222.222,208.67.220.220;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name;

It appears to work in that the OpenDNS addresses appear in the /etc/resolv.conf file.   My problem is the ISP addresses appear as well.  Here is the contents of said file:

art@art-desktop:~$ cat /etc/resolv.conf
search tampabay.rr.com
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 65.32.5.74
nameserver 65.32.5.75

So I thot I'd try to determine which DNS server was being used.  Since I'm fairly weak with networks I was hoping a simple command like netstat would work - not even a good guess. I tried ifconfig but it doesn't show the DNS address.  So I tried a traceroute.  That seemed promising except I didn't see any (of the four) DNS addresses in the list.

Does traceroute only kick in after the name resolution?

Is there a better command to determine which DNS server is being accessed?

Is there a way to force the ISP dhcp process from giving me their DNS server addresses?

Will mighty Underdog save the day?

I'll stay tuned.

---

### Post by kuja on 2007-07-31
try using dig.

---

### Post by art_erickson on 2007-07-31
Cool beans - that appears to indicate the DNS server used is the first one in the list at resolv.conf.

Much thanks.  I don't know why the ISP can still make entries but I don't know that I care much.


Would this be the proper place to point out "experiences" I may have with 7.10 that may be of interest to the developers?

---

### Post by puppy on 2007-07-31
Err , why would you use OpenDNS????

Unless you are physically located close to one of their servers (i.e. few hops) the time it takes for you to get to them, rather than your ISPs DNS servers will far outweigh any benefit that you get from their (apparently) large on-site physical cache. And rather than get a 404 error if a website isn't available you get an ad page with dating sites etc etc on it. What's 'open' about that...?

Just another company trying to monetise something that should be *free* - on the basis of their business model I think opensource users should avoid them like the plague on principle

---

### Post by art_erickson on 2007-07-31
I dunno, like I said - I'm pretty weak on networks.  It just seemed like a good idea at the time.

I made the decision some time ago, I don't really remember the reasoning.

I'm not fanatical about anything.  If someone can make money selling ads then so be it.  That's why I have rabbit ears for television reception instead of renting cable.

I would certainly like to hear more viewpoints about the pros and cons of OpenDNS.  Personal/technical experience would be preferred over just sentiments.

---

### Post by kuja on 2007-07-31
Pros:
* Attempts to be smart and correct or offer suggestions about mistyped urls (I'm not sure if it corrects or offers suggestions, but I'm pretty sure it's one of them), so lets say you type in [www.ubbntu.com](www.ubbntu.com), it might try to suggest [www.ubuntu.com](www.ubuntu.com).

Cons:
* DNS server may be farther away and/or slower
* It's suggestions/corrections might be completely irrelevant to what you're looking for

---

### Post by art_erickson on 2007-07-31
Arrrr kuja, to be sure, the points you make be right as rain (ok, that's the end of the pirate stuff - I'm not good enuf at it).

I did wait to see if there was a significant slowdown, I didn't notice any (there may be some, but milliseconds are just milliseconds).  Since I use bookmarks (typing R not me) I don't have to worry about getting error screens very often.

My perspective is a little different than yours.  I think I am (perhaps) helping someone with an alternative to the established forces.  It is a minor thing, not worth differentiating.  It was a good exercise for me to learn more about the Big U.

---

