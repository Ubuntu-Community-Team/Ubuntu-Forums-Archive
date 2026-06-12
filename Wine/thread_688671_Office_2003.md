---
title: "Office 2003"
date: 2008-02-05
forum: Wine
---

### Post by Stephan Smith on 2008-02-05
Hi, All,
    I just installed Ubuntu 7.10. I need to run Microsoft Office, as I am in college, and the school will not accept work done in anything else. I installed wine through synaptic, and  then installed Office 2003. It installed ok, but every time I try to start something, such as Word, I get an error that says, "Microsoft Word has not been installed for the current user. Please run setup to install the application." 
  Obviously I installed it, or I wouldn't have an icon in wine to press to start it, and it wouldn't open to the desktop before erroring out. Does anyone have any suggestions? I really need to get Office 2003 and Visio 2007 set up, so I can avoid my windows install; right now, that's about the only thing stopping me from going windows-free.

Thanks in advance,

Steve

---

### Post by pytheas22 on 2008-02-05
Installing Office in wine isn't trivial.  It may appear to install alright, but there are a lot of hacks you need to do to get it to run, I think.  There's a commercial product called CrossOver Office available that will make it easy, or there might be tutorials on how to do it if you search around the Internet.

That aside, as long as you save your work in Microsoft file formats, which OpenOffice can do without any problems, how would your college even know what program you're using to create them?  If you need to submit a file, just go to File>Save As and select the kind of file format you need (like .doc or . ppt).  You can also change the default file format to always be Microsoft's if you want, although I don't know how off the top of my head.

I've used OO exclusively for two years at my university, which also refuses to support it/acknowledge the existence of non-Apple and Microsoft platforms, but it's never a problem as long as I make sure to convert my work to proprietary formats that can be read by people using Microsoft Office.

---

### Post by Stephan Smith on 2008-02-05
I wish I knew how they know! I've done a couple papers in Open Office, because I didn't want to waste the time rebooting into windows just to do the paper and go back to Linux. I saved in windows format, and turned them in (my classes are online). I have gotten emails back from the teacher both times, telling me that the school only supports microsoft office, or its' mac equivalent, and returning the papers to be redone. I know I saved them in word format, because they would open in word. Maybe it was the formatting; when I opened them in word, some of it looked a little off. And I have a project due soon that has to be done in visio. No getting around using office for that...

Steve

---

### Post by pytheas22 on 2008-02-05
That's strange, there could be something weird going on...if you try doing unusual stuff like embedding videos into your documents or something I know that there can be problems.  I've never had problems saving in Microsoft formats.

Another solution would be to export the paper to pdf.  Also, another thing to check is that the file you send has a filename extension; otherwise Windows panics and doesn't know what to do, and your professor might not be competent enough to realize that adding .doc to the end is all he needs.

A more comprehensive solution to your problem is installing XP and Office inside a virtual machine like virtual box, [http://www.virtualbox.org/](http://www.virtualbox.org/) .  It's free, stable and very easy to install XP into, in my experience.  That way you could run whatever Windows software you want inside Ubuntu.

Otherwise, think about crossover or search for howto's on installing Office in wine...

---

### Post by Stephan Smith on 2008-02-05
I'm trying to install virtualbox now; ran into a snag during install, and I've got a post in their forum to find out if it means anything. Silly question: does Ubuntu come with a firewall? If it does, how do I turn it off?

Thanks,

Steve

---

### Post by Whiffle on 2008-02-05
If you're using the latest wine from the winehq website, Office 2k3 works fine.  I've got it running on mine.  If it gives you that error about it not being installed for the current user, run the office install/setup program again in repair/reinstall mode and it should fix it.

---

### Post by Stephan Smith on 2008-02-05
Thanks, Whiffle,
I tried that several times; I'm still getting that error. One thing I've noticed is, the first time I installed it, it asked for my name; it hasn't asked since, even when I uninstalled, then re-installed. And even when I uninstalled, it was still there....

Steve

btw - the program I need working the most right now, visio 2007, is on the list of programs that doesn't work yet....

---

### Post by doorknob60 on 2008-02-05
I've used Crossover for MS Office before and it works just fine and it's easy. But I can't see why they won't accept Open Office stuff as long as you saved it right. Also, I'd be glad to help you with Virtualbox because I use it too.

---

### Post by Epiphyte on 2008-02-05
RE POSTED elsewhere. This topic is meandering.

---

### Post by pytheas22 on 2008-02-05
> btw - the program I need working the most right now, visio 2007, is on the list of programs that doesn't work yet....

if this is the case then a virtual machine would be the only alternative to dual boot, unless you want to be ambitious and be the first person ever to make Visio run in wine.  I did some quick searches and it looks like it definitely doesn't work, even the eight-year-old version doesn't work: appdb.winehq.org/appview.php?iVersionId=175 .

> I'm trying to install virtualbox now; ran into a snag during install, and I've got a post in their forum to find out if it means anything. Silly question: does Ubuntu come with a firewall? If it does, how do I turn it off?

No, Ubuntu has no firewall running...you could say that it "comes" with a firewall, as the backend is built into the Linux kernel, but you would have to turn it on for it to start doing anything.  In any case, if you need help installing Virtual Box you should search the forums for the information you need or start a new thread, since this one is on a different topic.

> 
I'm running Wine 0.4.96 on Xubuntu 7.10. I'm on an old machine, but the idea was to test software compatibility, not to get hardware speed.

maybe it's a typo, but i think wine is on version 0.9. something now, so you should definitely make sure you're using the latest version of wine before anything else

---

### Post by kbless7 on 2008-02-05
I have heard that running the install file again and selecting the repair option gets rid of the "current user" problem. Its worth a try.

---

### Post by Stephan Smith on 2008-02-05
Hey, doorknob, I just got my glitch with virtualbox fixed; windows xp is installing as I type this. I think, for now, that I just won't worry about wine. Thanks, Pythias, I may need your help eventually!  Kbless, I tried that several times; I also tried uninstalling and reinstalling several times. That didn't work, either. I've got virtualbox running now, so I think I'll play with that and see what it can do. Thanks for the help!

Steve

---

### Post by Stephan Smith on 2008-02-05
Now, there's an interesting sight. Windows running in a window. That is poetic justice!!!!

---

