---
title: "Wine not finishing installer, and not running installer"
date: 2015-05-26
forum: Wine
---

### Post by mattig89ch on 2015-05-26
Hidy ho all,

I'm trying to get a windows based program to install and run using WINE.

When I startup the installer via the gui it says the installer was interupted and no changes were made to the computer.

When I fire up the installer via the cli it says I don't own or have rights to the folder the installer is in.  I have tried moving the installer around via the gui, but the results are always the same.  I don't own /home/user/.wine folder.  I have tried taking ownership of this folder via the cli with the "sudo chown -R user /home/user/.wine" command, but I keep getting the same error message.

I installed wine via the software center if it helps.

Edit: I'm currently doing this on a virtual machine.  I wanted to see if this was possible.

---

### Post by Bucky Ball on 2015-05-26
*Thread moved to **Wine**.*

---

### Post by mattig89ch on 2015-05-26
Thanks, did not realize there was a forum specifically devoted to WINE.  Good to know.

---

### Post by Bucky Ball on 2015-05-27
All good. Was a toss up between Wine and [this]("http://ubuntuforums.org/forumdisplay.php?f=93"), but your issue seems to be more Wine-centric.  

Good luck. If you don't get any attention for a reasonable amount of time (say twelve or more hours), feel free to 'bump' the thread by simply posting 'bump'. We are an international forum spanning many time zones so understand that the person that can help you may not have gotten here yet. Bumping will take the thread to the top of the new posts again (any post on the thread will do the same). Better than just posting 'bump' though is if you have been trying to sort things out, update the thread with what you've tried and where you're at with it now. ;)

---

### Post by mattig89ch on 2015-05-27
I actually think this post will help a bit.

I'm not trying to run a game.  This is an RMS program, we use for our clients.  Given how stable and reliable Linux is, I would think it would be better for our clients if we can get a Linux box to run this software.

It might not be possible, but we never know until we try.

---

### Post by Bucky Ball on 2015-05-27
> **mattig89ch said:**
> 
It might not be possible, but we never know until we try.

Indeed, and these forums are a good place to get help trying. The more workarounds and fixes we can come up with to get more apps working on Linux the better. ;)

---

### Post by mattig89ch on 2015-06-02
I'm bumping this thread

---

### Post by GnudeNoob on 2015-06-03
What about trying to install some other Windows program...for example, something simple like Notepad2. If that works it would at least tell you your Wine is ok.

Have you looked in the WineHQ app database to see if your app is listed there?

---

### Post by mattig89ch on 2015-06-03
I haven't looked no, but there is a reason for that.  This program isn't a common one that everyone has access too.  Its a program that acts like a cash register, giving functionality to recipt printers, cash drawers, scanners, and pretty much anything else you have ever seen a cash register do.

I'll have to see about finding where to download notepad 2, and trying to install that.

---

### Post by Bucky Ball on 2015-06-03
> **mattig89ch said:**
> I haven't looked no, but there is a reason for that.  This program isn't a common one that everyone has access too.

All the more reason for it not to work in Wine. If you really want to know, check WineHQ and save yourself some time. The help we can give at this end is limited if we have no idea what it is you're attempting to get working with Wine.

If you desperately need this Windows program, can't get it working in Wine, and there is no alternative in Ubuntu, as you seem to be au fait with virtual machines, why not install a Windows vm and install your app in that?

---

### Post by GnudeNoob on 2015-06-03
> **mattig89ch said:**
> 

I'll have to see about finding where to download notepad 2, and trying to install that.

You can get the install for Notepad2 from the developer [FlosFreeware]("http://www.flos-freeware.ch/notepad2.html"). Download the 'setup', either x86 or x64, and you'll have the .exe for Notepad2. If that installs ok then the problem is most likely not with Wine but with your program, although it could also be some interaction that involves both.

My .wine folder says its owner is [COLOR="#0000FF"]Me[/COLOR] (Right-click folder, Properties, Permissions tab) and my access is 'Create and Delete', so inside that folder I can create stuff, eg another folder...is that how yours is working?

---

### Post by GnudeNoob on 2015-06-03
> **mattig89ch said:**
> 
I'll have to see about finding where to download notepad 2, and trying to install that.
Actually Notepad2 looks like not a good example, it wouldn't install on my Wine.

Try [TuxPaint]("http://www.tuxpaint.org/download/windows/") instead, I just tried that and it installed and runs fine.

---

### Post by mattig89ch on 2015-06-11
Sorry for the lack of updates on this topic.  Last week or so had me running around like a chicken with its head cut off.

I am still interested in trying to get this software to run properly.  The WINE forums would be better for trying to figure this out?

Also, I haven't tried any other .exe programs yet, but I will try to give them a go.  Were you seeing the same error message when you tried to run notepad 2, that I saw?  The one that said the installer was interrupted and no changes were made.

---

### Post by Bucky Ball on 2015-06-11
Read post #12 re. notepad. Wouldn't hurt to post in the Wine forums as well.

---

### Post by mattig89ch on 2015-06-11
I just came back to post an update, that reply was much faster then I was expecting.  I'm able to run notepad2.exe, though there is no installer that comes up.  It comes up simply as a text editor, which is how it works on my windows box as well.  Not sure what to make of this development.  I used Q4Wine if that makes any difference.

I'll also go and make a post over in the wine forums as well, but I'd like to try and keep this topic going.

Edit: didn't mean to double post.  Would you (or any moderator) mind deleting that second post?  I don't see a way to do it myself, otherwise I'd just take care of it.

---

### Post by Bucky Ball on 2015-06-12
Removed as requested. :)

---

### Post by mattig89ch on 2015-06-12
many thanks.  I've started narrowing down the problem.  This is the topic over on wines forums: [https://forum.winehq.org/viewtopic.php?f=8&t=24767&p=100593#p100593](https://forum.winehq.org/viewtopic.php?f=8&t=24767&p=100593#p100593).

I'm getting a 1603 error when I run the installer.  I've found a few people having this trouble from wine, but I can't see any of them solving this problem.  Thats a little disconcerting.

Thankfully this isn't really a big deal for me, but i'd still like to try and get the program to run.

Edit: Ok, so the good people over on the wine forums say I'm running a version of wine thats a couple years old.  There is a more recent version I should be able to download, but I have to add that version to the software center by hand.

Now...how do I go about doing that?

because trying to do it this way:
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) 14.04.02 main 
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) 14.04.02 main 

Gives me the following output:

username@matt-vboxubuntu:~$ sudo deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) 14.04.2 main
sudo: deb: command not found
username@matt-vboxubuntu:~$ deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) 14.04.2 main
No command 'deb' found, did you mean:
 Command 'debi' from package 'devscripts' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'derb' from package 'icu-devtools' (main)
 Command 'dwb' from package 'dwb' (universe)
 Command 'debc' from package 'devscripts' (main)
 Command 'deb3' from package 'quilt' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
username@matt-vboxubuntu:~$

---

### Post by mattig89ch on 2015-06-15
I'm bumping this thread.  Should I ask that question in a new thread somewhere else?

---

### Post by howefield on 2015-06-15
The lines that you appear to be pasting into the terminal should be appended to your sources.list file.

Probably easier just to go to the winehq page and follow the instructions ? I'd uninstall whatever version you have first.

[https://www.winehq.org/download/ubuntu](https://www.winehq.org/download/ubuntu)

---

