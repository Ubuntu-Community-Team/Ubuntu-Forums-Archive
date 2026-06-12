---
title: "Is their a Antiviris for Ubuntu"
date: 2007-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by N4PSN on 2007-03-01
Hi, I am a 4 day old newbe. Is their a antiviris for Ubuntu? Do I need a antiviris?

Thanks, N4PSN

---

### Post by Stemp on 2007-03-01
An antivirus ? what for ? Forget it, you're not using a Microsoft product anymore ;)
A firewall is enough

---

### Post by userundefine on 2007-03-01
No, you do not need an antivirus in Linux.

---

### Post by solar george on 2007-03-01
> An antivirus ? what for ?
You will find that there are some antivirus programs available for Linux, but all that they do is scan for windows viruses, for example on a mail server to prevent viruses getting through to the vulnerable window$ machines

---

### Post by floke on 2007-03-01
You only need an antivirus if you are sharing files with a Windows box.
You can use Clamav (there is a GUI frontend called Klamav); a good firewall is firestarter which is in the repos.
You can do an online test here... 

[http://www.grc.com/default.htm](http://www.grc.com/default.htm)

to see how secure you are online with Linux (try it, you'll like the results!)

---

### Post by Stemp on 2007-03-01
That's why I said «what for ?»
You don't need actually an Antivirus for Linux, but you may use it for checking Windows mails or files ;)

---

### Post by schizoman on 2007-03-04
Wait, wait, wait....  I accept that almost all viruses are *currently* written for Windows, but surely there are viruses out there that attack Linux, as well?  And as Vista causes more and more users (corporate AND home) to switch to Linux, aren't these viruses going to get both, more virulent and more common?

I'm still a newbie to Linux, but where am I off the mark?

---

### Post by aa.ivanov on 2007-03-04
In short: 
All depends on the device standing in front of the keyboard ;)

The long answer:
Yes, there are a couple of viruses for Linux. Almost all of them are lab pets. There are some worms I know of, but they are more interested in servers - databases etc. 
Yes, you're right with the advance of the migration toward linux, the interest in writing "viruses" for linux will increase.

There are some issues in front of any virus writer though:
1. Linux is still not that well integrated. One of the greatest strengths and a major weakness in windows is the integration between the applications - the office, the outlook, the adress book, the operating system.
2. Linux is a very diverse system. There are two major desktop environments, at least half a dozen smaller projects, environments, window managers; a handful of command line interpreters; a bunch of scripting languages. While Windows works almost entirely on x86 processors, linux can work for a variety of processor architectures. For almost any task a couple of applications exist. In some areas we have a winner, but in some - we don't. Just the same with system libraries, that provide the routine procedures that a program needs - sometimes there is more than one library capable of doing the job. Finally every Linux distribution makes choices for its own what environment, libraries, shells etc. to include and what settings to set by default.
3. Linux comes with much more sensible default settings by default. Well... mostly. One example - in windows when you create a user - (s)he has administrator privileges by default. In linux users don't have such privileges. I hear this particular issue is planned to change with Vista (finally).

No, windows-style viruses are not a threat at this moment and I don't expect them to be in the near future. Rootkits are the issue that I consider dangerous for linux users. When migrating from the windows world people are looking for linux versions of their favorite programs or at least something that looks and feels like them. If they don't find them in the official repositories of their distro - they go for the 'google' option. I think it's much easier to allure a linux user install a pice of code than to try brute force attack against linux.

My personal opinion is that both linux and windows can be as secure as you make them. My computer at work runs WinXP and for the last 2 years I have not had issues with viruses, spyware, etc. My home computer used to run linux for me (now it runs linux for my parents), and my laptop is running linux. No issues for the last 4 years besides one the one time when I have erased my partition table, but it was my fault indeed.

---

### Post by omrsafetyo on 2007-03-04
One of the advantages of linux - and especially so in Ubuntu is that by default, you are forced to log in as a user other than root - and root is really the only account that can do any system critical damage.  In Ubuntu, you simply can't login as root without effort.  You must use sudo - and that only gives a virus about a 5 minute window to execute without having to know a password.

Sure there are viruses - but as said above, just because linux is so diverse, virus protection is really a moot point.  This is the reason that I switched 10% to linux.  I am sick of my windows box continually dying because of viruses.

OS/X is written off some version lof linux ( I forget which) - and mac posted almost as many security patches last year as m$ did for XP.  Why?  Because although there are less people targeting OS/X, its still extremely standard - and tehrefore an easy target.  This simply isn't the case with linux - because although they have to follow a specific filesystem, etc. to be considered UNIX, it is just far too diverse.

---

