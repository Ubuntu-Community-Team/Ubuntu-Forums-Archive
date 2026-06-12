---
title: "Using a Wine Game with Hamachi"
date: 2007-09-10
forum: Wine
---

### Post by beastrace91 on 2007-09-10
I am currently using Diablo2 trough wine on my kubuntu 7.04 I am also using hamachi to network with a few friends here at college. I am wondering if anyone knows how to make my Diablo2 work with my hamachi? When ever I try to connect to my buddies hamachi IP I get can't connect to server. Also my IP that D2 detects is 127.0.1.1 (or the home IP)

Any Ideas?
~J3ff

---

### Post by j.miller565 on 2007-09-10
have you try 
```
hamachi go-online
```

yet?

---

### Post by beastrace91 on 2007-09-10
Just tried that same resualt. and same home IP

~J3ff

---

### Post by beastrace91 on 2007-09-10
nvm go-online made it work thanks man.

~J3ff

---

### Post by Yangshuo Joe on 2008-07-15
I'm trying to do the same thing here. I have Diablo 2 installed in Wine on Ubuntu Heron.

My friend is using XP and has Hamachi installed.

I was trying to install Hamachi for Ubuntu but I wasn't sure if I was supposed to install the Linux version or if it can be installed as a windows app inside of Wine. I tried to do both and failed :)  

But if I knew which way was the best way to go, I'd work harder to get it to work.

Any suggestions?

Thanks

---

### Post by Yangshuo Joe on 2008-07-18
I finally got it installed on Linux (outside of Wine), so problem solved... time for gaming :D

---

### Post by mriedel on 2008-07-18
Installing the linux version of wine and hamachi-gui worked fine for me, but you still can't play D2 with that.

I tested it on windows and in order for it to work you need to add a peer vpn alias for the person you want to play with (so that the first two octet pairs of their hamachi ip are identical to yours). hamachi-gui doesn't have that option though and neither does the hamachi cli. For earlier windows versions of hamachi, you could just add an alias.txt in the hamachi directory and define aliases there. Is there any similar way to do this on linux? I actually haven't even tried putting an aliases.txt in ~/.hamachi.

Furthermore, I can't ping anyone on hamachi, neither through hamachi-gui nor via shell:

> mriedel@mrDesktop:~$ ping 5.X.X.X
PING 5.X.X.X (5.X.X.X) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

---

