---
title: "Rift on ubuntu 12.04 (help!)"
date: 2012-06-10
forum: Wine
---

### Post by liamm on 2012-06-10
Recently [I]I have been trying to make rift run on ubuntu 12.04 and im having no luck.
I got windows 7 installed as-well so i ran rift on that and it worked with no problems.

When trying to play rift on ubuntu I dont recieve any errors  but when I press play nothing happens??

I haven't a clue what to do so any help would be great!!
[/I]

---

### Post by ajgreeny on 2012-06-10
What is rift?

If it is a windows application or game you may get it to run in wine, but many windows programs will not run at all, or only partially.

[Wine Application DB]("http://appdb.winehq.org/") 
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by liamm on 2012-06-10
Its a game that many people have got running on ubuntu, but I think it might take some hours to get it working properly !

---

### Post by schtufbox on 2012-06-12
Just in case it's hitting the same issues as a few other games in wine with 12.04, try entering the following in a terminal before running the game, and see if it helps.

```
echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
```

---

