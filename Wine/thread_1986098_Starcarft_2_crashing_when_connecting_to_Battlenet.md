---
title: "Starcarft 2 crashing when connecting to Battlenet"
date: 2012-05-24
forum: Wine
---

### Post by sffvba[e0rt on 2012-05-24
**UPDATE: Using [this hack]("http://www.evilcodingmonkey.com/2012/05/15/playing-diablo-3-on-ubuntu-made-very-easy/") I found online to be able to authenticate Diablo 3 I was able to also get my SC2 to work!**

Hi,

I have played Starcraft 2 under PlayOnLinux some time ago, but recently I have not been able too (FTR, I have now even installed Crossover Trial and I get the same issue in both).

The game installs and patches itself fine, it also runs OK, but once it has to connect to the Battlenet server for authentication it crashes.  I am able to test this by disabling my networking so it can't attempt to authenticate, the game will then not crash right after starting.

But once I enable networking, add my e-mail and hit connect it crashes straight away :/

Thus far nothing on-line I have read has shed any light on this strange phenomenon.



404

---

### Post by sffvba[e0rt on 2012-06-22
Can't believe I haven't posted the solution to this yet...

Run the following from terminal before trying the game and login issues for Starcraft 2 are gone:
```
echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
```

ALSO, if you are having the same issue with Diablo 3, run the code above, and then run:
```
sudo sed -i 's/kernel.yama.ptrace_scope = 1/kernel.yama.ptrace_scope = 0/' /etc/sysctl.d/10-ptrace.conf
```


404

PS - Please note that I have no technical idea what the codes above are doing, except that they work and I have used them to log in and play both these games successfully :)

---

