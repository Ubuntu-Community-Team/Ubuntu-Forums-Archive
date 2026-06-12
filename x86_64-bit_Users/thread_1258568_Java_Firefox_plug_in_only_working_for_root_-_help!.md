---
title: "Java Firefox plug in only working for root - help!"
date: 2009-09-05
forum: x86 64-bit Users
---

### Post by craig100 on 2009-09-05
Hi,

Ref: Ubuntu 9.04 x64

I've been at this for 3 or 4 days now solid.  I had a working java installation which stopped working noticed by The Firefox plugin failing. This was just after I installed a full JDK from sun to allow Visual Paradigm UML to work, at the same time I upgraded my netbeans 6.5 to 6.7.1. To cut a long story short, I've removed netbeans and visual paradigm uml and any java installation I had.  Then I installed the sun-java6 from synaptic and added symlinks to ~/.mozilla/plugins, /usr/lib/firefox/plugins, /usr/firefox-3.0.13/plugins and /usr/firefox-addons/plugins.

The result is that while about:plugins shows "Java(TM) Plug-in 1.6.0_14   File name: libnpjp2.so" when I go to [http://www.javatester.org/version.html](http://www.javatester.org/version.html) all I get is a grey box.  If I launch firefox from a terminal using sudo, then the same address shows the plugin working correctly.

I'm really tearing my hair out here as I desperately need to get my web development environment back up to get a project started.

As I'm a relative newbie to Linux any help or advice as to how to progress this issue would be greatly appreciated.

Craig

---

### Post by darco on 2009-09-05
First I am going to assume you read the stickies above on installing Java on a 64 bit system? Secondly running sudo firefox causes more problem than it fixes. I read you need to run it as gksudo firefox....
Whats the output of  ls -al /usr/lib/mozilla//plugins/

darco

---

### Post by craig100 on 2009-09-05
Hi Darco,

Yes you're right I did read the links.  Another one I read a few minutes ago explained the problems with running Firefox with sudo re: profile ownership problems.  New profile created, same problem with Java plugin however.  The output you requested follows:-

total 12
drwxr-xr-x 2 root root 4096 2009-09-04 00:14 .
drwxr-xr-x 4 root root 4096 2009-04-20 15:09 ..
lrwxrwxrwx 1 root root   37 2009-09-04 00:14 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   58 2009-09-03 14:26 libnpjp2.so -> /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/amd64/libnpjp2.so
lrwxrwxrwx 1 root root   43 2009-04-28 11:24 libtotem-cone-plugin.so -> ../../totem/default/libtotem-cone-plugin.so
lrwxrwxrwx 1 root root   42 2009-04-28 11:24 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2009-04-28 11:24 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2009-04-28 11:24 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   60 2009-09-04 00:09 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

Appreciate your time looking at this.

Craig

---

### Post by darco on 2009-09-05
When you run about plugins, do you see the IcedTea Java Web Browser Plugin? I see it installed on my system so I am wondering if this is what you need.
Also not to make things worse for you but you no longer need those npwrappers for flash as flash is now native 64.

darco

---

### Post by wojox on 2009-09-05
```
sudo chown -R $USER:$USER ~/.mozilla
```

Change it back to you.

---

### Post by craig100 on 2009-09-05
Hi Wojox,

Thanks but I already did that as it was in the link I read (sorry can't remember where it was now).

Hi Darco,

The IcedTea plug in works really badly with volano chat, which is just one of the java applets I use often, hence using the sun java from the repro.

The real reason I need to get this permissions thing sorted is that when I install NetBeans, I can only run that as root, which isn't right. There seems to be something common here in that only root seems to have access to java.

Craig

---

### Post by craig100 on 2009-09-06
Does anyone know how to progress fault finding this as I'm all out of ideas? Why is it only root can run the repro installed sun-6-java?

Any advice appreciated.

Craig

---

### Post by pointyblue on 2009-09-06
I had a problem similar to this after upgrading from Firefox 3.x to 3.5.

Couldn't find the cause of the problem, ended up removing both Firefox and Java completely from Synaptic. Believe I removed Ubuntu Resticted Extras from Add/Remove too... Then reinstalled Firefox (3.x) and Ubuntu Restricted Extras from Add/Remove. After that Java worked again. I know, it's more of a roll-back than a real solution to the problem.

Sometimes it'd be really neat to be able to make a "System Restore" like on Windows!

Don't know if you can use this, just thought I'd mention it since you're out of ideas.

---

### Post by craig100 on 2009-09-06
Thanks pointyblue,

Looking at my Add/Remove list I see that the "Sun Java 6.0 Plugin" is checked but greyed out so I can't uncheck it. I'm guessing it's restricted to the root user. Yet the "Sun Java 6 Runtime" is checked and can be unchecked. This is odd.

Craig

---

### Post by pointyblue on 2009-09-06
You should still be able to remove Java completely in Synaptic.

---

### Post by craig100 on 2009-09-06
I wasn't looking to remove it, it was just an observation to possibly lead to a clue as to what's happening. I only installed it yesterday from synaptic so I'm puzzled as to why it's only available to root.  Before yesterday I'd had the Sun JRE and JDK installed for months, manually from the Sun site and they were working. Then they stopped and became only available to root. So something has happened somewhere else, but what? It's a general thing, not just to do with Firefox.

This is why it's taken me a whole week to sort out. I mean 8 hours a day for 7 days. Would be quicker to do a total reinstall but I don't want to go back to Windows ways of doing things. It should be possible to fix this if only I can find someone who understands what's going on and has the knowledge to fix it.  I might have to pay someone to come here as I can't afford much more time out of production.

Cheers,

Craig

---

### Post by craig100 on 2009-09-06
Just tried to start the Java Console in terminal by issueing a "jcontrol". It only works if I issue "sudo jcontrol", otherwise I get this error:-

# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f57be63858f, pid=3882, tid=140012636223824
#
# JRE version: 6.0_14-b08
# Java VM: Java HotSpot(TM) 64-Bit Server VM (14.0-b16 mixed mode linux-amd64 )
# Problematic frame:
# C  [libc.so.6+0x3158f]  catgets+0x1f
#
# An error report file with more information is saved as:
# /home/craig/hs_err_pid3882.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/bin/jcontrol: line 135:  3882 Aborted                 ${java_home}/java -Djavaplugin.user.profile=${USER_JPI_PROFILE} -Xbootclasspath/a:${java_home}/../lib/deploy.jar ${_JAVA_VM_OPTIONS} com.sun.deploy.panel.ControlPanel

Craig

---

### Post by craig100 on 2009-09-06
Ok, I've sorted it!

Removed all java-6-sun stuff from synaptic.
Removed all residual java directories from /usr/lib and anywhere else I could find them.
Removed java path from $PATH in /etc/environment
Removed /etc/jvm alternatives file
Created directory /opt/java
Copied jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin to /opt/java and ran as sudo to install.
Created a simlink: ln -s /opt/java/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins

et viola, it works in firefox without being root.

However, please note it's the update 12 (latest is update 16) and it's "ea" i.e. "early access" so therefore experimental. But it's the only one that works for 64 bit Firefox.

Now to put in the latest JDK and see if I can get Netbeans to play nicely.

Thanks for all your patience.

Craig

---

