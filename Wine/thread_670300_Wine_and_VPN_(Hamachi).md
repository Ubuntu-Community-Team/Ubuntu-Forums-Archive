---
title: "Wine and VPN (Hamachi)"
date: 2008-01-17
forum: Wine
---

### Post by Noem on 2008-01-17
Alright, not very active on this forum... and I just went back to Ubuntu from another Linux Distribution. So, sorry if posting something that has already been spoken of. 

Anyway, I have a problem, well... don't know if it's a problem yet.

I used to play a game through Wine, Nox. And it has a multiplayer feature which works like a charm, online. And it sure works over LAN too. But then I want to play over a VPN (LAN over Internet) with some friends of mine. The problem is, when going into LAN option in my game I can't find hosts of anyone in my VPN.

The VPN application I use is Hamachi and it's the native linux version. Hamachi uses "ham0" -device for internet connection. My suspects tells me that Wine uses the "eth0" -device. And there you have my problem.

Is there any chance that I can use "ham0" for Wine instead (if this is the problem)?

---

### Post by SBFC on 2008-01-18
Are you sure you ran all the necessary commands? The commandline linux version requires you to join a network and then sign on to that network. I don't remember the commands exactly, I'd have to check.

I did successfully use the Hamachi Linux client to play Warcraft III: The Frozen Throne with my friends who ran Windows.

---

### Post by misse- on 2008-03-14
> **SBFC said:**
> Are you sure you ran all the necessary commands? The commandline linux version requires you to join a network and then sign on to that network. I don't remember the commands exactly, I'd have to check.

I did successfully use the Hamachi Linux client to play Warcraft III: The Frozen Throne with my friends who ran Windows.

How did you do that?

I'm online in a hamachi room, I can ping others and they can ping me. But I can't find any lan games at  all. And when I create, they can't find me. It works if I boot up a windows machine, starts wc3 tft lan game in observer mode. Then the others can find the game and connect, and since it's on the same LAN as my ubuntu, it works there..

But not with Hamachi. Any suggestions?

---

### Post by SBFC on 2008-03-14
Unfortunately I have no suggestions at this time. When I tried it things just worked, there was no tweaking involved. This was quite a few wine versions ago, however. Perhaps some of the newer changes have affected the functionality.

I'd test it out again for you but sadly the latest wine releases (I think the last five or six) have rendered my Warcraft III install useless and it's the only game we play over hamachi.

---

### Post by SBFC on 2008-03-31
I got Warcraft III working again (hadn't recreated my .wine dir in while apparently) and it works with the Linux Hamachi client without any tinkering.

I'm not sure what it doesn't like about your setup.

---

### Post by ziwerliz on 2009-01-20
Can you say which version of hamachi you are using? i have had a problems whit hamachi 1.0.2.5 in windows but 1.0.1.5 works fine.

---

### Post by skipi-gz on 2010-06-12
sorry for late post. i remember i had to set my hamachi connection as my primary connection on windows when i tried to play warcraft 3 or any other game. isnt there a way to do this on wine or ubuntu?

---

