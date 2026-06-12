---
title: "removed evolution pkgs and lost ubuntu juanty jack"
date: 2009-09-17
forum: x86 64-bit Users
---

### Post by Shobuz99 on 2009-09-17
I've done it this time. I went to Synaptic Pkg and removed, what I thought was the Evolution email client. 
I was tired of it, and wanted to try the Thunderbird 3.0.3 Beta. 
Apparently, I removed MORE than just that. I selected everything that was Evolution named...BIG Mistake!
I must have 'removed' some Gnome pkgs or some critical pkgs that make the whole thing work. 
Once I restarted I couldn't get back into Ubuntu (9.04). I get through Grub, and the login/pw and that's as far as it gets. 
I sit there staring at a blank/black screen and my mouse cursor. Ubuntu Jaunty Jackalope 9.04 will not load.
I have a Dual-boot setup so I can use Windows XP to send this distress signal.

I tried recovery mode at 3 different versions/levels (15,14 and 13) and tried to reinstall the packages. No luck. 
I tried all that I know to do. 
I don't have an image of Jack 9.04, but I will try find one to download and then burn and try that if it's the right thing to do... 
I'm am beside myself with self-hate.

Will anyone help me here?
I appreciate any help at all.

Rick (shobuz99)

---

### Post by Shobuz99 on 2009-09-17
Never mind.. I fixed it.
I found help from a different Ubuntu forum that suggested
a command during "recovery": 'sudo dpkg-reconfigure xserver-xorg'.
I ran that and then ran 'sudo apt autoremove' to clean up old pkgs. 
Then I selected the option to restore 40MB worth of packages 
and went through the re-install, booted to grub, 
then login/pw and oila' Ubuntu Jaunty is back..
I guess I learned my lesson. No more synaptic remove before I know what I'm removing! 
thanks for being there for me, anyway, just in case.

Rick (shobuz99)

---

### Post by jerrrys on 2009-09-18
[http://ubuntuforums.org/showthread.php?t=1158042](http://ubuntuforums.org/showthread.php?t=1158042)

---

### Post by Shobuz99 on 2009-09-18
> **jerrrys said:**
> [http://ubuntuforums.org/showthread.php?t=1158042](http://ubuntuforums.org/showthread.php?t=1158042)

jerrrys,
Thank you for posting this link, anyway. 
It's good to have in my Ubuntu 'fix' bookmarks folder.
I've compiled quite a collection.:)

I can't remember where the thread/post to the one I used, came from, now.
All I know is that it worked.

Thanks again.

Rick (shobuz99)

---

