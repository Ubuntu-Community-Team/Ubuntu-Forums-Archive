---
title: "Excel Errors in 14.04/Wine/PlayOnLinux"
date: 2014-09-05
forum: Wine
---

### Post by mike240 on 2014-09-05
Ok, just made the jump from Windows, I'm VERY much over my head now and I need MS Office 2007 for work.

**First Method:** I Installed using Wine. Can't save my files. So I looked online again and found....

**Second Method:** Install using PlayOnLinux. Now Excel will not display axis labels in graphs, which I think is renders excel useless for my needs. 

I'm using the newest versions of everything, since I just made the switch this week. I read about setting riched20.dll to native, but that didn't seem to change anything for me. 

For testing I used a stupid graph:

[B]Jim > Ted > Frank
  1 >   4  >   3
[/B]
I Highlight all 6 cells, then select bar graph. I get the graph (3 blue bars with the correct values), but I have no labels on my axis. What gives? Also, if you have instructions requiring the use of the terminal, I'd appreciate severe hand-holding as I am the uber newb in this OS....

Thank You For Your Time,

Michael

---

### Post by EuclideanCoffee on 2014-09-06
Have you tried [LibreOffice Calc]("http://www.libreoffice.org/discover/calc/")? It's the green icon that should've been one of your default apps.

With PlayOnLinux you can configure multiple wine configurations for one app or many. I suggest using it. Go to your configuration tab and look around.
[http://www.gamersonlinux.com/forum/threads/playonlinux-explained-wine-configuration.267/](http://www.gamersonlinux.com/forum/threads/playonlinux-explained-wine-configuration.267/)
[http://www.playonlinux.com/en/dev-documentation-5.html](http://www.playonlinux.com/en/dev-documentation-5.html)


Here's some more information about what you'd need to configure. The WineHQ is a good tool to see what works and what doesn't.
[https://appdb.winehq.org/objectManager.php?iId=4992&sClass=version](https://appdb.winehq.org/objectManager.php?iId=4992&sClass=version)

Good luck!

---

### Post by mike240 on 2014-09-07
Thank you for the great alternatives, but I really needed something where I will not lose ANY formatting changes from my computer to my clients'. My "solution" was to get an old laptop, dust it off, wipe the drive and install MS Office on it. I can do my work on a separate system for now I guess. I sure wish I hadn't botched up making a dual boot....

---

### Post by EuclideanCoffee on 2014-09-07
> **mike240 said:**
> Thank you for the great alternatives, but I really needed something where I will not lose ANY formatting changes from my computer to my clients'. My "solution" was to get an old laptop, dust it off, wipe the drive and install MS Office on it. I can do my work on a separate system for now I guess. I sure wish I hadn't botched up making a dual boot....

Sorry to hear that.

You can also run Windows in a virtual machine. There's still hope.

---

