---
title: "64-bit Repositories"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by bgeek on 2006-08-04
Hi all,

I'm new to the AMD 64-bit Ubuntu and wondered if there are any other repositories that I should be looking at i.e. official and unofficial.  In particular any repositories with multimedia support.  I'm also interested in XGL ;)

I've noticed threads on how to get things like flash, java, mplayer, etc, working, but I've not seen any mention of repositories :)

Cheers,

gerald

---

### Post by M3phista on 2006-08-04
Hi,

you can modify your sources.list:

```
sudo gedit /etc/apt/sources.list
```

and there you can remove the '#' before the "deb http://..."-sources.
Especially those which have the information 'universe' and 'multiverse' at
the end.

Concerning XGL + Compiz:

add the following sources to your sources.list:

```

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
deb http://ubuntu.systemadministrator.org dapper eyecandy
deb-src http://ubuntu.systemadministrator.org dapper eyecandy

```

after that you also need to get the passkeys for these sources.
Execute:

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

and:
```
wget http://ubuntu.systemadministrator.org/2F306651.gpg -O- | sudo apt-key add -
```


But be aware that xgl + compiz are still not running perfect.
I recommend this tutorial: [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)
wit the **second method**.

Hope this helps.. otherwise, google is always your friend ;-)

---

### Post by bgeek on 2006-08-04
Cheers for that :)  That was a little more than what I was after - I'm not new to linux or debian-based distros.  My only concern was that some of the unofficial repositories that were specifically 32-bit might not be available for 64-bit :) I'll go play.  Thanks.

---

