---
title: "Terminal?"
date: 2006-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ATOMIC2 on 2006-05-22
Hello, my name is Christopher van Dal. I've been very interested in Linux for a while now, whether it be researching or testing different distributions and now i've finaly decided to go along with, Ubuntu! :KS 

So far, the only problem i've encountered is learning how to compile. I'm assuming it's done via some form of Terminal/Command Line? My problem is, I cannot find it! :confused: The following link is a tutorial for setting up an application which is required for me to access the internet.

[http://bpalogin.sourceforge.net/index.php?page=tutorial](http://bpalogin.sourceforge.net/index.php?page=tutorial)

If you skim through the tutorial you'll notice where it wants certain code to be entered, but as I stated earlier, I cannot find any form of Terminal/Command Line to enter the data.

I have however tried the following: Applications -> Add Applications -> More Programs -> Terminal

Before installing the Terminal it's description was, "This program is not currently installable. It should be available in the 'Universe' section of the repository."

So, in a nut shell, if somebody could be kind enough to direct me to the Terminal/Command Line or whatever else I may use to input the code from the tutorial it would be much appreciated as i've been awake to long trying to figure it out myself ](*,) 

Regards,
Christopher van Dal.

---

### Post by olsonar on 2006-05-22
it should just be under Applications -> Accessories -> Terminal. if its not there, hit Alt + F2 to bring up the "run" dialog and type gnome-terminal.

---

### Post by mynimal on 2006-05-22
You have that bar on top, right? Applications -> Accessories -> Terminal. :) It's installed by default.

---

### Post by ATOMIC2 on 2006-05-22
Ohh now I feel very stupid! :rolleyes: I must of missed it last night since I was tired. Never the less I have found it! Thank you both very much, however, I now face another issue while using Terminal. In order to stop, start, restart and check the status of my connection to my ISP, I need to run a file, "bpalogin" wich is located in, /etc/rc.d/init.d. But when I open Terminal and type, "/etc/rc.d/init.d/bpalogin stop" I am getting this message...

"/etc/rc.d/init.d/bpalogin: line 13: /etc/rc.d/init.d/functions: No such file or directory"

Since this particular application is for, Australian users who use Bigpond Cable as their ISP I don't expect anyone else to go out of their way to help me resolve it, but it would be greatly appreciated.

Regards,
Christopher van Dal.

---

### Post by olsonar on 2006-05-23
well, on my system there is no "/etc/rc.d" directory. instead there's a bunch of ones like rc0.d, rc1.d, etc. I would say just open up nautilus and browse those folders, and /etc/init.d/ as well, to find bpalogin. then use the path you found it at.

---

### Post by llamakc on 2006-05-23
When you have a package already installed you can check from the command-line which files were installed with:

dpkg -L nameofpackage

 Here's the list of stuff from packages.ubuntu.com:


etc/bpalogin.conf					    [net/bpalogin]("http://packages.ubuntu.com/dapper/net/bpalogin")
etc/init.d/bpalogin					    [net/bpalogin]("http://packages.ubuntu.com/dapper/net/bpalogin")
usr/sbin/bpalogin					    [net/bpalogin]("http://packages.ubuntu.com/dapper/net/bpalogin")
usr/sbin/bpalogin-configure				    [net/bpalogin]("http://packages.ubuntu.com/dapper/net/bpalogin")
usr/share/doc/bpalogin/README				    [net/bpalogin]("http://packages.ubuntu.com/dapper/net/bpalogin")
usr/share/doc/bpalogin/README.Debian			    [net/bpalogin]("http://packages.ubuntu.com/dapper/net/bpalogin")
usr/share/doc/bpalogin/changelog.Debian.gz		    [net/bpalogin]("http://packages.ubuntu.com/dapper/net/bpalogin")
usr/share/doc/bpalogin/copyright			    [net/bpalogin]("http://packages.ubuntu.com/dapper/net/bpalogin")
usr/share/man/man8/bpalogin-configure.8.gz		    [net/bpalogin]("http://packages.ubuntu.com/dapper/net/bpalogin")
usr/share/man/man8/bpalogin.8.gz			    [net/bpalogin]("http://packages.ubuntu.com/dapper/net/bpalogin")

So you can start or stop that program from /etc/init.d/bpalogin

Hope it helps.

---

### Post by FluffyElmo on 2006-05-23
*bpalogin* is available in the Ubuntu repositories. From the top menu run *System->Administration->Synaptic Package Manager*. Once in Synaptic try searching for *bpalogin*, if it's found right click it, select install and then click the *Apply* button in the toolbar.

If you don't find it you may have to enable the Universe and/or Multiverse Repositories. In Synaptic go to *Settings->Repositories*, click the *Add* button in the dialog and then select *Universe* and *Multiverse*. Click OK until you're back in Synaptic proper, then click Reload. When it's done you should be able to find and install *bpalogin*.

It sounds a little complicated, but you can get the vast majority of software you'll need from withing Synaptic. Note that I can't test the *bpalogin* since I'm not in Australia but if you have problems with Synaptic and what-not I may be able to help.

Good Luck and Welcome to Ubuntu!

---

