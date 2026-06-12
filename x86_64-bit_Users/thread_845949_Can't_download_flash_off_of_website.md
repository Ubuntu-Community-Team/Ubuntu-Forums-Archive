---
title: "Can't download flash off of website"
date: 2008-07-01
forum: x86 64-bit Users
---

### Post by lukasz101 on 2008-07-01
Alright. Just to clear things up, i can download flash using the internet browser and what not.
From there i try to install it and uh oh problem 
```
 ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

```

Thats fine. So i tried using synaptic package manager to download it and install the flash plugin. 
It wont download from the website.

Okay so i try the install guide i found on the forums.
First few steps work without a hitch. 
Then i get this (same thing as was happening above)

```
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--02:09:46--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.0.4
Connecting to fpdownload.macromedia.com|72.246.0.4|:80... failed: Connection timed out.
Retrying.

--02:12:56--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
  (try: 2) => `./install_flash_player_9_linux.tar.gz'
Connecting to fpdownload.macromedia.com|72.246.0.4|:80...

```

This just keeps on happening.

Sorry for the long post.
Thanks for the help.

PS: I am using Wubi.
PPS: I prefer ubuntu over windows any day, just only thing holding me back at the moment are the slight problems i encounter. I got past all of them except for this one.

---

### Post by philinux on 2008-07-01
Open synaptic package manager and install

ubuntu-restricted-extras

This will install flash, java and a few other important things.

---

### Post by Sef on 2008-07-01
Read [Kliz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490") to install flash on 64-bit Ubuntu.

---

### Post by Sef on 2008-07-01
> Open synaptic package manager and install

ubuntu-restricted-extras

This will install flash, java and a few other important things. tras

That will not work.  Flash and Java are only for 32-bit systems.

---

### Post by pixel :-) on 2008-07-01
sudo apt-get install flashplugin-nonfree
it will install the other stuff that it needs

in antisipation of other stuff you whant to install 

for java 32 bit
sudo apt-get install ia32-sun-java6-bin

if you need to install 32 bit applications, a start is 
sudo apt-get install ia32-libs
you'll probably need some other stuff,depending on the aplication.

---

### Post by philinux on 2008-07-01
> **Sef said:**
> That will not work.  Flash and Java are only for 32-bit systems.

It's what I used and I'm running 64 bit.

---

### Post by lukasz101 on 2008-07-01
> **philinux said:**
> Open synaptic package manager and install

ubuntu-restricted-extras

This will install flash, java and a few other important things.

Okay i did that, most of it installed except for flash.
Reason being the connection kept on timing out as before when it got to downloading it from the website.

---

### Post by lukasz101 on 2008-07-01
Sorry double post by accident.
i'll make use of this though...

 
i followed the install guide by Kilz
and when i typed in  sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns in the terminal i got this.
I did this earlier but i tried again and i'm deciding to post what i got.
From what i can tell it seems that flash is downloaded but then when it tries setting it up it has to connect to the website
and from there the connection times out and then retries with the same results

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
nspluginwrapper is already the newest version.
flashplugin-nonfree is already the newest version.
lib32nss-mdns is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--13:05:41--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.7.0.4
Connecting to fpdownload.macromedia.com|96.7.0.4|:80...  
```

---

### Post by Yellow Pasque on 2008-07-02
Looks like you had a bad install on the flash plugin. Follow Kilz's guide on purging a failed install and then try again.

---

### Post by stchman on 2008-07-02
Just install the following package:

```
sudo apt-get install flashplugin-nonfree
```

It works great in 64 bit HH with Firefox.

---

### Post by lukasz101 on 2008-07-06
I dont think i had a bad install of anything.
I couldnt connect to that website for some reason.
But now i'm in a different country and it works fine here.
Everything installed without a hitch.
Thanks for the help

---

