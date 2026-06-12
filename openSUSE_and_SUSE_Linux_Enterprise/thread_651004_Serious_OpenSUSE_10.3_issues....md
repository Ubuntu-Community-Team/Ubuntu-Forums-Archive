---
title: "Serious OpenSUSE 10.3 issues..."
date: 2007-12-27
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Moonfrost on 2007-12-27
Reply with quote Edit/Delete this post Delete this post
Post Serious OpenSUSE issues... 
Well, it all started when I wanted to update KDE from 3.5.7 to 3.5.8 following step-by-step instructions from the official OpenSUSE site. Of course I had to restart the PC to see the changes, I restarted and I see a non-graphical login screen? ok, I thought something happened but after logging in X would start...I WAS WRONG! X wouldn't start! and since I'm kinda new to SUSE I didn't know any special commands except reboot which usually works on every OS I have used so far...I rebooted and still nothing! it told me the Nvidia kernel couldn't be loaded!!! what the h***? I didn't modify anything relating to the Nvidia driver! so I went and re-installed (fortunately I have all recent changes on the previous distro I was using backed up).

After re-installing I did all the usual stuff and such and went and re-installed the Nvidia driver. Ok good so I logout to restart X as told before on the official OpenSUSE site (which worked like a charm before) and I don't see a graphical user interface to log back in again! so I just went and restarted and still the same!!! in the error screen there were a lot of fatal errors! one of them said the Nvidia kernel was not found or something like that! what the h***? I had just installed it like before!!...so here I am, I re-installed (again) the OS and everything is working fine but I'm afraid to change anything. I want to install the Nvidia driver and enable Compiz again but I don't know...and I'm definitely not trying to update KDE anymore!

Does anybody know what the problem could be? could anybody help me with suggestions or anything? and I'm open to questions regarding what else I could've done that was probably wrong on my side...

EDIT: Another error was "no screens found: 93" or something like that...also it said that runlevel 5 was skipped, and everytime I typed "startx" it gave me this whole list of errors including fatal errors like I mentioned and the errors I just discribed.

EDIT #2: This is the link with the instructions to update KDE [http://en.opensuse.org/KDE/Upgrade](http://en.opensuse.org/KDE/Upgrade)
Let's see if I did something wrong...pretty sure I didn't miss anything though...is there another method?

EDIT #3: Ths is the link to installing the Nvidia drivers (note that this method [which I'm sure it's the only one out there] worked like a charm before and Compiz was up and running in no time perfectly)...[http://en.opensuse.org/NVIDIA](http://en.opensuse.org/NVIDIA)

---

### Post by RedDwarf on 2007-12-27
I don't think the problem had nothing to do with the KDE update. Probably the kernel or the NVIDIA driver were also updated...

If you try again and have the same problem we can help you if you give enough information:
- rpm -qa | grep nvidia
- rpm -qa | grep kernel
- lspci
- /etc/X11/xorg.conf
- /var/log/Xorg.0.log

---

### Post by Moonfrost on 2007-12-27
> **RedDwarf said:**
> I don't think the problem had nothing to do with the KDE update. Probably the kernel or the NVIDIA driver were also updated...

If you try again and have the same problem we can help you if you give enough information:
- rpm -qa | grep nvidia
- rpm -qa | grep kernel
- lspci
- /etc/X11/xorg.conf
- /var/log/Xorg.0.log

Ok...I should put this in the command line if the same thing happens? or should I go now to the directories? unless you want me to put this on a terminal and show you the output...

---

### Post by RedDwarf on 2007-12-27
> - rpm -qa | grep nvidia
 - rpm -qa | grep kernel
 - lspci
Are commands to execute in the command line. We need his output.

> - /etc/X11/xorg.conf
 - /var/log/Xorg.0.log
Are files. We need to know what there is in them.


Right now these will give the results of a working configuration, so they are of no help. But if you have the problem again...

---

### Post by Moonfrost on 2007-12-27
> **RedDwarf said:**
> Are commands to execute in the command line. We need his output.


Are files. We need to know what there is in them.


Right now these will give the results of a working configuration, so they are of no help. But if you have the problem again...

That's what I thought...I will have to try again and it it happens and I happen to fix it then I'll check them out and see what happens...thanks!

---

