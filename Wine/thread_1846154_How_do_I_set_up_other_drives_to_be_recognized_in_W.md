---
title: "How do I set up other drives to be recognized in Wine?"
date: 2011-09-18
forum: Wine
---

### Post by PayPaul on 2011-09-18
[SIZE=2]I had a problem after the install of Winamp. It could not see any other partition/drive except for the C drive which of course contains my Win7 install. I see in the settings for Wine that one can add other drives to the program to be recognized. It's very confusing to do for a newbie and I'd appreciate some help in going about it. I suspect the reason Winamp couldn't find my other drives/partitions where I have my music files is because Wine needed to create folders pointing to them. [/SIZE]

:popcorn:

---

### Post by An Sanct on 2011-09-18
Welcome!

Go to Applications > Wine > Configure WINE then open the tab drives and there you can configure new path-"drive letter" combinations.

---

### Post by Elfy on 2011-09-18
Thread moved to Wine.

---

### Post by PayPaul on 2011-09-18
> **An Sanct said:**
> Welcome!

Go to Applications > Wine > Configure WINE then open the tab drives and there you can configure new path-"drive letter" combinations.

What do I do? Just make up drive letters? I know the drives have specific drive letters but do I also have to include their volume names? I just add a **/x** with x being the drive letter?

I go to the properties of multiple drives and I see the path **/media** for all the drives I'm interested in allowing Winamp to access. I don't see drive letters for these drives/partitions. I do see their volume names only.

:???:

I'd love to see a screen shot or a tutorial somewhere on Wine.

---

### Post by An Sanct on 2011-09-19
Linux has no "drive letters" :) if you mount your NTFS drive for example D:, then it will be something like /media/XXXX-XXXX. You can also mount it to something else. Then point WINE's "D:" to the path where you mounted the drive. Winamp will see it as D:.

---

### Post by PayPaul on 2011-09-19
> **An Sanct said:**
> Linux has no "drive letters" :) if you mount your NTFS drive for example D:, then it will be something like /media/XXXX-XXXX. You can also mount it to something else. Then point WINE's "D:" to the path where you mounted the drive. Winamp will see it as D:.


Ok. I put in the path of each drive in the path box with /media/xxxx and hit apply. Should Wine have made folders in its folder as it did for my C drive when I installed it? Does that take awhile maybe?

---

### Post by An Sanct on 2011-09-19
I really don't know :)

For the full and complex info on how WINE handles files, you can read [this]("http://www.winehq.org/docs/winedev-guide/x2987").

But from the user point of view, I would say, the folder/location has to exist, just like in Windows. Or the drive access API "reports" an unformatted drive with unknown metrics... So create the folder first or map the drive and then restart WINE (a system reboot will also do).

---

### Post by PayPaul on 2011-09-25
Hee! Hee! I think I figured it out! When I add a new path I click on the Browse button next to path, look for the Media folder in the Unix file system, find the folder entry for the "Drive" I'm looking to add to Wine's drives function and click OK. Now I see. Unix/Linux creates entries in its file system that point to the actual drives on my system. I then clicked apply and it worked! 

Now Winamp can add the folders within those physical drives to its library. The only glitch if it is one that I see is loading individual music files is very slow. Is this because it's a virtual machine? I think that first there is the connection to the Unix folder in question then a directive has to be sent to locate distinct files within that drive. Winamp may not be the best program to run within Wine but I'm glad to have solved this.

I've added some jpeg images of the two screens for illustrative purposes.

:lolflag:

---

