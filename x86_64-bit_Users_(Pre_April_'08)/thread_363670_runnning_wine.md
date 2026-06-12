---
title: "runnning wine"
date: 2007-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by simonsphotos on 2007-02-17
Well trouble was already anounced when on thw wine site they said it was not quite 64 bit compatible but I went ahead anyway. they said to use this workaround:

cd ~/Desktop 
sudo dpkg --force-architecture -i wine_0.9.30~winehq0~ubuntu~6.06-1_i386.deb

and I did and the last I saw was that wine was replacing an already existing wine and it was setting up....

the the command prompt came up and I saw and heard no more of wine. how do I know if it was installed ? where do I go to launch it ? ok you got it I am quite raw on this all I know is I want to have the option of running some windows apps under Ubuntu

---

### Post by an.echte.trilingue on 2007-02-17
three commands you need:
man wine (documentation)
winecfg (configure wine)
wine <filename> (run something with wine)

If any of those don't work, your install might be broken, but usually dpkg will tell you if it had an error. On the desktop, if you right click on an .exe file, you should have the option to "run with wine"

Take care
-mat

---

### Post by simonsphotos on 2007-02-17
ok so where do I have to be to run wine is the standard command prompt ok to just type in wine ?
so if I put a windows exe file onto say the desktop and right click it I should have the run with wine option ?

sorry but I am relearning using a computer all over again with Ubuntu and until I figure out how to connect to the internet I am sufing in windows getting info and then rebooting

---

### Post by Kilz on 2007-02-17
> **simonsphotos said:**
> ok so where do I have to be to run wine is the standard command prompt ok to just type in wine ?
so if I put a windows exe file onto say the desktop and right click it I should have the run with wine option ?

sorry but I am relearning using a computer all over again with Ubuntu and until I figure out how to connect to the internet I am sufing in windows getting info and then rebooting

This page of mine might help you understand wine and how to use it. [http://tghc.org/wine.php](http://tghc.org/wine.php)

---

### Post by simonsphotos on 2007-02-17
thanks it did shed some light

---

### Post by simonsphotos on 2007-02-18
now I get a error 127 when I try and run it,

the installation went as follows:


dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 87583 files and directories currently installed.)
Preparing to replace wine 0.9.30~winehq0~ubuntu~6.10-1 (using wine_0.9.30~winehq0~ubuntu~6.10-1_i386.deb) ...
Unpacking replacement wine ...
Setting up wine (0.9.30~winehq0~ubuntu~6.10-1) ...

simon@Simonsphotos:~/Desktop$

has it installed ? I figure it was already present on ubuntu but not enabled due to the 32/64 bit issue and so basically I got know where

---

### Post by Kilz on 2007-02-18
> **simonsphotos said:**
> now I get a error 127 when I try and run it,

the installation went as follows:


dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 87583 files and directories currently installed.)
Preparing to replace wine 0.9.30~winehq0~ubuntu~6.10-1 (using wine_0.9.30~winehq0~ubuntu~6.10-1_i386.deb) ...
Unpacking replacement wine ...
Setting up wine (0.9.30~winehq0~ubuntu~6.10-1) ...

simon@Simonsphotos:~/Desktop$

has it installed ? I figure it was already present on ubuntu but not enabled due to the 32/64 bit issue and so basically I got know where

```
Unpacking replacement wine ...
```
Says it was installed already and you just reinstalled it.

```
Setting up wine (0.9.30~winehq0~ubuntu~6.10-1) ...
```
Basicly is saying that it installed it again.

To check. Open a terminal and type in 
```
wine
```
See if it errors, if it gives you instructions to use it, or that its setting up a folder , its installed.
Alternately you could search in synaptic to see if its installed. Or type in ```
winecfg
``` If a configuration box pops up its installed. Let me caution you against the common misconception of thinking you can install anything with the config. You cant.

---

### Post by simonsphotos on 2007-02-18
hm I think I tried that with no luck if I just type wine it says that it is a wrong command I suppose because it is not installed but in usr/bin there are wine files perhaps they are just stored and not installed ?

---

### Post by mhenriday on 2007-02-18
> **Kilz said:**
> This page of mine might help you understand wine and how to use it. [http://tghc.org/wine.php](http://tghc.org/wine.php)

Dear **Kilz**,

When I lost my **XP** set-up when trying to do a double boot a couple of months ago, I also lost a lot of files. The content of most of these was retrievable as I use **Gmail** as my email client, but some files that I should like to have were not. I was, however, using [Mozy]("https://mozy.com/?ref=LMYF7F") to back up my other files, so that these are also in principle retrievable. As **Mozy** doesn't offer any backup services for **Linux**, I thought I'd wait until I had performed a dual boot installation, and they try to get my files back, but I've never succeeded in doing so, and as time goes by and I find myself more and more comfortable with **Ubuntu**, I become less inclined to try. Do you know if it is possible to run **Mozy** from the **WINE** compatibility layer ? If so, any suggestions about how I can go about doing so ? To retrieve my **Windows** data from **Mozy**, all I have to do is write and provide my account name and password, and the data will be forwarded to me within a week. Will I be able to read it on my computer with the help of **WINE** ?

Thanks a lot for your help !

Henri

---

### Post by Kilz on 2007-02-18
> **simonsphotos said:**
> hm I think I tried that with no luck if I just type wine it says that it is a wrong command I suppose because it is not installed but in usr/bin there are wine files perhaps they are just stored and not installed ?

Please open a terminal and enter in the command ```
winecfg
``` in the terminal. Then copy and paste in the command and the response you get to a post here. If a configuration window opens please tell us if it dose.

> **mhenriday said:**
> Dear **Kilz**,
 Will I be able to read it on my computer with the help of **WINE** ?

Thanks a lot for your help !

Henri


If you read the page I linked to, you will see that wine isnt perfect. It doesnt run all Windows applications. There is also a wine application database to help you find out how to setup some applications to run. Unfortunately there is no Mozy entry in the wine application database. The best advice I can give you is to try it, it cant hurt and it may work.

---

### Post by simonsphotos on 2007-02-18
ok next time I'm up with ubuntu I'll try the command again I also don't get the run with wine when I right click on an exe file

---

### Post by Kilz on 2007-02-18
> **simonsphotos said:**
> ok next time I'm up with ubuntu I'll try the command again I also don't get the run with wine when I right click on an exe file

You wont unless you have entered it as a custom command first, thats at the bottom. Alternately you could click on an exe, click opens with, click add, click use custom command, type in wine. This way wine becomes associated with .exe files.

---

### Post by simonsphotos on 2007-02-19
simon@Simonsphotos:~$ winecfg
exec: 29: /usr/bin/wine: not found
simon@Simonsphotos:~$ 


I hope this is of help what I can't unerstand is that wine is in bin this is the answer to the winecfg command

---

### Post by sloggerkhan on 2007-02-19
it'd probably be easier to start with 32 bit ubuntu... then wine is fairly easy.

---

### Post by Kilz on 2007-02-19
Go here and get the amd64 package for wine

[http://www.ubuntuforums.org/showthread.php?t=297280](http://www.ubuntuforums.org/showthread.php?t=297280)

---

### Post by Kilz on 2007-02-19
> **sloggerkhan said:**
> it'd probably be easier to start with 32 bit ubuntu... then wine is fairly easy.

I wish there was a separate count for posts in the 64bit area. That way we could tell when someone was jumping in to spread FUD.

---

### Post by sloggerkhan on 2007-02-19
nice Watchmen Smiley. Love that comic.
Sorry, the guy just sounds like he's new to linux. I found getting stuff to work pretty confusing when I first started because I tried doing 64 bit first. So I went 32 bit, and after learning the basics in an environment where they worked, getting stuff working in 64 bit became a lot easier. I actually wound up having like 3 or 4 OSes booting back when I first started out with linux...

Anyhow, good luck getting it working. Sound like you are more persistent than I was initially.

---

### Post by simonsphotos on 2007-02-19
well I have a 64 bit computer and would like the performance that 64 bit can give in heavy duty things like image manipulating

---

### Post by simonsphotos on 2007-02-19
> **Kilz said:**
> Go here and get the amd64 package for wine

[http://www.ubuntuforums.org/showthread.php?t=297280](http://www.ubuntuforums.org/showthread.php?t=297280)


thanks for the link I think us last three or four answered imultaneously and I missed your replys

---

### Post by Iskeet on 2007-02-19
My wine isnt working that great, it wouldn't let me install the AMD 64, but it would let me install the other, it wont load exe files but winrar.

---

### Post by simonsphotos on 2007-02-19
I have a problem with the link it tells me my address is already downloading a file and to wait (what other file ?) is there another hoster for this file ?

---

### Post by mhenriday on 2007-02-19
Dear **Kilz**,

Here is what I have done. Very shortly after requesting my files from **Mozy**, I received two files to be downloaded to my computer. I clicked on the first one to download it to a map called «Mina dokument» (My documents). Due to the size of this exe file (more than 400 MB). the downloading process took some time, but when it was finished, I right-clicked on the icon as per your instructions. One of alternatives which appeared on the menu was «Open with WINE Windows Emulator», but when I clicked on that nothing happened. I tried the same thing with the smaller (168 MB) file, but again, no result. Have I missed something ? I can feel those files tantalisingly close to my hands and eyes ; is there something I can do to open them, or will they, like the food and drink presented to Tantalos, be swept from my grasp before I can get my fingers 'round them ?...

Henri

---

### Post by Kilz on 2007-02-19
> **mhenriday said:**
> Dear **Kilz**,

Here is what I have done. Very shortly after requesting my files from **Mozy**, I received two files to be downloaded to my computer. I clicked on the first one to download it to a map called «Mina dokument» (My documents). Due to the size of this exe file (more than 400 MB). the downloading process took some time, but when it was finished, I right-clicked on the icon as per your instructions. One of alternatives which appeared on the menu was «Open with WINE Windows Emulator», but when I clicked on that nothing happened. I tried the same thing with the smaller (168 MB) file, but again, no result. Have I missed something ? I can feel those files tantalisingly close to my hands and eyes ; is there something I can do to open them, or will they, like the food and drink presented to Tantalos, be swept from my grasp before I can get my fingers 'round them ?...

Henri

Unfortunately I have no experience running or installing Mozy so Im not sure what we can do about it. It looks like you have dont what you should. But wine isnt perfect. Just a thought, have you tried installing windows to a vmware virtual machine?

---

### Post by Kilz on 2007-02-19
> **sloggerkhan said:**
> nice Watchmen Smiley. Love that comic.
Sorry, the guy just sounds like he's new to linux. I found getting stuff to work pretty confusing when I first started because I tried doing 64 bit first. So I went 32 bit, and after learning the basics in an environment where they worked, getting stuff working in 64 bit became a lot easier. I actually wound up having like 3 or 4 OSes booting back when I first started out with linux...

Anyhow, good luck getting it working. Sound like you are more persistent than I was initially.

Thanks, Im an avid comic reader, Watchmen was one of my all time favs. Sorry to be so hard. Its been one of those days.

---

### Post by John Jason Jordan on 2007-02-19
> **simonsphotos said:**
> well I have a 64 bit computer and would like the performance that 64 bit can give in heavy duty things like image manipulating
I started with Linux a year and a half ago after years of using Windows. I needed a laptop for school and I wanted to learn Linux. I deliberately bought a 64-bit computer and deliberately put 64-bit distros on in, ending up with Ubuntu Hoary as my first serious Linux OS. Yes, it is frequently a pain in the butt. But I wanted to learn Linux and a baptism by fire is more instructive. I still have a Windows 2000 desktop that I can use in case of serious disaster, but I now use the laptop for 99% of my work, today using Ubuntu Edgy amd64.

But my needs and desires are different from anyone else's. I just want to say that if you want to learn Linux, going 64-bit will teach you more than 32-bit because of the extra stuff you have to do. On the other hand, for some people that might be biting off more than they can chew at once, so the advice to start with 32-bit might make more sense. I won't comment on how much extra you have to do with 64-bit over 32-bit because I've never actually tried 32-bit Linux.

Re the problems with Wine. That was one problem I was not ready to tackle. At the time when I decided I needed Wine the extant version of Ubuntu was Hoary, and it was even harder to install Wine on 64-bit Hoary than it is now on Edgy. I checked with the folks at Codeweavers (codeweavers.com) and they assured me that their CrossOver Office 5.03 Pro would install seamlessly on 64-bit Hoary. The student price was $58 and I paid it just so I wouldn't have to deal with the issue of trying to install Wine. I just followed the instructions, clicked a couple of times, and it was installed.

So far CrossOver Office has done almost everything I need. There are only a couple of things I still need my Windows computer for. And I am now investigating VMware Player, which will probably be my next big leap. Luckily, I found a local Linux group that has meetings and an e-mail list. One of them is a VMware guru and has promised to hold my hand while I screw up my computer yet again trying to install it. :)

And that brings me to my final comment: Find a local Linux group if you can or at least some local Linux users who will let you ask them occasional questions. You can go a long way with online help, and the Ubuntu forums are awesome, but sometimes there is nothing like hands on help.

---

### Post by simonsphotos on 2007-02-20
yea well around here they don't even know what linux is

---

### Post by mhenriday on 2007-02-23
I don't expect **Wine** to be perfect, being well aware that nothing in either the real or the virtual world ever is. But I still retain a certain amount of *a priori* optimism to the effect that if one fiddles around long enough, certain problems are amenable to solution, if not always the first one one imagines. I am encouraged in this by a letter I received from **Mozy**, as follows :
[INDENT]
...

To answer your questions - yes, your files should be compatible with WINE through linux - it just depends on how your restore comes to you. If it is a zip file, you will be able to just unzip it like normal and put the files wherever you would like them to and run them via WINE. If it comes as an exe file, you will need to get a linux version of a program called 7-zip which will allow you to extract the files in the same manner.

As far as Mozy for linux - it will not be happening any time really soon. We are busy keeping up with all the Windows versions as well as adding the ability for Mac as well. It most likely will be available sometime, but it will be a while...

Hopefully that answers your questions! Let us know if you have any more and thanks for referring your friends to us!

Thanks,
James[/INDENT]

I received them, in fact, as exe files, which I saved as per the above. My attempts to open them using the **Wine** emulator have failed, but after receiving James' instructions above, I thought I might be able to use **7-zip** (I have both **p7zip** and **p7zip-full** installed on my machine) to extract the files and _then_ open them with **Wine**. But when, right-clicking on the files, I try to gain access to **7-zip** with which to extract them, I find that the programme is not listed on the extensive menu that then appears. I get the feeling that I'm missing something which is painfully obvious to all experienced **Ubuntu** users, but passes unseen right before my inexperienced eyes. Any suggestions ?...

**Kilz**, I do have **VMware Player** installed on my machine, but I've never used it. Do you think it would be possible to utilise this tool to install a virtual **Windows XP Pro** copy, and if so, could you point me to a tutorial which might help me to do so ? Just as an alternative in the event that, even with the help of tips from the community, I find myself unable to retrieve my lost files with **Wine**....

Henri

---

### Post by Kilz on 2007-02-23
> **mhenriday said:**
> I don't expect **Wine** to be perfect, being well aware that nothing in either the real or the virtual world ever is. But I still retain a certain amount of *a priori* optimism to the effect that if one fiddles around long enough, certain problems are amenable to solution, if not always the first one one imagines. I am encouraged in this by a letter I received from **Mozy**, as follows :
[INDENT]
...

To answer your questions - yes, your files should be compatible with WINE through linux - it just depends on how your restore comes to you. If it is a zip file, you will be able to just unzip it like normal and put the files wherever you would like them to and run them via WINE. If it comes as an exe file, you will need to get a linux version of a program called 7-zip which will allow you to extract the files in the same manner.

As far as Mozy for linux - it will not be happening any time really soon. We are busy keeping up with all the Windows versions as well as adding the ability for Mac as well. It most likely will be available sometime, but it will be a while...

Hopefully that answers your questions! Let us know if you have any more and thanks for referring your friends to us!

Thanks,
James[/INDENT]

I received them, in fact, as exe files, which I saved as per the above. My attempts to open them using the **Wine** emulator have failed, but after receiving James' instructions above, I thought I might be able to use **7-zip** (I have both **p7zip** and **p7zip-full** installed on my machine) to extract the files and _then_ open them with **Wine**. But when, right-clicking on the files, I try to gain access to **7-zip** with which to extract them, I find that the programme is not listed on the extensive menu that then appears. I get the feeling that I'm missing something which is painfully obvious to all experienced **Ubuntu** users, but passes unseen right before my inexperienced eyes. Any suggestions ?...

**Kilz**, I do have **VMware Player** installed on my machine, but I've never used it. Do you think it would be possible to utilise this tool to install a virtual **Windows XP Pro** copy, and if so, could you point me to a tutorial which might help me to do so ? Just as an alternative in the event that, even with the help of tips from the community, I find myself unable to retrieve my lost files with **Wine**....

Henri

I have never had to deal with 7zip but perhaps you can right click on the file and choose extract here without wine. As for Wvware there is a good howto in the Ubuntu wiki. You will need the workstation or the server version to make the virtual machine. The server version is free from what I understand.
[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation) 
[https://help.ubuntu.com/community/VMware/Server?action=show&redirect=VmwareServer](https://help.ubuntu.com/community/VMware/Server?action=show&redirect=VmwareServer)

---

