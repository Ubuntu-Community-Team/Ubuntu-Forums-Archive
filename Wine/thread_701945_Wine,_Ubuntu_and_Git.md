---
title: "Wine, Ubuntu and Git"
date: 2008-02-19
forum: Wine
---

### Post by denali on 2008-02-19
So, in the process of waiting for Wine 0.9.55 to arrive, I decided to switch to the version stored in the Wine Project's Git repository.  It works great and I'm happy with it.

I know nothing about scripting, but I'd like to automate the updating of my local Git repository.  Basically, what I'm looking for is a script to do:

1) git fetch

Then, it this results in a change to the local repository, do the following:

2) git rebase origin
3) configure
4) make depend && make
5) zenity --info --text=Wine Updated!

I'm not even sure if this is the right forum for this.  If it isn't, I apologize.  Any help is appreciated.

denali

---

