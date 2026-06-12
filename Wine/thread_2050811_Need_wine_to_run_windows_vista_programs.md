---
title: "Need wine to run windows vista programs"
date: 2012-08-31
forum: Wine
---

### Post by ectechnologies on 2012-08-31
Hi,

I have a customer who has full ubuntu install, she wants to install a windows program (500,000 Games 2.0).

I am trying wine but it doesn't seem to work. I am trying not to pay for crossover, but any free alternatives, I will be greatly appreciative.

---

### Post by oldos2er on 2012-08-31
Moved to Wine.

---

### Post by wheeze on 2012-08-31
PlayOnLinux maybe?

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

It's essentially WINE but has a better user interface for config and installations.

---

### Post by ectechnologies on 2012-08-31
Hi,

Sorry guys, i needed to up date it to 1.4 through terminal:

sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get dist-upgrade

then:

wine --version



Thanks for the help though

---

### Post by RedRat on 2012-08-31
Just be aware that some Windows programs don't install correctly with Wine. You may well have to do some futzing about to get them installed. You may well have to download some freebie stuff from Microsoft, e.g., some DLL's, or other things. The version of the Ubuntu can play a role here too. I found that I could install one of my favorite Windows program, ThumbsPlus, on 12.04/64, with a considerable amount of futzing, but could not get it to install on Mint 13/64. On the other hand, I could install my newsgroups program, NewsRover, on the Mint 13 machine relatively easily! Earlier versions of Ubuntu, e.g., 8.04, most Windows programs seem to install under Wine, but I suspect that later Windows programs may be more difficult.

Much will be dependent on the libraries that the Windows application needs to run. I do not play Windows games (just not a gamer), so can't say whether you will be successful. 

I suspect that as Window progresses along, it may become increasingly difficult to install those programs unless the Wine developers move along with Windows. I can't comment on Crossover since I have never used it.

---

