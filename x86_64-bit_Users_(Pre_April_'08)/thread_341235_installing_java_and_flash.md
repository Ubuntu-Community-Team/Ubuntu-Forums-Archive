---
title: "installing java and flash"
date: 2007-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by llorenzo on 2007-01-18
which is the best way to install java and flash on my dell inspiron 1501, it has a amd sempron 3500+ processer?

---

### Post by Kilz on 2007-01-18
> **llorenzo said:**
> which is the best way to install java and flash on my dell inspiron 1501, it has a amd sempron 3500+ processer?

There are 2 methods. Either mess around with the nspluginwrapper that a lot of people have problems with , or install a 32bit version of Firefox and the 32bit plugins.

---

### Post by skinny on 2007-01-18
I'd recommend kuja's excellent [simple64]("http://www.xnowherex.net/simple64/") script. I installed Opera (32bit) using that, and it works peachy, and was very easy.

$

---

### Post by llorenzo on 2007-01-18
would i have any problems just installing 32 bit ubuntu?

these are my specs:

Dell AMD Laptop Model Number 1501

Mobile AMD Sempron 3500+ Processor (1.8GHz/512K)
ATI Radeon Xpress 1150 256MB HyperMemory (integrated)
512 MB of 533 DDR2 RAM (1 Dimm)
60gb 5400 RPM SATA hard drive
DVD+/-RW with Dual Layer DVD+R write capacity
Dell Wireless 1390 802.11g Mini Card (54Mbps)

---

### Post by Lowfront on 2007-01-18
> **skinny said:**
> I'd recommend kuja's excellent [simple64]("http://www.xnowherex.net/simple64/") script. I installed Opera (32bit) using that, and it works peachy, and was very easy.

$



this is only for amd.  Is there an intel version of this?

---

### Post by Kilz on 2007-01-18
> **llorenzo said:**
> would i have any problems just installing 32 bit ubuntu?

these are my specs:

Dell AMD Laptop Model Number 1501

Mobile AMD Sempron 3500+ Processor (1.8GHz/512K)
ATI Radeon Xpress 1150 256MB HyperMemory (integrated)
512 MB of 533 DDR2 RAM (1 Dimm)
60gb 5400 RPM SATA hard drive
DVD+/-RW with Dual Layer DVD+R write capacity
Dell Wireless 1390 802.11g Mini Card (54Mbps)

Im not sure if you will have problems. But some people do have problems running the 32bit version on 64bit hardware. Also there is no such thing as a Linux install where you dont have to do some setup. Getting Flash and java working is rather easy to do. There are a lot of howto's and scripts that will do it. You may want to think about this before doing it and keep in mind you could be jumping from the frying pan into the fire.


> **Lowfront said:**
> this is only for amd.  Is there an intel version of this?

Anything labeled AMD64 for Ubuntu will also work on 64bit intel hardware to my knowlage.

---

### Post by anilat3r on 2007-01-18
I just tried to install Flash on my 64 bit installation and it didn't work. I received the following error:

```

sean@SeansComputer:~$ cd /install_flashplayer_9_linux
bash: cd: /install_flashplayer_9_linux: No such file or directory
sean@SeansComputer:~$ ls
Desktop   install_flash_player_9_linux
Examples  install_flash_player_9_linux.tar.gz
sean@SeansComputer:~$ cd /install_flash_player_9_linux
bash: cd: /install_flash_player_9_linux: No such file or directory
sean@SeansComputer:~$ cd install_flash_player_9_linux
sean@SeansComputer:~/install_flash_player_9_linux$ ls
flashplayer-installer  flashplayer.xpt  libflashplayer.so  Readme.txt
sean@SeansComputer:~/install_flash_player_9_linux$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

sean@SeansComputer:~/install_flash_player_9_linux$ 


```

I am a noob still with Linux, but as far as I know I did everything correctly, I have installed Flash a few times before. Is there an x64 download available or is it not written yet?

Also, just for reference I had 32bit installed on my Athlon 64 3700 PC and it worked flawlessly. Don't mean it will work with all systems but just to give you my own personal experience.

---

### Post by Consumed on 2007-01-18
There is no official x64 version from Adobe at this time.  ndiswrapperplugin is your best bet.  I have yet to do this, mainly because I could care less for getting flash working.  Just search for help with flash plugin using ndiswrapper.

---

### Post by anilat3r on 2007-01-18
Thanks Consumed, I already have simple64 installed and will see how that works, otherwise your advice will be followed. Thank again, and if things aren't working neither do I care so much, however I'm just trying to get more fluent with Linux so I need all the practice I can get.

---

### Post by amd-64 on 2007-01-19
I installed the adobe flash 9 on firefox or swiftfox 32-bit. 

1. Download the install_flash_player_9_linux.tar.gz file from [www.adobe.com]("http://www.adobe.com") and 
exit your browser(s). Run the following

```
tar zxvf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
sudo linux32 flash_installer 
```
If you do not have linux32 installed, use  sudo apt-get install linux32 to install it.
 
2. Note that the script will require you to enter the path of your firefox installation
either /usr/lib/firefox, /usr/lib/mozilla, .. Mine is at /opt/swiftfox 

3. Check what plugins are installed by entering the url [HTML]about:plugins[/HTML] in your firefox address bar. You should remove older flash plugins from the plugins directory in the program directory (e.g. /usr/lib/firefox) or in your home directory (e.g. /home/yourname/.mozilla/../plugins). 

The flash 9 player works well and certainly is more stable than nspluginwrapper and gnash.

---

### Post by Sasquatch2000 on 2007-01-19
Surely there has to be an easier way. 

Isn't there something you can just click (like in Windows)?

I'm trying to explain this to someone over the phone. 

6.10


Thanks.

---

### Post by Sasquatch2000 on 2007-01-19
I saw the [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) page, which at least looks a "little" easier if all one has to do is copy/paste everything on that page and it works.

Why can't this be made to work seamlessly? THIS is why linux is still not caught up to Windows yet. (Well, this and configuring wireless, video, and printers.)

---

### Post by Kilz on 2007-01-19
> **Sasquatch2000 said:**
> I saw the [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) page, which at least looks a "little" easier if all one has to do is copy/paste everything on that page and it works.

Why can't this be made to work seamlessly? THIS is why linux is still not caught up to Windows yet. (Well, this and configuring wireless, video, and printers.)

I suggest you try and install wireless and printer drivers into 64bit windows and then come back and tell me about Linux.

---

### Post by amd-64 on 2007-01-20
> **Sasquatch2000 said:**
> I saw the [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) page, which at least looks a "little" easier if all one has to do is copy/paste everything on that page and it works.

Why can't this be made to work seamlessly? THIS is why linux is still not caught up to Windows yet. (Well, this and configuring wireless, video, and printers.)

This method appear to be for 32-bit ubuntu, and will only work  on 64-bit systems if you installed a 32-bit firefox in the default location /usr/lib/firefox. 

I could not understand why you would want to do this manually, since the install script will do it for you.

---

### Post by Sasquatch2000 on 2007-01-22
I am pretty sure I am trying to install flash in 32 bit Ubuntu. 

Why all the antagonism towards getting an answer to the question? 

It doesn't seem to work, or something is wrong. Is there an installer script, as you allude to which makes this easier? If so, I haven't found it.

Thanks.

---

