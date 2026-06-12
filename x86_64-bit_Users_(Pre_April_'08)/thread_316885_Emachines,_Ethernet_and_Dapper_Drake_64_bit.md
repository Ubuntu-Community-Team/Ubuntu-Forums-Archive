---
title: "Emachines, Ethernet and Dapper Drake 64 bit"
date: 2006-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by thepaul on 2006-12-11
Hello All

I've installed 6.06 on my laptop and a 1 gig xp machines without an difficulties.  All the hardware was found on both machines and it works great.

However I have a 64bit emachine in which Ubuntu is not able to connect to the Internet.  This machines connects through the Ethernet card through a router.  I know the router is not the problem since the other desktop can connect through the ethernet card, and my laptop connects wirelessly.

Everything else works but I'm not sure why the new machine cannot connect.

Any and all suggestions will be appreciated.

thanks in advance

---

### Post by goatflyer on 2006-12-11
Does the ethernet card show up when you do

```

ifconfig eth0

```

If so, then try
```

ping -c5 72.14.203.104

```
(its google.com) see if there's any response.

If so, then try
```

ping -c5 [www.google.com](www.google.com)

```

If neither works you have a routing problem, perhaps your router doesn't advertise itself as a gateway?  Try pinging your router's address if you know it.

If the first works but the second doesn't you have a DNS problem.
```

cat /etc/resolv.conf

```
should show where ubuntu looks when translating names to IP addresses.

If both work, try
```

wget www.google.com
cat index.html

```

If that works, but firefox doesn't, then you have a firefox setup problem...


EDIT: added one more thing

If you have a DSL connection you might have to run

sudo pppoeconf

to configure your ISP account's user id/password.


As you may guess by reading this post, its hard for anyone to diagnose every possible network problem from one post.  The more info you give, the better...

---

