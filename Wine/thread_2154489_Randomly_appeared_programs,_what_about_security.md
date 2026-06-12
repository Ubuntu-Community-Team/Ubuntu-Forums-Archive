---
title: "Randomly appeared programs, what about security?"
date: 2013-06-14
forum: Wine
---

### Post by chrisjxw on 2013-06-14
Hi

I'm a long time Linux user, and trying to help someone moving over to Ubuntu from Windows.

I didn't install Wine for him, and didn't think anything about it; seems it was installed by default. (I *did* worry a bit about installing Flash, but I did that because I didn't want to provide him with unexplained random web breakage).

Today I noticed that his computer was very slow, and noticed that there were two .exe programs running eating all the CPU. (I copy pasted some info but don't have access right now, will post tomorrow.) Using locate I couldn't find any other location for the exe files than in his ~/.local/ and ~/.wine/ folders. How did they get there, then? I guess the only way is through running a differently-named installer. What I'm concerned about is whether he downloaded and ran some windows binaries without being aware of it (he said he didn't think he installed anything), or worse, something that was downloaded and executed without any further ado.

In the interest of security I've removed Wine from his computer now.

Is there a better explanation than mine above? Did you experience the same? Should inexperienced people just not have Wine installed on their machine?

Ch.

---

### Post by user_of_gnomes on 2013-06-16
> Did you experience the same? Should inexperienced people just not have Wine installed on their machine?


Absolutely. I've worked a lot with Wine in the past weeks and although it is a great solution, it should only be implemented on a per-program basis and set up in such a way that it does not affect the rest of the system (For some reason, Wine is configured to share the users' home folder resources by default.) or that the user can even install Windows programs beyond the ones that are absolutely necessary to run. You also need make sure that Wine is actually shut down when you quit the program in question. 

I ran Steam through wine without the virtual desktop and it had the habit of continuing to run even though I couldn't open Steam any more because of the way Steam handles shut downs (It minimizes rather than shutting down). I can imagine that if your Wine installation installation is infected, it might not shut down properly either.

>  (he said he didn't think he installed anything)

Some people will click on -anything- and not remember afterwards. Or even care to tell the truth.

The best way in my experience to get someone used to moving over to Linux is by installing Thunderbird, Firefox and all other sorts of open source programs under Windows and then when they've worked with those for a while, you can replace Windows with Ubuntu. For programs that they may have worked with all their lives and can't let go of for some reason (think shopkeepers with 15-year-old DOS accounting software, yes they do exist) you should probably use Wine. (Or alternatively DOSBox!)

Check out some of these links on why Wine is a security risk:

[http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)
[http://askubuntu.com/questions/5031/what-if-i-run-a-virus-trojan-windows-exe-on-ubuntu-with-wine](http://askubuntu.com/questions/5031/what-if-i-run-a-virus-trojan-windows-exe-on-ubuntu-with-wine)

---

