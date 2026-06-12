---
title: "Ubuntu crashed in 2 days"
date: 2007-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by JAmerican on 2007-06-28
Hey all,

I am a new comer to Ubuntu and Linux. I've been a Windows guru and fanboy for some time. I have also purchased a PowerBook G4 to better understand Mac OS X. Having come to like the stability of Mac OS X (being that its really just Unix under the hood), I decided to do the same to my PC. Having installed Ubuntu AMD64 Feisty Fawn on my PC, I came into some problems. I didn't want to have to deal with the terminal and it seems like you need to in order to install an application. In any regard, I installed the NVidia drivers by enabling the Graphics Acclerator.

The problem started when I tried to install the RealTek HD Audio drivers. My PC didn't take them and I started having libasound.so.2 shared library missing errors. I read on the forums to try something and now I cannot see my Ubuntu GUI login screen. I just seen the command prompt. I also think that the Firefox 32 Flash Fix contributed to the problem greatly. I am going to reinstall Ubuntu again but I have a few questions:

Is it better to partition the drive for the OS and regular storage?

If so how do you make the storage partition the default for applications so that the OS partition does not fill up?

Where can I find RealTek High Definition drivers for Linux that won't crash my PC?

What can I do to prevent such a catastrophic problem as this one from happening again?

I thought Ubuntu would have been easier to use and start with but it seems way harder with the constant Terminal codes? Is there a guide that relates Windows commands or actions with Ubuntu commands or actions?

As for my hardware, I have a [Shuttle SN27P2]("http://global.shuttle.com/Product/Barebone/SN27P2.asp"). Can I get some suggestions as to where I can get drivers for my hardware?

Also is there a recovery mode or repair mode of some kind? I tried using a guide that told me to use the Live CD but with every command, the terminal windows replied with 0 changes, 0 updates, 0 etc...

Please help. After this experience, I felt like going back to Windows but I am willing to live though this and make Ubuntu or just Linux in general work for me. 

To get an idea of my background. I am a person who likes to program in Visual Basic .NET 8, uses Windows Mobile 6 Smarthpone (T-Mobile Dash), uses Macromedia Fireworks MX 2004 to create images and logos, used to play games on my PC until I got a 360. If anyone has had better luck with another distro with my kind of personality, please suggest it. I just want to leave the headache that is Windows XP. As for my Dash, its my first Windows Mobile device. I used to be a Palm OS person. So I am not a M$ fanboy throughout. It just looks that way.

BTW, my Ubuntu Linux install is on a 120 GB HDD by itself and I partitioned the drive to have 8GB for Ubuntu OS and the rest for storage.

Could someone also tell me how much swap is necessary?

Thanks all. Looking forward to replies. Here is my site as well where I posted basically what I said above...

[http://www.jamerican.net/?p=39](http://www.jamerican.net/?p=39)

JAmerican

---

### Post by carniolus on 2007-06-29
Well if you are willing to have ubuntu all of your hard drive:
When your running the installer and you are in partition manager just set "Use the largest continuous nonallocated space" or something like that to install ubuntu in empty space on your disk.

---

### Post by JAmerican on 2007-06-29
I've moved the discussion here...

[http://ubuntuforums.org/showthread.php?p=2934132&posted=1#post2934132](http://ubuntuforums.org/showthread.php?p=2934132&posted=1#post2934132)

Tks for the help.

JAmerican

---

### Post by Jouke74 on 2007-06-29
> I have allocated 3.5 GB for swap space (for a memorysize of 2 GB). Though, I never have have been using swap memory for any program. My root partition is 28 GB. The whole system installed is around 4 GB, depending on the amount of additional programs you install with synaptic. I have "home" together with root. If you want to have all your storage under home, you can also make a separate home partition for your data. Carefully go through the options of the partitioner.

> Check if your audio is not working using the default setup first. Unlike windows many drivers are pre-installed.

> Get comfortable with the terminal, it will be your life-saver in many more problems to come. 
There are many Linux manuals on the web with the basic commands. Another option is to use the "MAN" command which stands for "Manual" but I did not like it too much.

> Take note that 64 bits means sometimes more issues to get stuff working, hence this forum. Also for linux there are sometimes only 32 bits versions of programs.

---

### Post by JAmerican on 2007-06-29
> **Jouke74 said:**
> > I have allocated 3.5 GB for swap space (for a memorysize of 2 GB). Though, I never have have been using swap memory for any program. My root partition is 28 GB. The whole system installed is around 4 GB, depending on the amount of additional programs you install with synaptic. I have "home" together with root. If you want to have all your storage under home, you can also make a separate home partition for your data. Carefully go through the options of the partitioner.

> Check if your audio is not working using the default setup first. Unlike windows many drivers are pre-installed.

> Get comfortable with the terminal, it will be your life-saver in many more problems to come. 
There are many Linux manuals on the web with the basic commands. Another option is to use the "MAN" command which stands for "Manual" but I did not like it too much.

> Take note that 64 bits means sometimes more issues to get stuff working, hence this forum. Also for linux there are sometimes only 32 bits versions of programs.

My audio did work before I installed the Realtek drivers. It was just too low to hear anything comfortably. 

JAmerican

---

