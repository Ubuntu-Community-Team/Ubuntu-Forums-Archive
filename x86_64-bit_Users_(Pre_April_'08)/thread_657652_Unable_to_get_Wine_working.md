---
title: "Unable to get Wine working"
date: 2008-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by calinux on 2008-01-03
I'm having my all-time most frustrating time trying to get Wine to 
work on my Ubuntu 7.04 running on AMD64.

I try Synaptic, and the packages appear, but when I try to install 
them, I get an error that one of the packages depends on an 
inexistent package  (libwine and wine, or somehing like that).

I go to winehq.org and download the .deb, which does come 
in a x64 flavour --- ok, the download works, it's opened with 
the graphical package manager, and it does install.  But, as 
far as GUI usage, it is as if the package did not exist --- I double 
click on a Windows executable, and I get an error box telling 
me that it does not recognize the file.  I don't have a Wine menu 
under System Tools, etc.

If I try to run it manually from the CLI, I get the following error:

Warning: the specified Windows directory L"c:\\windows" is not accessible
Warning: the specified System directory L"c:\\windows\\system32" is not accessible

And nothing runs.

I tried running winecfg, and I do get a little configuration dialog, 
but no matter what I do in it, nothing happens and nothing works 
afterwards.

Some guidance, ideas, pointers?  please?

Thanks,

Carlos
--

---

### Post by BreathEasy on 2008-01-03
Ok, best we start from scratch, and I'll tell you the way I got it working, just so that I'll know how to help if anything goes wrong. :)

First, remove the version of wine you've got installed. Removing it using synaptic should be easy - if it doesn't appear installed in synaptic for some reason, type **sudo apt-get remove wine** in a terminal. Also, in a terminal, type **rm -rf .wine** to clear out any config settings.

Next, you should add the winehq repository instead of manually installing it yourself. Using the instructions from [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) I'll give you the lines to enter into a terminal (just copy & paste each line into the terminal):

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

sudo apt-get update

sudo apt-get install wine


Now that it's installed, **log out**. Log back in, you'll see the Wine menu entry. You might not have to log out to see the entry, but doing so gurantees it'll appear. In any case, go and run Wine Config from the menu, OR in a terminal, type **winecfg**. Let it run, then just click OK. Now you're configured. I can't gurantee that double-clicking on .exe files will work, I've seen times where it does and others where it doesn't, but at least running wine using the terminal should work.

---

### Post by Kilz on 2008-01-03
The orignl poster has wine installed, they got the deb package from wine and installed it. I just think they may not understand what wine is. [That will be made clear here.]("http://tghc.org/winefaq.html")

---

### Post by calinux on 2008-01-04
Thanks BreathEasy --- following your instructions, it did work! 

Actually, I did the equivalent through Synaptic  (went to Options -> 
Repositories -> 3rd Party -> Add, and added the two lines you 
indicated).  Then, search wine, select it, apply, and off I went !! 

I guess apt-get and Synaptic do some behind-the-scenes 
package configuration that I was missing  (I had run 
dpkg --configure, dpkg-preconfigure, -reconfigure ... The 
experience was quite frustrating, I tell you !!)

And BTW (for the other poster), no, it was not lack of understanding 
about what Wine is --- I have been using it and successfully running 
several Windows apps for quite a few years.  Still, thanks for taking 
the time to offer some advice!  (it might as well have been the 
solution I was missing!  :-))

Thanks,

Carlos
--

---

### Post by BreathEasy on 2008-01-04
Ah, good then. :)

---

