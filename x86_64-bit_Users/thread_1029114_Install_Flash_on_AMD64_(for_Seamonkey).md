---
title: "Install Flash on AMD64 (for Seamonkey)"
date: 2009-01-03
forum: x86 64-bit Users
---

### Post by Macamba on 2009-01-03
Hi,

Yes, I know there is a stick about installing Adobe Flash on an AMD64. I even executed the instructions. I have downloaded and extracted libflashplayer.so to my bin directory (for now) and copied it to the newly created directory plugins in ~/.mozilla. But when I start my Seamonkey browser (Netscape rules!, sorry for the plug :-D) no movie is shown on YouTube, and no Flashy entry is added to my 'Helper Applications' (menu: Edit -> Preferences -> Navigator -> Helper Applications). 

I looked at the owner of libflashplayer.so, and it is "username" (fill in the name I use to log in on Ubuntu). I tried a 
```
sudo cp libflashplayer.so ~./mozilla/plugins
``` the command ls -la gave the same names.

Anyone know what other steps are available for me? 

<confused mode>
Macamba
</confused mode>

---

### Post by halovivek on 2009-01-03
hi 
welcome to ubuntu fourms
you can try by reading this thread. i have solved using this one.
[http://ubuntuforums.org/showthread.php?t=1024873](http://ubuntuforums.org/showthread.php?t=1024873)
please reply after trying this. we can help you more

---

### Post by Macamba on 2009-01-04
Hi halovivek,

Thanks for your reply. It seems I'm on the right track using:
```
sudo apt-get install flashplugin-nonfree
```
If I still have a problem I will report about it.

I will reboot my browser and look what result that will give. The only thing I'm wondering about is that I get the following installed:
```
flashplugin-nonfree ia32-libs lib32asound2 lib32gcc1 lib32ncurses5
  lib32stdc++6 lib32z1 libc6-i386 nspluginwrapper

```

To me that looks like the 32bits stuff gets installed, not the 64bits. But if it works, I will not grumble about it. 

Macamba

---

### Post by Kilz on 2009-01-04
> **Macamba said:**
> Hi halovivek,

Thanks for your reply. It seems I'm on the right track using:
```
sudo apt-get install flashplugin-nonfree
```
If I still have a problem I will report about it.

I will reboot my browser and look what result that will give. The only thing I'm wondering about is that I get the following installed:
```
flashplugin-nonfree ia32-libs lib32asound2 lib32gcc1 lib32ncurses5
  lib32stdc++6 lib32z1 libc6-i386 nspluginwrapper

```

To me that looks like the 32bits stuff gets installed, not the 64bits. But if it works, I will not grumble about it. 

Macamba

The flash plugin is in fact 32bit, the nspluginwrapper lets it work with your 64bit browser. But it still needs 32bit support files.

---

