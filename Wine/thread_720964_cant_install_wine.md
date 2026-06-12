---
title: "cant install wine"
date: 2008-03-10
forum: Wine
---

### Post by dctalk37 on 2008-03-10
Hi im running Unbuntu 7.10. I try and follow the steps at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft). but cant get past spet 3. 

This is what i get in my terminal. I'm no pro so most of the is japanese to me. Please help.

ty-fighter@ty-fighter-desktop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
[sudo] password for ty-fighter:
--18:18:55--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184, 81.171.111.184, 88.159.206.7, ...
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[====================================>] 181           --.--K/s             

18:18:55 (21.79 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [181/181]

ty-fighter@ty-fighter-desktop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
OK
ty-fighter@ty-fighter-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
ty-fighter@ty-fighter-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
ty-fighter@ty-fighter-desktop:~$ winecfg
bash: winecfg: command not found
ty-fighter@ty-fighter-desktop:~$

---

### Post by LoneWolfJack on 2008-03-11
Gutsy comes with WINE pre-installed, so you just start at "Installing WoW". ;)

---

### Post by Vadi on 2008-03-11
Head over to System - Administration - Software Sources, and in the "Ubuntu Software" tab, enable everything except the Source code. Click close, let it reload, and try sudo apt-get install wine once more.

(@LoneWolfJack - I don't think wine comes pre-installed...)

---

### Post by LoneWolfJack on 2008-03-11
Doesn't? I'm pretty sure I had that thing pre-installed. But I may be wrong. It definitely can be found in add/remove programs though...

---

### Post by dctalk37 on 2008-03-11
That you for the help that system/admin thing seems to have worked. I'm now running wine. Next thing is getting wow running. So you might be hearing from me again soon. Thanks again.

---

### Post by mc4man on 2008-03-11
Or you could just head over here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)  and dl. whichever ver. you want.

---

### Post by Vadi on 2008-03-11
> **dctalk37 said:**
> That you for the help that system/admin thing seems to have worked. I'm now running wine. Next thing is getting wow running. So you might be hearing from me again soon. Thanks again.

You're welcome!

---

### Post by stu_3881 on 2008-03-11
Hi,
I seem to have gotten wine installed ok.  I got it here [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/).  I am running Ubuntu 6.06.  I'm starting to suspect that these packages have to exist on the machine in windows partitions that wine somehow finds.  Is this true or can I actually download Textpad into my Ubuntu file system.  I come from a windows env but am running Ubuntu standalone.

---

### Post by Vadi on 2008-03-12
Wine should be able to run Textpad fine. Just right-click on the .exe, and select the wine option.

Just curious, there's a plethora of text editors available for Linux - is there some feature in textpad you're looking for?

---

### Post by stu_3881 on 2008-03-12
I like that I can have 10 or more modules open at once although gedit is OK for that but I guess what I miss most in Linux is find in files.

---

### Post by Vadi on 2008-03-12
Places - Search for files will let you find text in files (just leave the file name category blank, and click on select more options, and type the text in the "contains text" field).

Though I do use wine + notepad++ myself, so eh...

---

### Post by dctalk37 on 2008-03-14
For all those still interested wine and wow are both up and running perfectly. thanks again for all your help

---

