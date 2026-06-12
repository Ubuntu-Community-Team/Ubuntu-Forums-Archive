---
title: "Weird start up HELP!"
date: 2009-05-04
forum: x86 64-bit Users
---

### Post by ElevenWarrior on 2009-05-04
hello, I'm running Juanty 9.04 (64-bit) and this is the problem I'm having.
 when I start up jaunty, it for some reason loads firefox, and Pidgin. 
I don't know why this is, there not on the startup applications.
HELP!:confused:

---

### Post by astabeno on 2009-05-04
So they are not in checked in the System -> Preferences -> Startup Applications.  Also check the if 'Automatically remember running application when logging out' under the options tab is checked.

---

### Post by ElevenWarrior on 2009-05-04
yep I made sure. I checked it once, but then I un-checked it b/c of what it did. They still start up.

---

### Post by gamblor01 on 2009-05-04
Are you running gnome?  If so, check for the file ~/.gnomerc and see if it contains anything.  If it contains commands to launch firefox and pidgin, then that's likely the issue.  Adding commands to ~/.gnomerc prompts gnome to execute those commands after a successful login.  So for example, I put a call to a shell script that waits 20 seconds and then launches conky (for some reason if conky starts before compiz it has issues, so I just forcefully delay it by 20 seconds to ensure that compiz has started fully).

Otherwise, you'll probably have to start looking into the startup scripts in /etc/init.d.  Well -- most likely you need to look in /etc/rc*.d.  Usually the scripts in there are symbolically linked to the scripts in the /etc/init.d directory.  So when the system hits runlevel 1, it starts executing the scripts in rc1.d.  When it gets to runlevel 2, it starts executing the scripts in /etc/rc2.d and so on.

Scripts that have the S## suffix tell the system to start the process.  Scripts with the K## suffix tell the system to kill the process.  The numbers go in order such that a script with S01 would start before S02, which would both start before a script with S03, and so on.

Here's a decent link about startup scripts:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html)

---

### Post by ElevenWarrior on 2009-05-06
thank you! I think it solved the problem

---

