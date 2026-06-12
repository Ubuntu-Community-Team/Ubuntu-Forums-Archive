---
title: "Death of a 64-bit Ubuntu Machine"
date: 2009-06-21
forum: x86 64-bit Users
---

### Post by wboyd53tx on 2009-06-21
Well, I have to report today the death of a 64-bit Ubuntu Machine. My son-in-law and I built a quad-4 processor machine for my wife and installed Ubuntu on it last December, and she fell in love with Linux. It did everything she wanted, and she found Linux very easy to use. She really liked it.

Now, that having been said, you have to understand my wife is an end-user not a developer. She just wants her computer to do some basic stuff, the most important of all, for her, is the ability to play Runescape online with her machine. Well that worked great, as did everything else.

Until the night before last.

That's when she finally clicked on the "Upgrade Ubuntu" button. Ubuntu upgraded to the latest greatest version, and Runescape would no longer work. I worked on it all night, and the next day had my son-in-law come over and the two of us hashed away at it, installing/reinstalling Java and putint in symbolic links, and following every conceivable possibility. Then we read on a Runescape forum that if you want to play Runescape, DON'T upgrade your Ubuntu. So we reformatted her hard drive and put Hardy back on it, went through the java/symbolic links process described in various places to solve our problem, and after an ENTIRE day, we were not able to get it working.

So in the end, we had to put Windows Vista on the machine.

Now my wife thinks she is stuck with Windows. She doesn't like it. But she has the tools she needs at her finger tips, and can do all the things she likes to do, including playing Runescape. It came down, in the end, to a decision on her part to either play Runescape or have Linux on her machine.

So thus, the death of an Ubuntu Linux Machine.

---

### Post by The-Don on 2009-06-21
That's a shame. I'm new to the Forum/Linux, but from what I understood from the post:
- Latest version (9.04) isn't compatible with this game;
- A previous version does;
- Hopefully the game devs will write a patch to allow the game to play on Jaunty.

How did it work beforehand?

P.S.
An alternative that I'm still playing around with is to run:
```
sudo aptitude install virtualbox
```

That way, the Mrs. can play the game inside of a Vista shell (still fullscreen and acceptable framerates).

---

### Post by CoreyB. on 2009-06-21
Since, from what I understand, RuneScape is just a Java based game in a web browser, I would have done a fresh install of Jaunty then install sun-java6-plugin.  There is no reason (I can think of) that it shouldn't work.

---

### Post by robstel on 2009-06-23
Runescape works for me. AMD Sempron 3000+ (single core), Jaunty 9.04 64-bit, sun-java6-jre and sun-java6-plugin installed via synaptic.

---

### Post by brew1brew on 2009-06-24
> **wboyd53tx said:**
> I built a quad-4 processor machine

does this mean you have 16 cores?:p

---

