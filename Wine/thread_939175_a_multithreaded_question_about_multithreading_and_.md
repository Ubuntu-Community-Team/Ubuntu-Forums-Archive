---
title: "a multithreaded question about multithreading and thief"
date: 2008-10-05
forum: Wine
---

### Post by Griffin Bain on 2008-10-05
ok guys, I have read the posted stuff on the taskset and schedtool programs in order that I may run thief 2 in wine with the multi threading turned off. I have followed what the forums and help files have said and I still cannot get the program to even launch. 

this is what happened when I tried the taskset way:

nate@nate-desktop:~$ taskset -c 1 wine thief2.exe
wine: could not load L"C:\\windows\\system32\\thief2.exe": Module not found
nate@nate-desktop:~$ sudo taskset -c 1 wine thief2.exe
[sudo] password for nate: 
wine: /home/nate/.wine is not owned by you

and this is what happens when I try the schedtool way:

nate@nate-desktop:~$ sudo schedtool -a 0x2 -e wine thief2.exe
wine: /home/nate/.wine is not owned by you

I don't know what to do, friends, i remeber seeing something else about not being able to run wine as a sudo or a root but I know no other commands to get around the wine not being owned by me stuff.:confused:

---

### Post by Griffin Bain on 2008-10-05
I know I'm not supposed to post wine related stuff here but the issue is not wine or thief, but rather multithreading and core affinity and the ownership stuff and the command line stuff.  please help me I am new here.

---

### Post by Albertint on 2009-09-14
Maybe lowering the affinity in the system monitor... maybe? I dunno either, and sorry if it's not good to resurrect posts, but I've had questions go unanswered as well, so...

---

### Post by naikon89 on 2009-09-14
```
sudo chown -R nate:nate ~/.wine
```This will change the ownership of the wine 
directory, and all sub directories of the wine directory to your user account, and allow users 
of your group to access the directory, and all sub directories.

---

