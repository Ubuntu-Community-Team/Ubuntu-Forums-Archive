---
title: "Macromedia Flash Plugin not available"
date: 2007-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by kevil99 on 2007-05-15
Macromedia Flash Player  IS in my add remove lst
But wont allow me to install.
when i try to check it it wont do so
I need it so i can view my website.
Any suggestions?

---

### Post by kevil99 on 2007-05-15
heres what it reads in my add remove when i select to install it

The use, modification and distribution of Macromedia Flash plugin is restricted by copyright or by legal terms in some countries.
Macromedia Flash plugin cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by John.Michael.Kane on 2007-05-15
Since your running ubuntu 64bit you will need to install flash via this method.
[ Firefox with Flash for  AMD64]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java")

---

### Post by reidms on 2007-05-15
Hmmm it seems like it is not offering a 64bit  flash player.

Which version of Ubuntu do you have, and did you install 32 bit or 64 bit version of Ubuntu?

---

### Post by kevil99 on 2007-05-15
7.0.4 amd64

---

### Post by John.Michael.Kane on 2007-05-15
> **kevil99 said:**
> 7.0.4 amd64

You will have to use the method posted above, this will will allow you to have flash.

---

### Post by kevil99 on 2007-05-15
kevil99@kevil99-desktop:~$ cd ~/Desktop
kevil99@kevil99-desktop:~/Desktop$ tar -xzvf install_flash_player_9_linux.tar.gzinstall_flash_player_9_linux/
install_flash_player_9_linux/Readme.txt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
install_flash_player_9_linux/flashplayer.xpt
kevil99@kevil99-desktop:~/Desktop$ sudo mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib32/firefox32/plugins
mv: cannot move `/home/kevil99/Desktop/install_flash_player_9_linux/libflashplayer.so' to `/usr/lib32/firefox32/plugins': No such file or directory
kevil99@kevil99-desktop:~/Desktop$

---

### Post by John.Michael.Kane on 2007-05-15
> **kevil99 said:**
> kevil99@kevil99-desktop:~$ cd ~/Desktop
kevil99@kevil99-desktop:~/Desktop$ tar -xzvf install_flash_player_9_linux.tar.gzinstall_flash_player_9_linux/
install_flash_player_9_linux/Readme.txt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
install_flash_player_9_linux/flashplayer.xpt
kevil99@kevil99-desktop:~/Desktop$ sudo mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib32/firefox32/plugins
mv: cannot move `/home/kevil99/Desktop/install_flash_player_9_linux/libflashplayer.so' to `/usr/lib32/firefox32/plugins': No such file or directory
kevil99@kevil99-desktop:~/Desktop$

Use the Browser Install Script method. as it makes things simpler. This is the method i just used, and it installed fine.

---

### Post by kevil99 on 2007-05-15
Im sorry i dont follow
browser install script method?

---

### Post by ronocdh on 2007-05-15
> **kevil99 said:**
> Im sorry i dont follow
browser install script method?
Plissken means that you can download Kilz's script and run it in the terminal. This automates the process entirely, so you don't have to enter any commands, just answer a few brief prompts about your preference of browser. Good luck.

---

### Post by John.Michael.Kane on 2007-05-16
> **kevil99 said:**
> Im sorry i dont follow
browser install script method?

Here [Feisty Users Browser Install Script]("http://home.comcast.net/~next/f-base-plugins-0-1.tar.gz")

Download the above file to your desktop. Right click on the file, and select extract here.

You will then see a folder on your desktop label base-plugins open this folder.

On the inside of said folder you will see two files. Their names listed below.

1)base-plugins <-------This will install flash, and the needed files. You double click it to run it, and Select "Run In Terminal".

2)Readme <-------This will explain what above file does, and how you use it ect.

---

### Post by kevil99 on 2007-05-16
THX SD

This finally resolved my issue.
I basically wound up with a new browser.

Thanks to you for patiently helping a clueless newb.
Ive been doing my part in speading the word about
Ubuntu. So be forewarned even more clueless pll will be around..lol

You are what makes free distros awesome!

---

### Post by John.Michael.Kane on 2007-05-16
> **kevil99 said:**
> THX SD

This finally resolved my issue.
I basically wound up with a new browser.

Thanks to you for patiently helping a clueless newb.
Ive been doing my part in speading the word about
Ubuntu. So be forewarned even more clueless pll will be around..lol

You are what makes free distros awesome!

Your welcome kevil99.

I'm just one guy. This whole forum, and the others like it is really what makes free distros awesome.

If you have any further questions or problems please post.

---

### Post by rootkowski on 2007-05-16
hello!

i followed the advice and ran the script, answered all questions accordingly and it didn't seem to work. Do I have to uninstall the 64-bit version of firefox first? Is that the problem?

Thanx a lot for help! :-)

---

### Post by John.Michael.Kane on 2007-05-16
> **rootkowski said:**
> hello!

i followed the advice and ran the script, answered all questions accordingly and it didn't seem to work. Do I have to uninstall the 64-bit version of firefox first? Is that the problem?

Thanx a lot for help! :-)

If your doing this on ubuntu 7.04 feisty

Open synaptic, and make sure the **ia32-libs-gtk** file is installed, if it's not then install it, and re-run the script.

You should be golden.

---

### Post by rootkowski on 2007-05-16
I run feisty for amd64. I checked and the ia32-libs-gtk is installed. So should I uninstall 64-bit firefox and then re-run the script?

Sorry if I'm tiring with not being able to understand. :-) I'm still learning the basics

Thanx again

---

### Post by John.Michael.Kane on 2007-05-16
> **rootkowski said:**
> I run feisty for amd64. I checked and the ia32-libs-gtk is installed. So should I uninstall 64-bit firefox and then re-run the script?

Sorry if I'm tiring with not being able to understand. :-) I'm still learning the basics

Thanx again

Theres no need to uninstall firefox.


Double click on the script, and copy paste here the output msg that it gives.

---

### Post by rootkowski on 2007-05-16
I'm actually blushing. Stupid me. :-)
The reason why it didn't work is that I didn't extract the package on the desktop but in another folder. So the script was looking for folders and files within the desktop, and those of couse did not exist. Well, now I have it all nicely running with all plugins installed.
I'm sorry for wasting your time and I'm very greatful for all your help. 
Next time I will just remember that even if something runs automaticly it might be a good idea to check what it's actually doing.

Thanks again!!!

---

### Post by John.Michael.Kane on 2007-05-16
> **rootkowski said:**
> I'm actually blushing. Stupid me. :-)
The reason why it didn't work is that I didn't extract the package on the desktop but in another folder. So the script was looking for folders and files within the desktop, and those of couse did not exist. Well, now I have it all nicely running with all plugins installed.
I'm sorry for wasting your time and I'm very greatful for all your help. 
Next time I will just remember that even if something runs automaticly it might be a good idea to check what it's actually doing.

Thanks again!!!

There was no wasting of time. I'm glad you figured out what the issue was.

If you have any other problems just post a thread..

---

### Post by rootkowski on 2007-05-16
Thank You a lot! :-)

---

