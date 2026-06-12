---
title: "Where does the file need to be if I want to run it in the Terminal??"
date: 2009-05-30
forum: x86 64-bit Users
---

### Post by JerichoDefeated on 2009-05-30
(Solved)I need to install flash 10 on my 64bit machine but in order to do that I need to run the 32bit flash.deb file in the terminal. Using the 

[FONT=monospace]
[/FONT]sudo dpkg -i --force-architecture flash.deb


Command. But when I run it, It says this -

cannot access archive: No such file or directory

The file is currently on my desktop, but i don't know if it should be somewhere else.

PS I'm very new to linux but willing to learn.

Thanks, Josh

---

### Post by Rhubarb on 2009-05-30
The easiest solution is to move the deb file into your home folder, then run the terminal command.

Alternatively, you could in a terminal:
```
cd Desktop
```
Then run your command to install the deb.

Running "cd Desktop" will change the current directory in your terminal to your Desktop folder.

The terminal is a very powerful tool, there's much to learn from it, and can be quite fun too :)

---

### Post by meho_r on 2009-05-30
It have to be in present working directory (try command: pwd). So, if your .deb file is located on your Desktop, make sure your pwd is Desktop. By default, when you open Terminal, pwd is your home directory, so to get to your Desktop directory, type command: ```
cd Desktop
```

EDIT: Hehe, Rhubarb beated me for couple of seconds :)

---

### Post by _Purple_ on 2009-05-30
You have to go to desktop using this command
```
cd ~/Desktop
```

Then run that command. ~ is your home directory. It is same as /home/username where username is your own username.

---

### Post by pixel :-) on 2009-05-30
Whoo NO NO NO, Guys you should have read what he is doing

You can't install flash this way. Install the following manually and uninstall what you did.

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

---

### Post by JerichoDefeated on 2009-05-30
Thanks Guys, I did what the first 3 people said to do and it seems to be working fine. I'll refer to the 4th post if I have any further problems.

Thanks, Josh:)

---

### Post by meho_r on 2009-05-30
But why installing 32bit flash? You have 64bit in repos available.

---

### Post by cariboo on 2009-05-31
Even if you were to install the 32bit version of flash, why not install it from the repositories, that way all the delendencies are met.

---

### Post by Random-penguin on 2009-05-31
I am beginning to get the impression that newbies (and I'm trying not to sound condescending!!) are not realizing the wonders of the repositories and using synaptic / apt are such great powerful tools for package installs. We, in general don't install things the windows way, which is one reason for Linux's good security record.

My point is could there be a little tutorial or something in the default install? There seem to be quite a few posts from people not aware of this. What do people think??

---

### Post by cmay on 2009-05-31
> **Random-penguin said:**
> I am beginning to get the impression that newbies (and I'm trying not to sound condescending!!) are not realizing the wonders of the repositories and using synaptic / apt are such great powerful tools for package installs. We, in general don't install things the windows way, which is one reason for Linux's good security record.

My point is could there be a little tutorial or something in the default install? There seem to be quite a few posts from people not aware of this. What do people think??
i am one of the few that after a couple of month had managed to get a hold af a malicius file that erased half of my installtation and i got it by using the windows way (any random website )of installing instead of the linux way (synaptic). 

i think its a great idea. today i see a lot of post that has teh questions about flash and other codecs and they dont know how to get the things working from repositories. 

the funny thing is that even after i used linux in over a couple years i never found all the software in those repositories yet. i recently found some programs i did not even know existed in debian just by adding for one time only the media repositories in debian etch. 
i was amazed to find some new audio recording software i did never see before. 
its a shame that people dont learn using repositoreis as one of the first things.

---

### Post by Random-penguin on 2009-05-31
Thank you, Cmay. The more I think about it, the better this idea seems. It would take some of the pressure off the forum and make Linux under Ubuntu a much smoother transition. But how do you submit a new idea to the development team??

---

### Post by loomsen on 2009-06-01
> **Random-penguin said:**
> But how do you submit a new idea to the development team??

New idea - like - reading manuals and HowTos?

---

### Post by cariboo on 2009-06-01
I seem to remember seeing somethng from the current UDS where they were going to include a start up video during installation, that explains some of the features available with Ubuntu.

---

### Post by Random-penguin on 2009-06-01
> **loomsen said:**
> New idea - like - reading manuals and HowTos?


I'm sorry but that sounds like the old RTFM days. Surely if newbies are posting similar problems on the forums it says something. Surely a helping hand to ease a transition to a new OS is good. Maybe my idea is not original but it is not there at the moment and I think it needs looking into. If only to highlight certain key points to get the newbie going in the right direction... possibly with links to on-line Ubuntu Documentation.

The start up video sounds cool.... but what about language issues..... could become a nightmare in supporting those different mother tongues!!! :D

---

### Post by JerichoDefeated on 2009-06-02
> **meho_r said:**
> But why installing 32bit flash? You have 64bit in repos available.

I looked for a 64bit version of flash 10 but couldn't find one, all I could find was the 32bit version, and even though Syn had it I can't install it from Syn because Syn knows I am running a 64bit OS, so I downloaded it from the Adobe website. If you know of a 64bit version please let me know.

Oh, and by the way I agree. even though I am new to Ubuntu, I think everyone should check the Synaptic Installers before downloading a file from a website, which is what I try to do.

---

### Post by oldos2er on 2009-06-02
64-bit flash is here: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

---

### Post by rookcifer on 2009-06-02
> **JerichoDefeated said:**
> I need to install flash 10 on my 64bit machine but in order to do that I need to run the 32bit flash.deb file in the terminal.

No, you don't.  Adobe has 64 bit flash for Linux now. 

Read [this tutorial]("http://ubuntuforums.org/showthread.php?t=766683").  It will show you how to install just about every possible media codec you need.  You do not have to download anything from Adobe.  Ubuntu has all of this stuff in its repositories.

If you want a quick command for installing all of the media codecs, including flash, then do this (assuming you are on Ubuntu 64 bit):

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar
```

---

### Post by Anubis on 2009-06-03
> **pixel :-) said:**
> Whoo NO NO NO, Guys you should have read what he is doing

You can't install flash this way. Install the following manually and uninstall what you did.

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

Amen!:(

---

### Post by Anubis on 2009-06-03
> **loomsen said:**
> New idea - like - reading manuals and HowTos?

Amen!

---

### Post by JerichoDefeated on 2009-06-14
Thanks alot guys I used that quick command and it worked like a charm.:D

---

### Post by cariboo on 2009-06-14
Just a note: there is a sticky at the top of the page that shows you how to install flash.

---

### Post by JerichoDefeated on 2009-06-16
at the top of which page?? maybe I'm just not looking close enough.

---

### Post by _Purple_ on 2009-06-16
> **JerichoDefeated said:**
> at the top of which page?? maybe I'm just not looking close enough.

This page:
[http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

This thread:
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by JerichoDefeated on 2009-06-17
OK, thanks/

---

