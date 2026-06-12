---
title: "Can't print with AMD64 6.06"
date: 2006-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ceenvee703 on 2006-10-03
I'd installed 6.06 before on a 32-bit AMD system, and was able to print to my HP Color Laserjet 1500 through a JetDirect Ethernet print server.

Now I'm using the AMD64 version on a new AMD x2 machine and cannot print. I can set up the printer, print jobs are processed but the printer never prints. Test pages don't print either.

I got the web-based CUPS interface working and turned on "save debugging information for troubleshooting." I see many of these messages

```
cupsdAuthorize: No authentication data provided.
```

Also, before I turned on the debugging info, I had many of these:

```
cupsdAuthorize: Local authentication certificate not found!
```

Searching for these messages on Google and here didn't turn up much. Any ideas? Thanks.

---

### Post by kuja on 2006-10-03
As far as I know, Printers are HARD to set up in Linux in general :( 
It's saying that no authentication data is provided... It's talking about a username + password. Does this printer server require these?(I'm thinking not) As per things, I would look into a way of either passing it what it wants (less likely) or telling cups that authentication is not required (plausible).

---

