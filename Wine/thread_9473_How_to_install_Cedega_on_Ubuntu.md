---
title: "How to install Cedega on Ubuntu"
date: 2004-12-29
forum: Wine
---

### Post by nejc0 on 2004-12-29
Hi!
Please help me......How to install Cedega on ubuntu.....and how to install game and play?
Bye

---

### Post by p!=f on 2004-12-29
Use search feature on this forums. :)
See this thread:
[http://www.ubuntuforums.org/showthread.php?t=4428&page=1&pp=20](http://www.ubuntuforums.org/showthread.php?t=4428&page=1&pp=20)

---

### Post by Perfect Storm on 2004-12-29
Grab it at [www.transgaming.com](www.transgaming.com) (cost $5 at month). There's cedega.deb files. But go for the Point2Play.deb it's a nice gui for cedega (easy to use). Through Point2Play press download Cedega.

To install a deb file:

```

cd /where/you/saved/the/file/
sudo dpkg  -i  Point2Play_[version].deb

```

Now you can run Point2Play by writting in the terminal or the 'run application' box by writing 'Point2Play' Or make a application launcher like this

```

nautilus applications:///Games

```

 File Menu -> **Create Launcher**

Basic Tab ->
Name: **Cedega**
Command: **Point2Play**
Icon: **/usr/share/icons/Point2Play.xpm**

Now go to Applications ---> Games and press Cedega icon.

That's it :)

---

### Post by Randabis on 2005-01-01
I've found a free alternative to Point2Play, it's called Grapevine.

Do a google search for it. It has .deb files for easy installation. It works great. There's also .deb files out there for the latest Cedega.

---

### Post by hardcandy on 2005-01-01
> I've found a free alternative to Point2Play, it's called Grapevine. 
Come on, give the guys at Transgaming their $5 a month. I'll bet you can afford it. At least let some programmer keep working. If 1000 people chip in $5 a month, I'd bet that would keep someone working.

---

### Post by Randabis on 2005-01-01
[QUOTE=hardcandy]Come on, give the guys at Transgaming their $5 a month. I'll bet you can afford it. At least let some programmer keep working. If 1000 people chip in $5 a month, I'd bet that would keep someone working.[/QUOTE]
 Linux is about having choices. I simply provided another option and verified that it works.

---

### Post by pavkonti on 2005-01-01
[http://www.linux-gamers.net/modules/wfsection/article.php?page=1&articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?page=1&articleid=45)

---

### Post by the_epic on 2008-02-18
I double clicked on the .deb file. Everything installed perfectly (or so it says). But I can't locate it anywhere.

Edit: Never mind, I located it.

---

### Post by multilanguman on 2008-03-08
[QUOTE=the_epic;4353150]I double clicked on the .deb file. Everything installed perfectly (or so it says). But I can't locate it anywhere.

I did the same, but my problem is that when I try to launch cedega, my system either freezes completely (just like in the bad old Windows days) or logs out. I have tried uninstalling and reinstalling, no difference. I suspect I may have to reinstall Ubuntu and try again.

---

### Post by b0ktai on 2008-06-20
> **hardcandy said:**
> Come on, give the guys at Transgaming their $5 a month. I'll bet you can afford it. At least let some programmer keep working. If 1000 people chip in $5 a month, I'd bet that would keep someone working.

Is not the whole linux thing 'free distribution'?

---

### Post by Perfect Storm on 2008-06-20
> **b0ktai said:**
> Is not the whole linux thing 'free distribution'?

No - It's about an alternativ. You can't say Linux equals GNU (open source) equals free software (as in free beer). It's much more complex to define.

You can get close source software for linux which you can get for free (freeware) and commercial (pay-ware).
Then you have Open Source and again which license the Open Source is under, you can get freely - then there's Open Source software which cost money, it's still free (as in Open Source), but cost money.

This is a quick and rough explaination. If you want and indepth of diffrent license I suggest google/wiki search and alot of coffee because it's a jungle of FUD and facts out there, and everybody also have an opinion which can be biased towards one or another.

---

