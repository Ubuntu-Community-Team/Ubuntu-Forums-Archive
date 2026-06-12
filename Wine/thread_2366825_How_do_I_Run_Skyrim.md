---
title: "How do I Run Skyrim?"
date: 2017-07-22
forum: Wine
---

### Post by sweetpe on 2017-07-22
I've messed around with Ubuntu a few times, but nothing in depth like dealing with Wine, Terminal or Windows programs. 
I have an HP Notebook 15, 
4gb of RAM, 
250gb Hard Drive, 
Intel Celeron N2920 Processor with Turbo Boost up to 2GHz with Intel HD Graphics Card. 
I'm currently running Ubuntu 17.04 & as far as I can tell everything runs great. 
I installed PlayOnLinux, then through that program installed Steam (after installing Steam through Linux to find you can't install programs from the Linux version). 
I opened Steam, logged in, then downloaded Skyrim & all it's DLC's. 
The installations took forever but went pretty smooth. 
The game starts up until I get the menu screen, it shows no options. 
After sitting for half an hour I came to the conclusion it's not slow loading. 
I opened PlayOnLinux to find it has Skyrim & an install button so I reinstalled through that but I get an error, do to security locks to prevent male-ware or whatever.
I let it try to install anyway, the first few tries it just shut off during the install but when I finally got it to finish I ran into the same problem.
I tried a few sudo commands I looked up, but none of them installed or made any changes from what the terminal read.
I've seen multiple videos of people playing high end games on Ubuntu but no idea how to do it myself. I'm very familiar with Windows & its software & pretty good with the internal parts as well.
Any help would be greatly appreciated. Every forum I've looked at they all ask about specs & I have yet to find a solution based on mine.

---

### Post by deadflowr on 2017-07-22
Moved to *Wine*

---

### Post by sccman on 2017-07-23
I can run Skyrim through Steam on Lubuntu 17.04. It looks like Wine can run Skyrim, so the issue may either need some extra configuration or it may be PlayOnLinux itself.

We'll need more information on the issue. What does the error message say?

Also, try running PlayOnLinux through the terminal and running Skyrim. Copy the terminal messages and post them here.

---

### Post by sweetpe on 2017-07-23
I have Ubuntu 17.04, everywhere Ive read, not all Linux OS's are the same. As I said before, I don't know much about Linux, Terminal, or Windows programs through Linux. The error I get says I need to change /proc/sys/kernel/yama/ptrace_ scope to 0. I've looked this up and It's not a bug, it's a security thing. Skyrim has been Installed and starts up, i get the startup screen with detailed graphics but when the Skyrim logo pops up for the main menu I have no options or buttons. I have no idea how to run programs through terminal because whenever I look it up, it's specific coding, usually to a specific file or program. Aside from not being able to tell where the code ends and the file name begins, i have no idea how to find the file or programs I need. Like when i tried to install new themes, they give me a code to install a specific file I don't have and within the code I saw it says the file name like 3 times with random stuff between. Aside from all that IDK what info I haven't given..

---

### Post by sweetpe on 2017-07-23
The only thing i can think of is that since I didn't install it through PlayOnLinux without error, that maybe it's missing certain windows programs to run skyrim. because when I try to install Skyrim through PlayOnLinux it lists, java and a bunch of other windows programs that you need to run any windows programs. Everytime I try to use PlayOnLinux for the install it shuts off midway through and i have to keep trying until it works but even when it does finally install i get the same issue as if i installed through just steam. I'm almost positive its because of the security issue but i also dont wanna put my computer at risk if i were to bypass this or whatever.

---

### Post by mastablasta on 2017-07-24
> **sweetpe said:**
>  
Intel Celeron N2920 Processor with Turbo Boost up to 2GHz with Intel HD Graphics Card. 
.
assuming it even runs on these specs.... 

you probably need to install directX of some sort.

---

### Post by sccman on 2017-07-24
We can't do much without input to work off of. We'll be throwing darts in a pitch black room.

> **sweetpe said:**
> I have no idea how to run programs through terminal because whenever I look it up, it's specific coding, usually to a specific file or program.

Open the terminal (CTRL+ ALT + T) and enter **p****layonlinux**. Run Skyrim like you normally do and recreate the problem.

When you have the issue, don't close anything yet. Copy (CTRL + Shift + C) the whole text in the terminal and paste it (CTRL + V) here in a post. Then you can close it.

---

### Post by sweetpe on 2017-08-01
I've run Skyrim with the highest graphics setting the game has on an Acer Switch 10, pretty sure it should run fine on the lowest setting. I know how to run things in Windows & the types of programs i need to do so. On Windows it's fairly simple. Doing something simple for Windows, is difficult for me in Linux. Thank you for the Link, hopefully it helps me grasp how Linux functions better.

---

### Post by sweetpe on 2017-08-01
I apologize, that was lazy on my end. I had like 50 tabs up researching before I remembered my account on here & had already closed everything. I know how to copy and paste lol but glad to know the quick keys for terminal, thanks. Do i just type "playonlinux" minus the quotes and nothing else like dos? I'll recreate my problem and post it though, thanks again

---

### Post by mastablasta on 2017-08-01
not playonlinux, type wine & run command as sccman requested (playonlinux is just a GUI frontend for wine).

you are trying to run a program made for widnows in a completelly different operating system (linux) using a reverse engineered compatibility layer (wine). so all those .dll that windows has have been reverse engineered by wine devs. sometimes it all works perfectly, other times plenty of effort is needed. if the game was developed for linux as well, then it would be very easy to install and run it on linux.

wineHQ appdb might have some information. also i haven't visited in a while but UESP (unoficial elder scrolls pages) used to have some very good information on running TES games on linux.

---

### Post by sccman on 2017-08-01
> **mastablasta said:**
> not playonlinux, type wine & run command as sccman requested (playonlinux is just a GUI frontend for wine).

That works too. I only suggested **playonlinux** because it's what I know he's using. It's better to troubleshoot problems in what people are comfortable using, in my opinion.

---

