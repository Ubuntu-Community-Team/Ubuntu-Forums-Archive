---
title: "Installing matlab 2007a step by step instructions PLEASE!!"
date: 2007-09-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by BigWill on 2007-09-06
Hi there.  I am running feisty fawn on a dell dimension E521 (thank you to Dell-finally for getting the new bios out to make it possible to slowly dissociate myself from VISTA).  I digress.
I am trying to install matlab2007 and need some really basic step by instructions to do this.  I have the dvd and thats about it.
If someone who has done this and gotten it all working nicely was kind enough to fill me in on the hows (and the whys) I would be forever in their debt (figuratively)

---

### Post by o3rat on 2007-09-06
I install matlab R2006a but im sure 2007a isnt any different. First you need to get [wine]("http://www.winehq.com") there or using "synaptic package manager." If you use synaptic you need to add 

[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) 
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

to the repositories. 
 
Then after installing wine I did what this [tutorial said]("http://appdb.winehq.org/appview.php?iVersionId=5385&iTestingId=5290"). Basically install Matlab in windows and copy over the installation folder.

---

### Post by AegisTalons on 2007-09-06
So MatLab is made to run natively on Unix based systems, such as Ubuntu. You need to have the MatLab installer for Linux. I currently have MatLab 2007 installed, but I cannot get the menus (File, Edit, ...) to display correctly. Check the disc and see if MatLab includes any information about installing into Linux.

On my install, I found that it had a lot of documentation on the disc especially for installing it on Linux. In there you should find a step by step instructions.

Let me know how it goes.

---

### Post by oneminizut on 2007-09-06
I have gotten this to run on slackware 12, so as you digress I will try again on feisty 64 and post results.  It was a task though, as I remember semi clearly.  Get back to you, but I may have to re-download as it's been a bit of time.  Have to look through the back-ups.

---

### Post by sonni_kuba on 2007-09-07
It would be a poor idea to run it in Wine, since Matlab runs so much quicker under Linux then WIndows. Here are the step by step instructions:



1) Create a matlab directory 

$sudo mkdir /usr/local/matlab

2) Paste your license information into a license.dat file, and save

$cd /usr/local/matlab/ && sudo gedit license.dat

3) Copy the entire contents of the DVD into your /usr/local/matlab/ folder

$cd /media/cdrom/ && sudo cp * -R /usr/local/matlab/

4) Install matlab ...

$sudo /usr/local/matlab/./install_matlab

5) Answer yes to everything, and check off to install the symbolic link

6) When the installer finishes, you will have to start the license manager

$/usr/local/matlab/etc/./lmstart

7) Then change the ownership on your matlab directory

$sudo chmod a+rwx -R /usr/local/matlab/

8) Finally, you can launch matlab

$matlab

=-=-=-=-=-=-

Let me know if it doesn't work for you.

---

### Post by dolorindex on 2007-09-07
Yeah as mentioned above it'd be stupid to run matlab through wine since they have a native 64bit linux version. I have it installed on my laptop, though I'm sorry to say I can't recall the exact procedure, though I do recall it being very painless. I've gotten into the habit of downloading it directly from their website, since the disks they send are for mac or windows. You need to make sure you have java installed since all the menus and the installer are java based. The only issue that I had was getting the license manager to boot on startup(I'm new to linux), they have a nice walkthrough and I believe script to help you set that up.

---

### Post by Nadab on 2007-10-02
> **sonni_kuba said:**
> It would be a poor idea to run it in Wine, since Matlab runs so much quicker under Linux then WIndows. Here are the step by step instructions:



1) Create a matlab directory 

$sudo mkdir /usr/local/matlab

2) Paste your license information into a license.dat file, and save

$cd /usr/local/matlab/ && sudo gedit license.dat

3) Copy the entire contents of the DVD into your /usr/local/matlab/ folder

$cd /media/cdrom/ && sudo cp * -R /usr/local/matlab/

4) Install matlab ...

$sudo /usr/local/matlab/./install_matlab

5) Answer yes to everything, and check off to install the symbolic link

6) When the installer finishes, you will have to start the license manager

$/usr/local/matlab/etc/./lmstart

7) Then change the ownership on your matlab directory

$sudo chmod a+rwx -R /usr/local/matlab/

8) Finally, you can launch matlab

$matlab

=-=-=-=-=-=-

Let me know if it doesn't work for you.

I have the R2006a Matlab version, but I have it in 3 CD's do I have to copy all of them to the directory? If the answer is "yes", how can I do this?

---

### Post by eneth80 on 2007-10-17
I also have those 3 cds. I have launched the starter with : 
/~/Desktop/MatlabLinux/CD1/install
everything goes all right, at least apparently. but then i cannot launch matlab. /usr/local/matlab/etc/./lmstart does not work (no such file or directory).
/usr/local/matlab does not exist.

---

