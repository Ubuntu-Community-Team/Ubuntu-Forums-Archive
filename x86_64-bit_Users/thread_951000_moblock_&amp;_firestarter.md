---
title: "moblock &amp; firestarter"
date: 2008-10-17
forum: x86 64-bit Users
---

### Post by Spanner_Man on 2008-10-17
Some background info on my setup is;
Ubuntu Desktop 8.04 64 bit acting as a sort of fileserver/gateway.
Using (currently) firestarter to share my net connection.

I have some questions about both [moblock]("http://moblock-deb.sourceforge.net/") and firestarter.

If i have moblock setup will moblock also filter any request that my other computers request via my system?

I honestly hope so.
I just would like to ask before i go head and do this. I'm sharing my connection with family

---

### Post by jre on 2008-10-18
**MoBlock on routers:**
Yes, MoBlock also filters the FORWARD iptables chain. There all traffic passes that is routed through your system. Other machines on your network behind your gateway will have their traffic filtered by MoBlock. They will get the pro's (don't need to talk about that) and cons of using MoBlock. So you most probably will have to do the whitelisting of certain ports and/or IPs in the iptables chain moblock_fw, too to  keep your family happy!
Please note that I don't use MoBlock on a router so that I can't test anything related to this topic.

Changes for INPUT (moblock_in) and OUTPUT (moblock_out) traffic only apply to traffic related directly to the machine where MoBlock is installed.

**Moblock and firestarter:**
You have to make sure to restart MoBlock after every change in the firestarter settings. This is necessary because firestarter purges other iptables rules (including those needed by MoBlock) and/or places its iptables rules before MoBlock's rules.
See also the note for firewall users in the man page or at moblock-deb.sf.net.
MoBlock is non-invasive on firestarter's settings.

---

