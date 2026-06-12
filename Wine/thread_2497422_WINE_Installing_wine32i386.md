---
title: "WINE Installing wine32:i386"
date: 2024-05-03
forum: Wine
---

### Post by mark bower on 2024-05-03
I successfully used WINE to run ACAD2000 (32bit) and Irfanview (64bit) for many many years. My SYNAPTIC PKG MGR installations of it were successful in '21, '22, and '23. I am now trying to install WINE into Ubuntu-MATE 2024.04.  [I much prefer the simplicity of using synaptic or .deb over PPA installation if possible].

I have installed i386 and verified it is present with dpkg –print-foreign-architectures. 
I installed wine-stable and wine via synaptic.  At this point, all should be good - it's not.

Some diagnostics:
mark@mark:~$ wine
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32:i386"
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
mark@mark:~$ wine --version
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32:i386"
wine-9.0 (Ubuntu 9.0~repack-4build3)

Entry that supposedly will do the trick – but doesn’t
mark@mark:~$ sudo apt-get install wine32:i386
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package wine32:i386
mark@mark:~$ 

What am I doing wrong or what do I need to do to get wine32:i386 installed?

---

### Post by Claus7 on 2024-05-05
Hello,

have you checked this out? [https://stackoverflow.com/questions/62371617/wine32-is-missing-issue-in-ubunt-20-04-as-root-please-execute-apt-get-insta](https://stackoverflow.com/questions/62371617/wine32-is-missing-issue-in-ubunt-20-04-as-root-please-execute-apt-get-insta)

Regards!

---

