---
title: "Installing Flash 10.1 x32 beta on kamic x64"
date: 2009-11-17
forum: x86 64-bit Users
---

### Post by PyjamasBeforeChrist on 2009-11-17
Thought I had this but no!

below is the original steps I though had done it. I am a bit novice at linux. maybe I am missing something simple. It seems to run but slow and gerky again.

Any ideas? 

original post
---------
Hi all,

I am brand new to linux and ubuntu but just figured out how to get the new Flash 10.1 beta with GPU off load of the video working on my x64 karmic and thought I would share it.

1. go here [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/) and click on the "Get the Flash Player 10.1 prerelease" link. Download the "flashplayer10_1_p1_linux_111709.tar.gz" file and extract the "install_flash_player_10_linux" folder it contains. 

2. from Synaptic install the "flashplugin-installer"

3. in terminal remove the libflashplayer.so file that the Synaptic install has done for you. 
sudo rm /usr/lib/flashplugin-installer/libflashplayer.so

4. then in terminal add the libflashplayer.so from you download
sudo cp /where_you_have_extracted/install_flash_player_10_linux/libflashplayer.so /usr/lib/flashplugin-installer/

then enjoy the wonder of HD in flash 10.1 being processed by your GPU instead of the CPU! My new atom 330 ion is loving it.

Note. it appears that this is the x32 bit version of flash 10.1 (x64 not yet released) running only but it work well for the video. I found flash function/buttons worked better under the alpha release of Flash Player 10.0.32.18 for 64-bit Linux found here [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html) but the video is much better with the x32 beta per above.
-----------

---

### Post by darco on 2009-11-17
First I would wait for the x64 version to be released or install the perfectly working Alpha version.
Then follow this link to easily install Flash

[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)


darco

---

### Post by HappyFeet on 2009-11-17
OK, settle down. Since you are using 64bit ubuntu, we're going to go a different route.

First, uninstall flash. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

I do this, and it works every time. Let us know how it goes.

---

### Post by Yellow Pasque on 2009-11-17
If you want to use the 32-bit Flash 10.1, you have to manually wrap the libflashplayer.so file with nspluginwrapper (after you install the nsplguinwrapper package). Of course, you should uninstall any existing Flash player first.

---

### Post by clhsharky on 2009-11-17
HI

Sorry no hardware acceleration on Linux! Only windows.


Adobe Flash Player 10.1 Beta For Linux
[http://www.phoronix.com/scan.php?page=news_item&px=NzcxMg](http://www.phoronix.com/scan.php?page=news_item&px=NzcxMg)

---

### Post by TenPlus1 on 2009-11-17
Distortions when playing youtube movies, will wait until it's out of beta before upgrading flash...

---

### Post by HappyFeet on 2009-11-17
> **TenPlus1 said:**
> Distortions when playing youtube movies, will wait until it's out of beta before upgrading flash...

It's probably because of your video card. I've been using 64bit flash on 3 different computers without issue.

---

### Post by PyjamasBeforeChrist on 2009-11-17
> **clhsharky said:**
> HI
 
Sorry no hardware acceleration on Linux! Only windows.
 
 
Adobe Flash Player 10.1 Beta For Linux
[http://www.phoronix.com/scan.php?page=news_item&px=NzcxMg](http://www.phoronix.com/scan.php?page=news_item&px=NzcxMg)
 
Thanks, it looks like I will need to wait a bit longer for my flash to use the GPU instead of CPU for its Video :(
 
Interestingly my above steps did actual get flash video playing and it was a noticable improvement in the video performance. But it came with other issues the 64bit Alpha version doesnt have (ie poor response to buttons and controls in YouTube)
 
I have reverted back to the 64Bit Alpha for now [[COLOR=#000000]http://labs.adobe.com/technologies/f...r10/64bit.html[/COLOR]]("http://labs.adobe.com/technologies/f...r10/64bit.html")
The problem here is my intel atom 330 cpu just doesnt cut it for HD YouTube or Flash based internet TV and I need it offloaded to the Nvidia ION GPU which will not happen on windows or Linux until 10.1 Flash is available.
 
Thanks every one for thier thoughts
 
I will install the 10.1beta on my Windows 7 install on the same PC and get a bench mark. Hopefully Adobe include the H.264 decoding offload to the GPU in the final release next year for Linux and not just Windows. Fingures crossed.
 
Cheers

---

