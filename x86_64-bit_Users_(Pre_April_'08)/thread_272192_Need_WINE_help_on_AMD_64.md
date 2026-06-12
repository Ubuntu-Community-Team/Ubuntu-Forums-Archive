---
title: "Need WINE help on AMD 64"
date: 2006-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by eric.stone on 2006-10-05
I've installed WINE but can't run winecfg - which I believe is necessary to get it up and running.  When I type "wine" into a terminal, I get the following:

eric@Eric-LinuxBox:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
eric@Eric-LinuxBox:~$


When I type "winecfg" into the terminal I get the following:

eric@Eric-LinuxBox:~$ winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
eric@Eric-LinuxBox:~$

Can anyone help?  My ultimate goal is to run "Business Plan Pro" a MS prog.

Thanks!](*,)

---

### Post by kuja on 2006-10-05
Ewww, such an ugly error :o How did you go about installing wine? What version did you install?

---

### Post by eric.stone on 2006-10-05
Followed Kilz May 31st post.  If I should start over, how do I get rid of the old WINE?
E

---

### Post by acordes on 2006-10-05
I also had this problem once and it is related to using generic video card drivers. Try installing the appropriate ones - the 'glxinfo' command should tell you whether you have everything up and running or not.

---

### Post by Kilz on 2006-10-05
> **eric.stone said:**
> Followed Kilz May 31st post.  If I should start over, how do I get rid of the old WINE?
E

If you followed my howto, you should already have the solution to this problem. It is listed under the common errors.

---

### Post by JAPrufrock on 2006-10-06
I had a similar problem.   If Kilz's suggestion doesn't work, for a temporary fix try turning off glx by running from the terminal “sudo dpkg-reconfigure xserver-xorg” and then following the instructions. When you get to the x-org server modules section, de-select glx It's possible that your 3d video accelerator is not installed.  Note:  you may still get a glx error message, but Wine should run afterwards.

---

