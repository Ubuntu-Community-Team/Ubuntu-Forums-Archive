---
title: "Troubleshooting Baldur's Gate 2 multiplayer"
date: 2012-08-20
forum: Wine
---

### Post by aaeamdar on 2012-08-20
So first off, (for people who know the game) I'm not actually trying to play the game "multiplayer" - I just want to be able to make all my own characters. So if someone has a workaround (like I know once you have a mplayer save you can convert it to a single player game to remove some of the inconveniences - but right now I can't even get the original mplayer save) I'm all ears.

My specific issue: I've installed the game, I can run single player, but when I try to start a multiplayer game everything goes black (and nothing happens). I followed the steps here:

[http://wiki.winehq.org/DirectPlayGames](http://wiki.winehq.org/DirectPlayGames)

I tried the "full installation details" first, but I ran into a problem with step 5, "run regsvr32 on each of: dplayx.dll dpnet.dll and dpnhpast.dll, eg "regsvr32 dplayx.dll"" . When I tried running regsvr32 it said "cannot load xyz.dll", even though I could clearly see they were there (this was the same error I got if I tried "regsvr32 notarealname.dll"). 

I tried just moving on to step 6, but of course without a lot of hope for it working (it didn't).

I then opened up a terminal and did "sh winetricks directplay", which out-putted some text suggesting that the DLLs had been successfully registered. However, I tried again and the same thing happened.

Any thoughts? I'm really new at Ubuntu so please be specific and simplify things for me.

Thanks

P.S.: I don't have access to a Windows install, so don't say "Install the game in windows and then transfer it" etc.

---

### Post by aaeamdar on 2012-08-25
I actually managed to resolve the issue by following this excellent guide:

[http://ubuntuforums.org/showthread.php?t=1437195&highlight=baldur%27s+gate](http://ubuntuforums.org/showthread.php?t=1437195&highlight=baldur%27s+gate)

I'm going to mark this as solved unless anyone else has a similar issue that isn't resolved using the above.

---

