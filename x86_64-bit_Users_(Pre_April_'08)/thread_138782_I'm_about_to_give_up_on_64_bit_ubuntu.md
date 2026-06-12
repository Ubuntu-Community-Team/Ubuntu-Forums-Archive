---
title: "I'm about to give up on 64 bit ubuntu"
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by otake-tux on 2006-03-02
I managed to get dvd playback, the graphics card works, sounds great.

but wireless is an imposible.  I tried the linuxant driver and it did not work.  I'm out of ideas.  I cannot use the 32 bit drivers in 64 bit mode. So if I stay in 64 bit, I wont have wireless.


I know that its not ubuntu's fault. Its broadcoms.  It's still a bummer.  At least PC users can apreciate 64 bit linux.  I guess I'll have to wait till windows vista comes out. maybe then more 64 bit drivers will be availeble.

---

### Post by arctic on 2006-03-02
If this is so much of a headache, I suggest you perhaps try other 64-bit Linux system (Fedora, Mandriva and Gentoo come to my mind), hoping that they will perhaps work with your card. The better option is imho to stick to the 32-bit version. After all, it is not so much of a speed-drop off.

---

### Post by amd-64 on 2006-03-03
You should check this site. Wireless works well with ndiswrapper. 

[http://http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html]("http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html")

---

### Post by handy on 2006-03-04
I've used both 32bit & 64bit Ubuntu, & 32bit is sooo much easier to live with.

I'll check each new 64bit version of Ubuntu until the time comes when 32bit is superceded like 16bit was...

64bit is inevitable!  :KS :KS :KS

---

### Post by equilibrium on 2006-03-04
I just got a acer aspire 5024wlmi with a broadcom and I got it working without too much hassle using the ndiswrapper+win64 drivers :-k seemed to work first try.

The best guide I found was [here](https://wiki.ubuntu.com/WifiDocs/Acer5021WLMi_Amd64?action=show&redirect=WiFiHowto%2FAcer5021WLMiConfiguration)

I used the latest ndiswrapper manually compiling it instead of using the one on apt. Seems ok using gcc-3.4 as gcc-4.0 doesn't seem to work ;)
```
wget http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.7.tar.gz
tar xvzf ndiswrapper-1.7.tar.gz
cd ndiswrapper-1.7
make
sudo make install
```

---

### Post by mentallysilent on 2006-03-05
I suppose you have a Broadcom card most probably the 43xx series. Do not fret my friend they all work with ndiswrapper...give it a try...from what I understand ndiswrapper comes standard with The Breezy Badger so all you gotta do is get the drivers from linuxant (i think)...I use Gentoo 64 bit on an eMachines 6805 and wireless works quite fine...I'm guessing it would work under Ubuntu as well.

---

### Post by Aithnea on 2006-03-05
I have a broadcom wireless card in my Acer Asper 5000 laptop and have been having nothing but headaches when it comes to trying to install ndiswrapper.  I've tried everything that I can think of and nothing seems to work.  I have been following <a href="http://yuri.at/go/amd64/">this</a> tutorial.  I can get to the point where it says to use the ndiswrapper command and it comes back with the  the ndiswrapper command not found error.  So I tried what the ndiswrapper wiki suggested: /usr/sbin/ndiswrapper -i filename.inf only to get the same error.

I like using the 64bit Ubuntu, but I'm starting to find that a lot of the programs that I require use of don't really work so well (I still haven't figured out how to get flash or java to work a hundred precent either).

---

### Post by equilibrium on 2006-03-05
[QUOTE=Aithnea]I have a broadcom wireless card in my Acer Asper 5000 laptop[/QUOTE]

I've made a [howto](http://ubuntuforums.org/showthread.php?t=140007) on the laptop part of this forum, as I noticed a lot of the sources either didn't have all the info or didn't leave you with it 100% working.

I put in literally everything I did on my 5024wlmi with amd64.

---

### Post by otake-tux on 2006-03-13
I did give up. Installed 32 bit ubuntu. Felt bad about not using my cpu for what its for so I decided to try again.  Installed 64 bit ubuntu again.  Grabed ndiswrapper from the repositories , downloaded the 64 bit driver for my wireless and it worked!

Now I'm working on power management (which for some reason doesnt work), win32 codecs and compiling java.  Java I can do, but I have no idea on what to do for the other two.  Any help would be apreciated.

---

### Post by Bandit on 2006-03-13
Xine is better on 64bit systems. You can grab Xine and Totem from my website listed below. I still only have totem 1.3.1, its compiled for Xine. Xine has been compiled with everything enabled. To get DVDs to work all you nee is to compile libdvdcss using --prefix=/usr and your good to go.
Cheers,
Joey

---

### Post by blurredbrain on 2006-03-13
ACPI is weird.  I put in the Live CD, let it boot, then rebooted normally and for some reason I absolutely can't fathom ACPI started working correctly.

Oh, I was having problems with my system shutting down during boot giving me an error, telling me my internal temperature was at 255 degrees.

---

### Post by otake-tux on 2006-03-14
[QUOTE=Bandit]Xine is better on 64bit systems. You can grab Xine and Totem from my website listed below. I still only have totem 1.3.1, its compiled for Xine. Xine has been compiled with everything enabled. To get DVDs to work all you nee is to compile libdvdcss using --prefix=/usr and your good to go.
Cheers,
Joey[/QUOTE]


this is for 64 bit ubuntu?? you are saying that if I install the xine on your website on my 64bit machine I will have the win32 codecs issue resolved?

---

### Post by otake-tux on 2006-03-14
anyone know how to fix the battery problem?

---

### Post by Bandit on 2006-03-14
[QUOTE=otake-tux]this is for 64 bit ubuntu?? you are saying that if I install the xine on your website on my 64bit machine I will have the win32 codecs issue resolved?[/QUOTE]
The win32codecs package for MPlayer are fixed 32bit codecs from windows.
The Xine package from my site does not require the win32codecs as it has all the possible codecs built into Xine. This is becuase Xine does not require them. Just un install your current version of totem, make sure not to uninstall ubuntu desktop :) and then install the version of xine I compiled and the version of Totem I have. Incase it gives you any issues just run: ```
sudo dpkg -i --force-all *.deb
```
Dont worry about the totem-firefox plugin. My totem package already has that built in as well. But if it you upgrade to Fx 1.5.x from the original firefox it may have to be re linked.
But my Totem/Xine package plays everything possible to play on linux. All you need is lidvdcss to be able to play commerical dvd movies.
Cheers,
Joey

---

### Post by otake-tux on 2006-03-16
[QUOTE=Bandit]The win32codecs package for MPlayer are fixed 32bit codecs from windows.
The Xine package from my site does not require the win32codecs as it has all the possible codecs built into Xine. This is becuase Xine does not require them. Just un install your current version of totem, make sure not to uninstall ubuntu desktop :) and then install the version of xine I compiled and the version of Totem I have. Incase it gives you any issues just run: ```
sudo dpkg -i --force-all *.deb
```
Dont worry about the totem-firefox plugin. My totem package already has that built in as well. But if it you upgrade to Fx 1.5.x from the original firefox it may have to be re linked.
But my Totem/Xine package plays everything possible to play on linux. All you need is lidvdcss to be able to play commerical dvd movies.
Cheers,
Joey[/QUOTE]


I installed the packages just like you said, yet when I play a certain file I get he following error message from totem:

```
Video codec 'Windows Media Video 9' is not handled. You might need to install additional plugins to be able to play some types of movies
```

:-k

---

