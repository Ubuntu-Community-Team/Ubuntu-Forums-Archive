---
title: "Odd Issue with windows"
date: 2009-02-01
forum: x86 64-bit Users
---

### Post by bshiers on 2009-02-01
I'm having an odd issue with the x64 version of Ibex, Kubuntu.  I'm not sure what I did, but I've somehow the top bars on all my windows have gone missing.  I can't close, resize or move windows around.  

I've went through and reset all my apperance and theme settings to default -and that has not helped.  I am running kernel 2.6.27-9.  I did the last batch of recent updates and have to roll back to this kernel so I could still use virtualbox.  I'm using KDE.  

I also went back and set kwin as my window manager rather than compiz. 

Any suggestions?  This is very frustrating, as I can't figure out what I did!

Thanks,

Brandon

---

### Post by mgranet on 2009-02-01
I had the exact same problem with Gutsy and Hardy. I spent hours trying to track it down back then, and the closest I ever came to figuring it out was that it is compiz related. VirtualBox and Firefox were extremely susceptible to the titlebar disappearing. Compiz and Kubuntu Intrepid also do not play nicely together.

The only way I was able to get rid of the problem was to get rid of compiz completely (i.e., reinstall Kubuntu, changing back to Kwin did not work.). Besides, with KDE4.2, most of the compiz type of effects are implemented in KWin. It's MUCH more stable, but the downside is that with no Emerald, there's no effective way to theme your titlebars. :(

---

### Post by Uubnewb on 2009-02-01
I'm using Ubuntu 8.10, and it happened to me as well, but only with Firefox.  There has got to be a way to fix it other than getting rid of Compiz.

So far I'm handeling it by pressing F11 once to get Firefox fullscreen, and a second time to exit fullscreen mode.  After the second time I press F11 I have my top titel bar back.

---

### Post by mgranet on 2009-02-01
That's a good workaround, but unfortunately, the problem lies with Compiz or the Emerald themer or it's interaction with KDE. I've spend many dozens of hours trying to determine the problem, but in the end, the only effective way I've found to eliminate the problem is to not install compiz.

Which really sucks, because the default KDE titlebar theme is not very pretty, and there's no way to change it to anything other than previous KDE themes and the few on KDE-look.

If anyone knows how to get Compiz working reliably, please let us know.

---

