---
title: "firefox 3 32bit on 54 bit linux"
date: 2008-06-26
forum: x86 64-bit Users
---

### Post by joey-elijah on 2008-06-26
IS this possible? If so where do you get the 32 bit from, i tried the official website but it wouldn't tell me if it was 32bit or 64 bit... and i don't know how to install tar.bz2's 0_o

Will the flash plugin work for 32bit FF3?

---

### Post by stchman on 2008-06-26
> **joey-elijah said:**
> IS this possible? If so where do you get the 32 bit from, i tried the official website but it wouldn't tell me if it was 32bit or 64 bit... and i don't know how to install tar.bz2's 0_o

Will the flash plugin work for 32bit FF3?

The 64 bit Firefox runs just fine on 64 bit OS.

What are you wanting to do?

The Flash 9 plugin works fine in 64 bit.

---

### Post by joey-elijah on 2008-06-26
just be able to go on youtube etc - i'm downloading as we speak! thanks!

edit: 
erm how do you install a tar.bz2? I've never been able to do this.

Firefox tar.bz2 is sat on my desktop what do i do next?

---

### Post by stchman on 2008-06-26
> **joey-elijah said:**
> just be able to go on youtube etc - i'm downloading as we speak! thanks!

edit: 
erm how do you install a tar.bz2? I've never been able to do this.

Firefox tar.bz2 is sat on my desktop what do i do next?

I told you that the flashplugin-nonfree works fine on 64 bit Ubuntu with 64 bit Firefox.

I guess you don't believe me.

---

### Post by Steveway on 2008-06-26
Firefox 3 should allready be installed if you use Hardy.
If you use an older release then enable the Backports in your installation-sources and get it the usual way through your package-manager.
No need to download anything from websites.

---

### Post by joey-elijah on 2008-06-26
> **stchman said:**
> I told you that the flashplugin-nonfree works fine on 64 bit Ubuntu with 64 bit Firefox.

I guess you don't believe me.

errrm... i do believe you hence why i went and downloaded FF3!

The problem is, i have Firefox 2 32bit atm, the other Firefox got uninstalled when i installed the 32bit edition.

Will check the repos again tho

---

### Post by stchman on 2008-06-26
> **joey-elijah said:**
> errrm... i do believe you hence why i went and downloaded FF3!

The problem is, i have Firefox 2 32bit atm, the other Firefox got uninstalled when i installed the 32bit edition.

Will check the repos again tho

What Ubuntu are you using?

I gather it is not Hardy.

FF3 is in the backports of Gutsy.  Feisty and earlier you will need to download it from mozilla.com.

---

### Post by joey-elijah on 2008-06-26
i am using Hardy 64. As i've a;ready said i removed it to install 32bit ff2.. now i want it back, yet whenever i install it from the repo's in add/remove or synaptic i'm still stuck with 2.0!

---

### Post by stchman on 2008-06-26
> **joey-elijah said:**
> i am using Hardy 64. As i've a;ready said i removed it to install 32bit ff2.. now i want it back, yet whenever i install it from the repo's in add/remove or synaptic i'm still stuck with 2.0!

Make sure you completely remove Firefox 2.

To install Firefox 3 so the following at a terminal:

```
sudo apt-get install firefox-3.0
```

The package for Firefox 2 is firefox-2.

Hope this helps.

---

### Post by math_x3 on 2008-06-26
Flash 9 didn't work very well for me with 64 bit Firefox and java didn't work at all.

In contrary, 32bit Firefox works perfectly with Java & Flash & embedded videos on my 64 bit Linux machine.

---

### Post by joey-elijah on 2008-06-26
how can i make sure i'm getting the 32bit ff3?

---

### Post by WeEatVista on 2008-06-26
I think we are all a bit confused...

Are you wanting both FF3 64bit and FF3 32bit? 

As stchman stated,

> Make sure you completely remove Firefox 2.

In terminal, type 
```
sudo apt-get remove firefox-2
```

Also as stchman stated,

> To install Firefox 3 so the following at a terminal:

```
sudo apt-get install firefox-3.0
```



Then check out this post [http://ubuntuforums.org/showthread.php?p=1174435]("http://ubuntuforums.org/showthread.php?p=1174435")

**MAKE SURE TO READ ALL INSTRUCTIONS CAREFULLY, OR IT MIGHT NOT WORK CORRECTLY!**

Hope this helps,

We Eat Vista

---

### Post by joey-elijah on 2008-06-26
i'm not fussed about firefox 54.

I'll clarify :)

i want firefox on Ubuntu 64 - but with working flash java etc

I have installed the 32lib package thingy, and i have run the 3in1 several times - however it installs 32bit firefox 2 despite saying it's for FF3. 

whenever i try to uninstall firefox 2 via the terminal i'm told that it can't be removed because it's not installed. yet it is.. cos default links in other apps open in it, and going to Help > About shows it to be version 2.

i've downloaded the .deb and will try it out now, thanks!

---

### Post by markbuntu on 2008-06-28
To get flash to work on 64 with firefox you must have:

nspluginwrapper

It is a wrapper for 32bit extensions for firefox like flash and maybe java but I am not sure about that.

Once you get the 64bit firefox reinstalled, get nspluginwrapper from the repos and flash should work. If you know how to get flash10b, it works even better.

---

### Post by onering on 2008-06-28
I think the problem is that you are using 54 bit Linux instead of 64 bit Linux. ;-)

There is a sticky thread that shows you now to install the flash player into 64 bit Ubutu using the ndiswrapper.  

Here is the link to the stick thread: [http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")

In Ubuntu 8.04 64 bit you only need to type the following lines, one at a time, into a terminal window.  I had to reboot the machine and then flash worked fine in Firefox.

sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins/

---

### Post by stchman on 2008-06-29
> **onering said:**
> I think the problem is that you are using 54 bit Linux instead of 64 bit Linux. ;-)

There is a sticky thread that shows you now to install the flash player into 64 bit Ubutu using the ndiswrapper.  

Here is the link to the stick thread: [http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")

In Ubuntu 8.04 64 bit you only need to type the following lines, one at a time, into a terminal window.  I had to reboot the machine and then flash worked fine in Firefox.

sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins/

There is no need to install nspluginwrapper as it is a dependency of flashplugin-nonfree and will be installed automatically.

---

### Post by markbuntu on 2008-06-30
Well yes, if you get flash from the proper repository.

---

### Post by joey-elijah on 2008-07-01
it all got solved, so thanks! 

and yeah i might upgrade to 64bit sometime... heard there's a lot of compatiability issues so... :P

---

