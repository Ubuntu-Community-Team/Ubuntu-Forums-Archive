---
title: "Ubuntu and apps crashing"
date: 2009-07-23
forum: x86 64-bit Users
---

### Post by jstorta on 2009-07-23
I installed 9.04 64-bit about a week ago.  It has worked great and I was finally ready to bid farewell to Windows.  Then today I had a problem occur that has me baffled.

This morning, I was prompted to install some updates, which I did.  They were for firefox and something called xulrunner.  Might have been something else as well.  I watched the updates proceeding and after they downloaded a segmentation fault message appeared in the update manager.  Then Update manager crashed.

I forget the exact sequence of events because after the issue was resolved, I figured everything was fine.  At some point I was told something was partially installed ( I think the xulrunner updates) and that I needed to run an apt-get command.  I did so and I thought the problem was over.

All day today I have had random crashes.  At first I just thought it was FireFox.  I would be at web pages and it would just go grey and freeze.  I would let it sit several minutes to see if it would start again, but nothing.  I would have to do a force quit.  There seemed to be no rhyme or reason to what page I was on or what I was doing.

As the day wore on, I noticed that it was not just FireFox.  Other apps were crashing as well, including the Ubuntu Help Center.

I had none of these issues before today so I am convinced that something I have done today introduced this problem.  The question is what?  And, can I fix it without having to rebuild my system?

I have attached the dpkg log showing the messages from the updates installing.  Since I know there was a problem getting them installed, that seems to be the most likely culprit.

I also installed Wine today through Synaptec and installed several Windows apps using Wine.  A couple had to be uninstalled because they did not work.

Bottom line.  Something in the environment is unstable.  Firefox crashes.  Other apps are crashing.  Ubuntu itself has locked up at least twice forcing me to do a system reset.

I am looking for some help on a plan of attack.  How can I backout the updates?  Should I uninstall Wine?  

Any thoughts?


Thanks,
John S.

---

