---
title: "DNSMasq and College Domains, More than 3 NS in resolv.conf?"
date: 2007-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by ilikenwf on 2007-12-06
I have been using dnsmasq, and it works great with OpenDNS, but I can't have more than 3 nameservers, so I can't use my college's nameservers. This prevents me from accessing the school's webmail, my student portal, or the school's website, as they are served off of the local domain within the network. 

I disable opendns, and I can access them after rebooting, but dnsmasq doesn't work (yes, I have it setup correctly, with 127.0.0.1 being on the top of resolv.conf, alongside the school's ip addys, the prepend domain thing is setup, as is opendns's listen address).

I would like to be able to use more than three domains in resolv.conf, and would like to have my computer actually look at 127.0.0.1 as a DNS server first. Even though it is at the top of the list, it isn't caching, or pulling for teh cache, or something like that...

Help?

---

