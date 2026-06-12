---
title: "Installed kubunut-desktop now firefox will not work"
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by suyixiang on 2005-11-22
I am running Ubuntu Breezy amd64.  I wanted to check out kubuntu so I installed kubuntu-desktop.  apt-get install kubuntu-desktop.  Since I did that every time I open firefox it hangs and never opens a web page.  I can use Konqueror and it works fine.  Firefox will work, but very slowly if Konqueror is open.

When I put in a DVD I get an error message saying cannot read menu information, or something like that.

Please help

---

### Post by nalmeth on 2005-12-01
The DVD problem probably has to do with codecs or something like that. If you don't know how to install them, just search these forums, there are some helpful walkthru's.
Did firefox work fine in Gnome? I'm not familiar with your problem, so the only thing I can suggest is to sudo apt-get remove kubuntu-desktop, and if you still want KDE, maybe try sudo apt-get install kde.
XFCE4 is pretty killer too, but I'm a KDE man.

---

### Post by nalmeth on 2005-12-01
actually another idea..
Since you won't be able to use flash with firefox in 64-bit anyway, follow this guide to setting up a 32-bit chroot environment:
[http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit)
except everywhere it says "hoary" replace with "breezy" including most importantly when adding to sources.list.
you can basically just copy and paste all the commands (or highlight and click middle button) and everything should set up properly.
when you're done all this, open up a new terminal and type:
*dchroot -d*
*sudo apt-get install firefox flashplayer-mozilla*
*exit* 
(this will take you out of chroot, back into 64-bit)
get rid of 64-bit firefox with 
*sudo apt-get remove firefox*
then in the same terminal:
*sudo ln -s /usr/local/bin/do_dchroot /usr/bin/firefox*
this will create a symbolic link so that when you run firefox in a terminal, or if you have a shortcut on your toolbar or desktop, it runs 32-bit firefox. 

Of course, after all this you might still have the same problem, but its worth a shot. If it works you'll have a working firefox with flash.

Give it a shot if you have time

---

