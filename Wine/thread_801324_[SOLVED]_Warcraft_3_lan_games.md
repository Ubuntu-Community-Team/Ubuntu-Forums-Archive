---
title: "[SOLVED] Warcraft 3 lan games"
date: 2008-05-20
forum: Wine
---

### Post by danwizard208 on 2008-05-20
Hope this is the right forum for this...:p

I recently installed wine and Warcraft 3 on my very new (5 days old) ubuntu system, and finally (after 2-3 days of config issues) got *most* of the issues sorted out except one thing:
Whenever I create a lan game, or my brother on his windows xp computer (we're connected to the same router), we can't see each others games.
Before ubuntu, when i had xp on the same comp, and was connected to the same router, we could play lan without problems.
I used firestarter to port-forward the 6112-6119 range, and my router has Strarcraft enabled in the Application Layer Gateway (which let me play lan games on all blizzard games when i had windows) so I'm not sure if it's to do with ports.
One problem it might be:
Though from Ubuntu I can see and access all comps in the windows network, my Ubuntu comp does not appear in the network from the XP comp, and can't get to it from the address bar... maybe this is the problem?
:(

All suggestions welcome!

---

### Post by Silpheed2K on 2008-05-20
ever thought about tunneling over the internet and then directing it back to your LAN...
i doubt that would work but a lot of people have issues with Warcraft 3 and LAN... I have Warcraft 3 frozen throne on Wine on my windows partition... haven't tried it on LAN though.
I'm interested to see how this develops but from what I've read on ubuntu edgy it worked but all versions after that it didnt for some reason.

---

### Post by danwizard208 on 2008-05-21
I think I may have a solution (patching both comps to the same version of Warcraft 3), but just in case, could you explain what you mean by, "Tunneling over the internet and then directing it back to your LAN"?

---

### Post by Silpheed2K on 2008-05-21
Tunneling your LAN allows you to to play somebody else over the internet via the LAN option in the game... this will actually link you and the other persons LAN up so be careful because you dont want to link up to somebody with an infected network (virus) cause it will be just as if your networks were hard wired together.
but instead of that... using a VPN program like Hamachi or Tinc or OpenVPN to accomplish this.
Doubt it would work but you can always try... however I'd try to see if there's a way through wine it can be accomplished cause it worked on previous versions of ubuntu but not the latest releases it seems.

edit: what i'm really getting at i guess is bridging the connection of the 2 computers

edit 2: [http://ubuntuforums.org/showpost.php?p=4169307&postcount=4](http://ubuntuforums.org/showpost.php?p=4169307&postcount=4)

edit 3: can somebody else please step in and help him because i don't exactly know of a definite way of fixing the problem.. thanks.

---

### Post by danwizard208 on 2008-05-21
Patching the games seems to have worked, we can play together, i can connect to his games, only problem is that he can't connect to mine (still can play together though). Thanks anyways!

---

### Post by Silpheed2K on 2008-05-22
> **danwizard208 said:**
> Patching the games seems to have worked, we can play together, i can connect to his games, only problem is that he can't connect to mine (still can play together though). Thanks anyways!

no problem, but i just found this post and it had a solution in it i guess
[http://ubuntuforums.org/showthread.php?t=620480](http://ubuntuforums.org/showthread.php?t=620480)

It has something to do with patching wine but if oyu got it working i wouldn't really mess with it lol
great to see you have it working

edit: also you may want to check this out too [http://ubuntuforums.org/showthread.php?t=795714](http://ubuntuforums.org/showthread.php?t=795714)

---

