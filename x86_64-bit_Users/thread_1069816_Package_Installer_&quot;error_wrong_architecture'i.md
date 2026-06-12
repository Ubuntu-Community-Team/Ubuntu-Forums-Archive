---
title: "Package Installer: &quot;error: wrong architecture'i386&quot;"
date: 2009-02-14
forum: x86 64-bit Users
---

### Post by Nerv68 on 2009-02-14
I just Installed Ubuntu and when I try to install a .deb file, the package installer says "error: wrong architecture'i386". I'm on 64-bit Ibex.Could anyone help me out?

---

### Post by Jorge_C on 2009-02-14
You are trying to install a .deb compiled for 32 bits (i386 architecture) but your OS is 64 bits and the package manager is complaining about it. However, the best way to install applications is to use Synaptic or Add/Remove apps; since that way they'll be updated automatically. 

If the app is not in the repositories, you should download it in 64 bits flavour. By the way, what's the app?

---

### Post by Nerv68 on 2009-02-14
The things Im trying to install are Adobe Flash Player and Rainlendar, but I cant find them in Add/Remove applicatons.

---

### Post by oldos2er on 2009-02-14
64-bit Flash is here: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

 Seems there's a 64-bit Rainlendar here: [http://www.rainlendar.net/download/rainlendar2-pro_2.4.b69-1_amd64.deb](http://www.rainlendar.net/download/rainlendar2-pro_2.4.b69-1_amd64.deb)

---

### Post by Jorge_C on 2009-02-14
Flash player is in Add/Remove applications. Make sure it shows all applications. Or, you can install it from terminal, pasting this in a terminal:
```
 sudo apt-get install flashplugin-nonfree
```

Adobe released a 64 bits version of its plugin, but it's still in alpha or beta. Though, it seems to perform better than previous versions. Install instructions [here]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install")

Concerning Rainlendar, I understand it's not available to us using 64 bits OS according to [its FAQ]("http://www.rainlendar.net/cms/index.php?option=com_easyfaq&Itemid=26#faq4"). But I installed the 32 bits version provided (the lite one) and it seems to work well for me, using 
```
 sudo dpkg -i --force-all /path/to/deb/file.deb
```
to install it. I'm using 64 bits Ibex, too.

EDIT: Rainlendar *seems* to work for me this way

---

### Post by debadams on 2009-03-23
> **Jorge_C said:**
> You are trying to install a .deb compiled for 32 bits (i386 architecture) but your OS is 64 bits and the package manager is complaining about it. However, the best way to install applications is to use Synaptic or Add/Remove apps; since that way they'll be updated automatically. 

If the app is not in the repositories, you should download it in 64 bits flavour. By the way, what's the app?

I'm not the original person that put this message in; however, I too have received this wrong architecture message when I tried to download SKYPE.

Where can I go to get the right instructions for downloading to Ubuntu?  Please...
Deb Adams

---

### Post by 3Miro on 2009-03-23
> **debadams said:**
> I'm not the original person that put this message in; however, I too have received this wrong architecture message when I tried to download SKYPE.

Where can I go to get the right instructions for downloading to Ubuntu?  Please...
Deb Adams

Skype is 32-bit only, you will have to install it manually via the terminal:

sudo dpkg -i --force-architecture sype-something.deb

I have done it on my two 64-bit machines and it works.

---

### Post by Jorge_C on 2009-03-23
Hi, have a look at [this how-to]("http://ubuntuforums.org/showthread.php?t=432295&highlight=skype").

Take into account that some of the commands, despite being in the same "code box", are separated with ";". 

Hope this helps

---

### Post by jespdj on 2009-03-24
The easiest way to install Skype on 64-bit is by installing it from the [Medibuntu repository](http://www.medibuntu.org/). They have a package for 64-bit to install Skype along with the necessary dependencies.

---

### Post by dineshrathod2216 on 2009-11-02
Hi, thanks for the flash player 64bit link. Is there Avast x64 antivirus link for .deb package?

---

