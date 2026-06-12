---
title: "Firefox 1.5.0.4 DNS Lookups"
date: 2006-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Beamerboy on 2006-06-26
This is not a serious problem but it is very annoying.  Whenever I visit any webpage in firefox 1.5.0.4 it does DNS lookups for every page and any dynamic links within a page (for images etc).

For example, when I refresh the Ubuntu Forums page firefox first spends upto 17 seconds (longest time so far) doing:

Looking up [www.ubuntuforums.org](www.ubuntuforums.org)

Then starts to load the page, then stops halfway through to lookup some google address (dunno what is linked to google on the ubu forum but something must be).  All in all it can take upto 35 seconds to just refresh the forum page.

This hapens with every single site, or pages within a site I am already on.  It is incredibly annoying and adds some really quite heavy latency to browsing the web.

I thought it was just me, something funky and not configured correctly, but I was talking about it in the ubu irc channel and it seems I am not the only person who has noticed this.

Any ideas?

Thanks

BeamerBoy

---

### Post by 11hjpphty76lkjj on 2006-06-26
I have the same problem, also on a 64 bit box.

I've tried disabling the ipv6 setting, as well as installing fosterfox (just for the heck of it) to no avail.

Aaron

---

### Post by Beamerboy on 2006-06-26
OK a big thanks vinicius on the Ubuntu irc channel for the solution to this as follows:

type "about:config" as the URL
right click anywhere on the page that loads and select new>integer

add the following name: network.dnsCacheEntries
click OK
in the next dialog add a value (apparantly 20 is the default, I used 50)
Click OK

This worked for me, so hopefully it will for others too.

BeamerBoy

---

### Post by 11hjpphty76lkjj on 2006-06-26
This seems to have done the trick for me as well.

Thanks for following up on this BeamerBoy.

A

---

