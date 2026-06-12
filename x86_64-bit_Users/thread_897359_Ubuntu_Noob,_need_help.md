---
title: "Ubuntu Noob, need help"
date: 2008-08-22
forum: x86 64-bit Users
---

### Post by nightwheel on 2008-08-22
First off, Hi I'm nightwheel. I'm new here. Today is the first time I have installed Ubuntu. I installed version 7.04 for 64-bit PC's to one of my 2 HDD's I have in this computer.

Now to the the problems and questions.

How do I get Ubuntu to allow me to take advantage of my screens max resolution which is 1280x1024? Does it help I use a Nivida 6150 LE video card?

Also, how do I navigate to the terminal? As from what i have seen, I have to get to the terminal to install stuff. 

And since I have used Windows all my life. Stuff like the questions and problems above confuses me. And I'm a very computer savvy person. At least when it comes to Windows. I'm a fish out of water when it comes to linux.

Anyways, can you guys help me?

---

### Post by sandysandy on 2008-08-22
for terminal see space bar ( panel) at top of desktop

applications-----> accessories---->Terminal

regards

---

### Post by cpetercarter on 2008-08-22
The tool to alter screen resolution is at

System > Preferences > Screen Resolution

---

### Post by Thelasko on 2008-08-22
> As from what i have seen, I have to get to the terminal to install stuff.

Not necessarily, posting terminal commands is just the best way to post information on the boards.  Also, many users prefer the terminal.

If you feel uncomfortable with the terminal, there are multiple ways to install software in Ubuntu.  The simplest one is to click on "Applications" and go to "Add/Remove Software."  That will provide you a list of software you can install, complete with descriptions and information about how many people use each piece of software.  Just click the checkbox next to what you want to install and click "ok." There is a lot more [information here]("https://help.ubuntu.com/7.04/add-applications/C/index.html").

---

### Post by nightwheel on 2008-08-22
Well I found the screen resolution thing right from the get go. The problem is I only have 2 options. Either 800x600 and 640x480. And I know my screen can take up to 1280x1024. So how do I set ubuntu to go up to 1280x 1024?

---

### Post by oldsoundguy on 2008-08-22
You have not mentioned your video card/chip set up.  That is required to get further help.
You may have to enable restricted driver support. (you will have to be on line for that and you will have to have all of the regular repositories enabled.)
OR .. if you are running NVidia or ATI:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
this is a third party install program for those cards that DOES work for most.  (I have used it MANY times with NO issues with NVidia .. some with ATI).

And here is a list of noob guides that are really invaluable for "tweaking and installing" items within the systems:

[http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=2Ku&q=+site:ubuntuguide.org+ubuntuguide&sa=X&oi=smap&resnum=1&ct=more-results](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=2Ku&q=+site:ubuntuguide.org+ubuntuguide&sa=X&oi=smap&resnum=1&ct=more-results)

---

### Post by cariboo on 2008-08-22
Go to System-->Administration-->Hardware Drivers, click to enable the restricted drivers. It will sown load the nvidia driver you need.

The reason they are called restricted drivers is that they are closed source drivers. I don't know it still does it, but at one time during boot up it would print a message that the kernel was tainted because of the closed source drivers :)

Jim

---

### Post by elmoosecapitan on 2008-08-22
This is about the fourth time I have done this today, but here are some terminal tutorials:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://nsit.uchicago.edu/docs/os/unix/](http://nsit.uchicago.edu/docs/os/unix/)
[http://linuxcommand.org/](http://linuxcommand.org/)


cheers

---

### Post by nightwheel on 2008-08-24
> **oldsoundguy said:**
> You have not mentioned your video card/chip set up.  That is required to get further help.
Opps sorry, I have a Nvidia Geforce 6150 LE integrated card.

And I used that Nvidia Fix you gave and it worked. Unfortunately, I learned the Hard Way what a certain update for Ubuntu 7.04 could do for computers with the Nvidia drivers installed. Thankfully my main 120gb hard drive Has Windows XP on it still. And that HDD will continue to have xp installed.

So today, I installed the newest version of Ubuntu, Hardy Heron to my other 40gb HDD. 

But before I go get that fix again. Is there any updates for Hardy Heron that can make computers with the Nivida drivers installed not boot correctly?

---

### Post by cjm5229 on 2008-08-24
Instead of using 3rd party scripts to install drivers, use the Hardware Drivers Manager. That way when there is a Kernel update it will also update the restricted-modules for the kernel. Just click enable on the HDM and let it install, then reboot when it tells you to.

---

### Post by nightwheel on 2008-08-24
> **cjm5229 said:**
> Instead of using 3rd party scripts to install drivers, use the Hardware Drivers Manager. That way when there is a Kernel update it will also update the restricted-modules for the kernel. Just click enable on the HDM and let it install, then reboot when it tells you to.

OK I did that I downloaded the drivers. Restarted, but for some reason. Ubuntu is not using the driver for my card. I'm still stuck with 800x600 resolution. Where did I go wrong?

---

### Post by Sef on 2008-08-24
> OK I did that I downloaded the drivers. Restarted, but for some reason. Ubuntu is not using the driver for my card. I'm still stuck with 800x600 resolution. Where did I go wrong?


Have you gone back into System > Preferences > Screen Resolution

---

### Post by cjm5229 on 2008-08-26
You say you have Ubuntu 7.04 installed. It's been so long since I ran Feisty I don't remember all the details, but, I think I had to bring up the /etc/X11/xorg.conf and change the resolutions under devices. If you upgrade to 8.04 it may solve a lot of your issues.

---

