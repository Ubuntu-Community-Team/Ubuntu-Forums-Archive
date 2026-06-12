---
title: "amd64 x2, install has i386 kernel?"
date: 2007-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by havrelm1 on 2007-03-16
I just installed Ubuntu, and got the hang of a good majority of the program in a couple hours, I tried installing Ardour, and got an error message about my system having the i386 kernel, well I have an amd 64x2 processor, seems like the system is using both processors, but It would be nice to be using the system in 64 bit for the extra speed etc. Any suggestions/detailed instructions here? I don't want to start messing with things I know nothing about, hehheh.

:guitar:

---

### Post by Kobalt on 2007-03-16
I advise you not to switch to the 64bit kernel. 
First, you will not gain a whole lot of speed in the use of your system, since very few apps are ready for 64bit instructions. 
Second, very common things such as Flash, Java or some audio/video codecs are tricky to install on a 64bit kernel...

---

### Post by havrelm1 on 2007-03-16
what about a newer kernel? I can't install some programs because I get a "your system has the i386 kernel and can't install". What should I do then?

---

### Post by dptxp on 2007-03-16
I am using 64 bit, audio/video codecs can be loaded by add/remove, the only problems I have are - 
recorder does not show input device.
the built-in card reader (it is a laptop) does not show up.
I have not used much, but I decided not to go to 32 bit.
I did not check Flash.

---

### Post by havrelm1 on 2007-03-16
I just want to have the optimum settings for whats available at the moment. But I can't install some programs because I have an i386 kernel, but I dont know what I should upgrade to and how.

---

### Post by Songwind on 2007-03-16
The applications you are trying to install probably have 32 bit versions which should install just fine in your i386 kernel.

---

### Post by havrelm1 on 2007-03-16
I installed Ubuntu 6.10, did all the updates it prompted me to do, went to add/remove programs, searched for Ardour, and tried to install. Then I get that error message.

---

### Post by Kilz on 2007-03-16
> **Kobalt said:**
> I advise you not to switch to the 64bit kernel. 
First, you will not gain a whole lot of speed in the use of your system, since very few apps are ready for 64bit instructions. 
Second, very common things such as Flash, Java or some audio/video codecs are tricky to install on a 64bit kernel...

Thats a load of FUD (Fear Uncertainty and Doubt). Secondly, the i386 install on 64bit hardware is not the cure all some people make it out to be. There are entire sections of this forum dealing with setup and problems people with 32bit installs have.

---

### Post by ginyip on 2007-03-16
Well, actually. I am also a 64 bit cpu owner myself. I am using 32 bit anyway. First of all, there are not many 64 bit programs at the moment. Secondary, I prefer to save my time on banging my head on the wall in order to try finding out how to install such and such drivers for a 64 bit kernel. Thirdly, I am an ATI user, I have tried ATI 64 bit driver many time on a 64 kernel. However, it doesn't do very well. Also I do not want to spend few hundred buck to buy a Nvidia card. Even though I wana spend few more hundred buck switch to Nvidia card, I can't be sure that it will be able to use with a 64 bit kernel.

The point is. The standard is still on 32 bit side so far. For such a huge range of devices on the PC market. We can't expect Linux to "just get it right on" on the 64 bit kernel. For 64 bit, it's getting there but it needs more time.

---

### Post by Kilz on 2007-03-16
> **ginyip said:**
> Well, actually. I am also a 64 bit cpu owner myself. I am using 32 bit anyway. First of all, there are not many 64 bit programs at the moment. Secondary, I prefer to save my time on banging my head on the wall in order to try finding out how to install such and such drivers for a 64 bit kernel. Thirdly, I am an ATI user, I have tried ATI 64 bit driver many time on a 64 kernel. However, it doesn't do very well. Also I do not want to spend few hundred buck to buy a Nvidia card. Even though I wana spend few more hundred buck switch to Nvidia card, I can't be sure that it will be able to use with a 64 bit kernel.

The point is. The standard is still on 32 bit side so far. For such a huge range of devices on the PC market. We can't expect Linux to "just get it right on" on the 64 bit kernel. For 64 bit, it's getting there but it needs more time.

1. There are enough 64bit applications. Graphics, encoding and number crunching applications get a 30% performance increase.
2. FUD - Few if any drivers are needed.
3. I have ATI graphics myself. There is no difference between its performance and the 32bit version. There may have been with the 8.25.18 drivers, but that was long ago. 
4. 64bit Ubuntu is as old as 32bit Ubuntu. This isnt the "First time". The "needs more time" argument is outdated FUD.

In short this FUD is a rationalization designed to make you feel better about installing an operating system because you perceive that it is easier. It isnt, it isnt perfect. The 32bit version does not work flawlessly on all 64bit hardware. Heck it doesnt work flawlessly on 32bit hardware. Setup and learning are to be expected regardless of which version you install.

---

### Post by dptxp on 2007-03-17
If users start shying away from 64-bit, it can not grow.
Obviously if you have some critical applications that you are unable
to run on some OS, you have to use what works for you.
32 bit on AMD 64 has its own share of problems as per some posts.

---

### Post by havrelm1 on 2007-03-20
Though some good information, I am still trying to figure out what to do here. If I need to install the 64bit amd kernel, I would like to try it out, how do I go about installing it without screwing up my system. I'm somewhat new here.

---

### Post by saneone on 2007-03-20
To try the 64 bit Ubuntu u`ve got to install a new system... The ISO image for 64 bit is avalaible on the internet.
I'm using 64 bit OS and i don't have any bigger problems with it. 99% of codecs are avalaible since mplayer1.0rc1 and the latest vlc. Flash and Java are also avalaible.
I'm using Ardour and it works perfectly.

---

### Post by havrelm1 on 2007-03-20
thanks, I will give it a try!

---

### Post by John.Michael.Kane on 2007-03-20
Have read here [**Advantages and Disadvantages of 64bit.**]("http://www.ubuntuforums.org/showthread.php?t=368607")

At the bottom of the page links to the live cd ,and methods for installing other items under 64bit.

---

### Post by FrozenFOXX on 2007-03-20
> **ginyip said:**
> Even though I wana spend few more hundred buck switch to Nvidia card, I can't be sure that it will be able to use with a 64 bit kernel.

The nVidia drivers work fine, I'm proof of it (BFG Tech GF7800GT OC, rock solid since day one and has survived many a driver and operating system...even the dreaded Battlefield 2 engine).  The nVidia drivers are built specifically for 32 **AND** 64 bit and have been that way for quite awhile.  nVidia knows how to support their products more often than not.

---

### Post by Feenix3k on 2007-03-25
I have the amd 64 x2, if i can get the no acpi to work i will be loading in 32 bit mode. This system had 64 bit W$ and I had a lot of headaches. I finaly deleatyed all and went back to 32bit. 

The technoalagy is still behind in 64 bit drivers.

---

### Post by Kilz on 2007-03-25
> **Feenix3k said:**
> I have the amd 64 x2, if i can get the no acpi to work i will be loading in 32 bit mode. This system had 64 bit W$ and I had a lot of headaches. I finaly deleatyed all and went back to 32bit. 

The technoalagy is still behind in 64 bit drivers.

Only in Windows. You cant compare windows drivers and linux in the 64bit department.

---

### Post by uputer on 2007-03-25
So, 32-bit applications and programs still don't work (properly?) in 64-bit Ubuntu (i.e. Feisty)?   Other than Firefox, maybe?

I'm still confused here.

I tried using Automatix a while back when I installed Ubuntu 64-bit on my AMD 64 machine.   It didn't help (to put it nicely).

---

### Post by Kilz on 2007-03-25
> **uputer said:**
> So, 32-bit applications and programs still don't work (properly?) in 64-bit Ubuntu (i.e. Feisty)?   Other than Firefox, maybe?

I'm still confused here.

I tried using Automatix a while back when I installed Ubuntu 64-bit on my AMD 64 machine.   It didn't help (to put it nicely).

Ubuntu is not multiarch. You cant install 32bit applications automatically with synaptic. But, and this is an important concept, the number of 32bit applications you need is small. Exactly what applications do you need?
If you have problems with Automatix, you might want to tell them over at the automatix website.

---

### Post by russell.h on 2007-03-26
This thread is driving me nuts. I was afraid of switching to 64 bit for a while, because it seemed like there was "all this stuff" that I was going to have to do. As it turns out it is very simple. Now, let me go down this thread and address *just a few* of the incredibly wrong things people have said in it (I know Kilz beat me to most of them already, but still):

> First of all, there are not many 64 bit programs at the moment.
That is wrong. I currently have over ***twenty one thousand*** packages available in synaptic, and the only third party repository I have enabled is the Beryl repository. As far as I know nearly every open source program available in the i386 repos is available in the 64 bit ones also, although there may be a few exceptions.
> I prefer to save my time on banging my head on the wall in order to try finding out how to install such and such drivers for a 64 bit kernel.
I have only had to install 3 drivers on 64 bit so far:
1. nvidia driver = sudo apt-get install nvidia-glx <-**just like in i386**
2. Brother printer driver - 1. Download driver .debs from the Brother site. 2. Install drivers (I had to use the --force-all option to install them, that was simple even for my then-linux-noob self)
3. MTP for my Zen Touch (if you call that a driver) - Followed the instructions for doing in in 32 bit to the letter, (this involved compiling something, but you have to do that on 32 bit too) and it worked beautifully.
> I am an ATI user, I have tried ATI 64 bit driver many time on a 64 kernel.
That may be, but they work fine now (or as fine as ATI drivers ever work).
> Even though I wana spend few more hundred buck switch to Nvidia card, I can't be sure that it will be able to use with a 64 bit kernel.
If they send you a broken card, then send it back. If the card isn't broken then it will work with a 64bit kernel.
> This system had 64 bit W$ and I had a lot of headaches. I finaly deleatyed all and went back to 32bit.
Let me see if I have this right: You were using Windows and it was causing you lots of headaches? No way....

I used 64 bit Windows once, and it was crap. I used 32 bit Windows a lot more than once, and it was still crap, although somewhat less so.

What people need to understand is this: Windows programs are typically released as binaries, so a lot of programs won't work at all on 64 bit Windows, and ones that do are for the most part still a 32 bit binary, and so they are not getting any performance benefit.

However, Linux programs are typically released as source code, which is higher level and architecture independent. The same program that can be compiled to run on a 32 bit processor can be compiled to run on a 64 bit processor. In fact, depending on its use of floating point math it is probably a fairly trivial matter to compile it to run on the microchips which control your microwave, stereo, mp3 player, router, etc.

**The switch to 64 bit probably the greatest opportunity Linux has ever had**, and it perfectly exemplifies one of the greatest benefits of Open Source - portability. While windows users are stuck trying to sort out their binaries, linux packagers have simply begun compiling programs for 32 and 64 bit, a task made possible by the fact that they have the source code, while windows developers, even if they have their own source, probably don't have the source of the libraries their programs rely on. While the window software market has to completely rebuild itself from the ground up, Linux users have been enjoying using 64 bit software for  years.

***********************************************

Ok, so now that I'm done ranting, there is really one thing that people need to do when they switch to 64 bit: They need to install 32 bit Firefox so they can install (proprietary, binary) plugins. 

Now pay close attention -
1. Download the script in the thread that Kilz's signature links to.
2. Run the script in the thread that Kilz's signature links to.

That wasn't so hard was it? :lolflag:

---

### Post by Kilz on 2007-03-26
> **russell.h said:**
> This thread is driving me nuts. I was afraid of switching to 64 bit for a while, because it seemed like there was "all this stuff" that I was going to have to do. As it turns out it is very simple. Now, let me go down this thread and address *just a few* of the incredibly wrong things people have said in it (I know Kilz beat me to most of them already, but still):
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`
Ok, so now that I'm done ranting, there is really one thing that people need to do when they switch to 64 bit: They need to install 32 bit Firefox so they can install (proprietary, binary) plugins. 

Now pay close attention -
1. Download the script in the thread that Kilz's signature links to.
2. Run the script in the thread that Kilz's signature links to.

That wasn't so hard was it? :lolflag:

:D I enjoyed your post!

---

