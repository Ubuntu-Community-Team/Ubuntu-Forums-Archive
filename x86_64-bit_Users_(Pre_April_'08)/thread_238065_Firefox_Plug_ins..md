---
title: "Firefox Plug ins."
date: 2006-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by bender[OO] on 2006-08-17
Hey, I recently installed Ubuntu, and am very new to Linux.

I want to watch streamed videos from websites such as [www.break.com](www.break.com) [www.thatvideosite.com](www.thatvideosite.com) [www.filecabi.net](www.filecabi.net) but I don't have the flash plug in for it.

So I downloaded the flash plug in from [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) but I can't install it.  I extract the contents to a file on my desktop and then I go to my terminal and I type in exactly what it says I'm supposed to do in the readme.txt which is ./flashplayer-installer but then I get

tyson@tyson-desktop:~$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory

How do I go about installing the flash player?

Thank you.

---

### Post by louis_nichols on 2006-08-17
Actually, there is an easier way to install it. There is a package in the repos that will do this automatically for you.

So, make sure you have all repositories enabled (instructions [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html")) and then in synaptic search for and then install the package called *flashplugin-nonfree*.

As for the way you've already tried, the reason it didn't work is that you issued the command from within another folder than the one where you saved the file. When you open a terminal window, it will most likely place you in the home folder, which is indicated by a ~ character at the beginning (this is just a place holder for the absolute path /home/*user-name*/). But if you saved the flash installer in another folder (Desktop, or Downloads or something) then you have to navigate to that folder, then issue the command. So, say you saved it on your desktop. You should start a terminal and then issue the following commands (# just represents your command prompt - you don't have to type it):

```
#cd Desktop
#./flashplayer-installer

```

It's just like in a visual file explorer: you have to navigate to where the file is before you can double click on it.

Of course, there are several ways to do this. For example, the first command can also be:
cd /home/*user-name*/Desktop
or
cd ~/Desktop

At the same time, the executable can be launched using directly the command:
Desktop/flashplayer-installer
or
/home/*user-name*/flashplayer-installer

Now, all this was for general info. For installing the plugin, I strongly recommend the package in synaptic, as there is some more configuring involved (and also the installer has to be  made executable, which is very easy, but a different story).

---

### Post by bender[OO] on 2006-08-17
Thank you for the quick and informative reply!  I don't know if I have synaptic though.  I went to applications, add/remove and seached for synaptic but It wouldn't let me download it.  Also I enabled those things before.  The multiuniverse and the other thing...Thanks for the help again!

---

### Post by louis_nichols on 2006-08-17
Synaptic is unavoidably in every Ubuntu so far. You'll find it under

System>Administration>Synaptic package manager

:) Ubuntu couldn't live without it.

Still, they're thinking to replace it, from what I gather. Or, at the vrey least, add some features which it needs (quite desperately, I'd say). But, again, that's a different story.

---

### Post by Kilz on 2006-08-17
You may have a problem installing flash as Louis Nichols suggests. The problem is that the flash plugin is 32bit. The Firefox that is installed with the AMD64 version is 64bit. The plugin wont work with the browser. 
That's not to say it cant be done. But this is one area that you have to do a little extra work with the 64bit version. Simply visit the Firefox/flash/java link in my signature. The howto/script will install 32bit firefox with flash and java.

---

