---
title: "SMP   for amd 64 bit dual sore? cant see 2nd core"
date: 2006-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by retep57 on 2006-03-12
how do i get SMP running?  i have just gut a dual core amd  but alas ubuntu only sees one core? any ideas? or do i switch to another distro??

---

### Post by fimbulvetr on 2006-03-12
What output does "uname -a" give you?

---

### Post by Sutekh on 2006-03-12
You need to install a smp kernel.

Are you running the AMD64 version of Ubuntu?

You can install a smp kernel using
```
sudo apt-get install linux-amd64-k8-smp
```
To get the latest smp kernel.  When you reboot you should have the option of booting your original kernel and the newer one.


If you are running the 32bit version of Ubuntu, install the k7-smp kernel (close match to the k8 )
```
sudo apt-get install linux-k7-smp
```

---

### Post by retep57 on 2006-03-12
Linux ubuntu 2.6.12-10-amd64-generic #1 Mon Feb 13 12:14:05 UTC 2006 x86_64 GNU/Linux

---

### Post by retep57 on 2006-03-12
sudo apt-get install linux-amd64-k8-smp  this seemed to download and install, thanx for your help,  i then ran benchmarks within my worldcommunitygrid program but it can only see one core even now.. do i have to reboot, sorry am total newbie
basically this machine is devoted to the wcg  anti cancer anti aids etc   distributed computing  work.. thanx for your help, this is encouraging

---

### Post by Sutekh on 2006-03-12
Yar you have to reboot, when the GRUB menu comes up you should be able to choose to boot with the new k8-smp kernel.  The old (non-SMP) kernel will still be installed, should you ever want to boot using that.

Try 
```
cat /proc/cpuinfo
```from the terminal.  You should see both cores.

---

### Post by retep57 on 2006-03-12
cat /proc/cpuinfo
eter@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2000.124
 hmmm i am getting excited , than x for help  will reboot as u recommend then  choose the grub thing,, ps this is all new to me, amzing to get this far with minimal knowledge, i am "standing on the shoulders of giants" ie  could not do this with out help

---

### Post by Sutekh on 2006-03-12
Ok well when you reboot and choose the k8-smp kernel, cpuinfo should have two entries like the one you have now, the second one should have processor : 1

BTW I have a X2 3800 too

---

### Post by retep57 on 2006-03-12
wow this is amazing, a few lines of intelligent help from you has  been worth hrs/ days of struggle. i now have 2 cores running  the world community grid health research stuff ( btw consider joining to help human health  works as screensaver sort of thing, in background while do other stuff, if you do  consider join our team vulture central) i digress, thi sis absolutely amazing , the computing power has just doubled YAY indeed, i cant thank you enough, btw i  even sent out for a disk   that will go airmailuk to australia (here)   but i did want to stay with ubuntu cos that is the only reasonalbe one i have  played with before  even though just a day or so.. cheers again

---

### Post by Sutekh on 2006-03-12
Your welcome, makes a huge difference doesn't it?  Can you post a link to the research project?

---

### Post by retep57 on 2006-03-12
[http://www.worldcommunitygrid.org/index.jsp](http://www.worldcommunitygrid.org/index.jsp)
is my favourite

[http://www.worldcommunitygrid.org/ms/team/viewMyTeam.do](http://www.worldcommunitygrid.org/ms/team/viewMyTeam.do)
is the team i have joined, you get points but it is just a bit of fun  and  sort of a measure of work done

[http://distributedcomputing.info/projects.html](http://distributedcomputing.info/projects.html)

gives a list and links to many other projects in case your interests lie elsewhere... basicaly   these  chop up big projects into small piecs and give them out to   hundreds of thousands of   users  which add up to  superdooper computer, some just download work units then upload from tiem to time.  i like to be on 24/7  or as i now say 96/7 as i now have 4 cores  (thanx to you) running fulltime ( in the background)  fantastic

---

### Post by Sutekh on 2006-03-12
Cheers! I will check those out when I finish work

---

### Post by retep57 on 2006-03-12
[http://www.worldcommunitygrid.org/index.jsp](http://www.worldcommunitygrid.org/index.jsp)

---

### Post by retep57 on 2006-03-12
there are many other  projects around see [http://distributedcomputing.info/projects.html](http://distributedcomputing.info/projects.html)  

[http://www.worldcommunitygrid.org/ms/team/viewMyTeam.do](http://www.worldcommunitygrid.org/ms/team/viewMyTeam.do)  
is the team i  have joined. points just a bit of fun and a way to measure contribution to various projects,  the one i am with  has over 100,000 users and  is currently doing 2 diff projects but they aim for even more soon, the human genome porject was the basis for the human proteome project etc etc  fight cancer   aids other diseases with a virtual superdooper computer ( works in the background)  now i have 3 computers with  the dually now having  2 cores  running thanx to you, keep up the good work, btw u are laready contributing towards human health research by proxy by intellingent and most usefull  information  and tips, again i thank you

---

### Post by Sutekh on 2006-03-12
Okay thanks again for the info.  Thanks for the kind words, I'm sure someone else would have had the answer too, you pick this stuff up very quick.

---

### Post by retep57 on 2006-03-12
just basically cutting and pasting your  script,  borrowing your brains cos is all new too me..

---

### Post by Sutekh on 2006-03-12
[QUOTE=retep57]just basically cutting and pasting your  script,  borrowing your brains cos is all new too me..[/QUOTE]
 - Well I think a simple explanation is in order (and some helpful links)

```
sudo apt-get install linux-amd64-k8-smp
``` - As I said before installs the SMP kernel.  I thought I'd explain the command a bit better.

 - The main part of that command is **apt-get**.  Apt-get is a very powerful tool for dealing with software in Ubuntu.  In Ubuntu apt-get draws on large online 'repositories' that contain pretty much any application or package you could need for your system.  The locations of these repositories are specified in the file /etc/apt/sources.list.

 - When the command **apt-get install** is used the repository sources.list is checked to see if the desired application is available.  Apt-get is very powerful in that it can also download and install any dependant packages required to make the desired application work.

 - The package you installed isn't actually a package in itself.  The linux-amd64-k8-smp package is dependant on other packages which are dependant on the most recent kernel.  

 - So by installing the general linux-amd64-k8-smp,  apt-get goes to work to install the latest kernel for you.  You may have noticed when you ran that command that it told you 5 packages were to be installed.  These were the dependant packages, which depend on the latest kernel.


 - Here is a good post (from a great thread) on some apt-get commands.

[http://www.ubuntuforums.org/showpost.php?p=468342&postcount=33]("http://www.ubuntuforums.org/showpost.php?p=468342&postcount=33")

[Ubuntu Forums - Terminal for Beginners]("http://www.ubuntuforums.org/showthread.php?t=73885")


 - Now **Synaptic** is a nice GUI 'front-end' to apt-get. You should check it out, in the System -> Administration Menu.  Synaptic allows easy browsing of available packages and simple click installations.  I generally use apt-get from the command line rather than Synaptic, but it is a great application for new users of Linux and Ubuntu.


 - While I'm on it, here are two good links for installing software in Ubuntu and Synaptic specifically

[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

[http://www.psychocats.net/essays/winuxinstall.php]("http://www.psychocats.net/essays/winuxinstall.php")

Happy reading and hope you really enjoy using Ubuntu!

---

