---
title: "Help Installing trading platform (beginner)"
date: 2008-09-11
forum: Wine
---

### Post by tstack77 on 2008-09-11
I use a proprietary trading platform at work where I have 8 monitors in winXP. I am having shoulder surgery on monday and will be stuck in a lazyboy for two weeks unable to commute to work. I am trying to set it up at home in hardy (wine 1.1.3) so I can use multiple desktops and not lose the vital screen space (only have 2 x 19" here).

When I first installed the software I ran into problems that were solved by installing winetricks and MFC42.DLL. However, now when I run it I cannot get it to load after I input my username/password. The main window opens but freezes immediately.

Running it from the terminal doesn't help because it doesn't display any errors, it just freezes the same as the program.

Is there something else I can try to diagnose the issues here?

---

### Post by Thelasko on 2008-09-12
Was this software created by your company, or do they purchase it from somebody?  If it was created in house, your best bet may be talking with the person that created it.

If it's purchased software, check wine's application database.  I found instructions for [MetaTrader]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2893&iTestingId=22068").  It appears that [Visual Trader]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9912&iTestingId=17859") won't work.  I was unable to find information for [TradeStation]("http://en.wikipedia.org/wiki/TradeStation").

---

### Post by Caedis on 2008-09-12
Being that it&#8217;s a custom trading app I would recommend running it in VMware honestly. I keep a Virtual Machine of windows XP around for just such occasions. I know it&#8217;s not the most elegant solution but if you don&#8217;t know and the developer that made it doesn&#8217;t know, then that&#8217;s just about all you can do. If it were a mainstream app I&#8217;d say just wait for someone to make a fix, but your options are very limited with this.  

(besides, you can &#8220;evaluate&#8221; VMware for full month for free. That should cover your down time I think) 

[VMware Main Website]("http://vmware.com")
[VMware Linux Evaluation]("https://www.vmware.com/tryvmware/login.php?eval=workstation-l")

If you need any help getting VMware installed (should you choose to go this route) let me know.

---

### Post by Thelasko on 2008-09-12
> (besides, you can “evaluate” VMware for full month for free. That should cover your down time I think) 
Yeah, but VirtualBox is free.  (Note: with both VirtualBox and VMware you will still need a copy of Windows)

---

### Post by Caedis on 2008-09-12
> **Thelasko said:**
> Yeah, but VirtualBox is free.  (Note: with both VirtualBox and VMware you will still need a copy of Windows)

Free, yes. I just prefer VMware since the VMs can be moved to any host OS without any issue. That, and the fact that VMware is a highly respected and trusted company that I’ve been using for several years now without ever looking back.

But I digress, back to the topic. A virtualization environment may be your best be to get this working, just get a copy of XP is all. (And that’s the hard part)

---

### Post by tstack77 on 2008-09-12
Thanks for the suggestions, I should have clarified that I already have xp installed in a dual-boot system. The reason I want to get this running in wine is simply so I can use the multiple desktops to simulate an 8-monitor environment. I have tried trading on the two 19" screens here and it's very limiting to say the least. 

I asked our admin at work and unfortunately it was not created in-house but was contracted out to a developer. He told me it wouldn't be possible to get their help on this issue anytime soon.

Is there nothing more that I can do on my end to figure out what the hang-up is?

And if not, is it possible to create a multi-monitor virtual environment? I have virtualbox installed but have not been able to figure this out. Is vmware a better option?


thanks again

---

