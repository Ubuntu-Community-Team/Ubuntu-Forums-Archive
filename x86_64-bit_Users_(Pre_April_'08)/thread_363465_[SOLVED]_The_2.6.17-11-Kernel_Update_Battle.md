---
title: "[SOLVED] The 2.6.17-11-Kernel Update Battle"
date: 2007-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cariboo1938 on 2007-02-17
Hi all,
I have to be very self disciplined not to get beaten by FRUSTRATION! Since about one week I fight in the "Kernel Update Battle"! After downloading the newest updates, i.e. including kernel 2.6.17-11, the Xserver will not get started. I attached some screen shots, which hopefully show my struggles. 
Figure 1): From the Grub menu I choose kernel 2.6.17-11.
Figure 2): This I get half way through the boot procedure. 
Figure 3): Showing details  
Figure 4): Following the recommendations which I found in the forums, I use [albertomilones]("http://albertomilone.com/nvidia_scripts1.html") "envy" to reinstall the nVidia driver.
Figure 5): Selection 5 of the 'envy' menu doesn't help so, desperate as I am, I try ```
Faulty
sudo dpkg-reconfigure phigh xserver-org
``` Without success!
What do I do wrong? Where is the mistake in my actions? Is there some body who can help? The [POLL]("http://www.ubuntuforums.org/showthread.php?p=2166041#post2166041") says there are 34% of users who solved the problem!!! Maybe one could give some detailed instructions for the remaining ca. 37% who didn't?

PS. ref. to Figure 5): line "kdm not running" is OK.
I have KDE desktop installed but Gnome is the default!

[COLOR="Blue"]Hello, blame on me! I'm the culprit for my frustration myself!
```
[COLOR="Red"]Correct[/COLOR]
sudo dpkg-reconfigure **[COLOR="Red"]-[/COLOR]**phigh xserver-[COLOR="Red"]**x**[/COLOR]org
```
Everthing works just fine. Case closed![/COLOR]

---

### Post by Snookered on 2007-02-17
*I removed nvidia drivers first using synaptic!

Reload the drivers following the guide on Nvidia website (nvidia.com). Read the read-me for your driver.
Log out, press ctr+alt+F1, run "sudo /etc/init.d/gdm stop" to completely stop X.
Make sure you know where you dowmloaded the driver package to. In my case I created a folder
in /home/snookered called /stuff, so "cd /home/snookered/stuff" then ran the command as
listed on Nvidia website. It will fix the kernel problem.
I did all this after installing Beryl. BUT --- Everything works EXCEPT no title bars on the windows!

Got all this researching the forums. Thanks to all who taught me!

---

### Post by spockrock on 2007-02-17
after you run envy have you installed the nvidia driver??  which is option 1 before trying option 5?
and I believe the second command is
```
sudo dpkg-reconfigure xserver-xorg
```

@snookered, I sometimes loose the title bars, I am not sure why, but I have always found this to work, install heliodor which makes the title bars look like your metacity theme.  Btw this works for me if beryl loads you can check by putting your mouse over the window hold alt and move (if it jiggles) beryl loaded alternatively you can play with opacity,sat, and brightness to see as well.
```
sudo apt-get install heliodor 
```

then from beryl manager, pick heliodor as your window decorator, and it should load and you window titles look like they do in metacity, from there, then pick emerald again as your window decorator and the emerald window titles should come back....

---

### Post by Cariboo1938 on 2007-02-17
> **spockrock said:**
> after you run envy have you installed the nvidia driver??  which is option 1 before trying option 5? Yes i did!
> **spockrock said:**
> and I believe the second command is
sudo dpkg-reconfigure xserver-xorg Oh this is different....I'll try and let you know...Thanks for now!

---

### Post by spockrock on 2007-02-17
> **Cariboo1938 said:**
> Yes i did!
 Oh this is different....I'll try and let you know...Thanks for now!

also if you could post the error logs, the screen capture does not help all that much.

---

### Post by Cariboo1938 on 2007-02-17
Hello all,
I would like to apologize to all of you who tried to help and a want to thank 'spockrock' for pointing to my wrong command line. In my diary notes I had [COLOR="Red"]two[/COLOR] mistakes. 
The correct command is: ```
sudo dpkg-reconfigure **[COLOR="Red"]-[/COLOR]**phigh xserver-[COLOR="Red"]**x**[/COLOR]org
``` So, after using ["envy"]("http://albertomilone.com/nvidia_scripts1.html") to re-install the nVidia driver 1.0-9746 and re-configuring XServer I can use kernel 2..6.17-11-generic. Thanks again for your support, help, patience and understanding!
Cariboo:)
**[COLOR="DeepSkyBlue"]Special thanks to 'Alberto' for his great tool![/COLOR]**

---

### Post by Cariboo1938 on 2007-02-17
> **Snookered said:**
> *I removed nvidia drivers first using synaptic!
Reload the drivers following the guide on Nvidia website (nvidia.com). Read the read-me for your driver...............Got all this researching the forums. Thanks to all who taught me!Thanks for your help, Snookered. I used ["envy"]("http://albertomilone.com/nvidia_scripts1.html") instead to remove and re-install nVidia drivers and I only can recommend to look into it. It worked great for me! Thanks again.
Cariboo

---

### Post by Snookered on 2007-02-17
Spockrock,
On the Beryl site it said that there may not be enough video memory. To fix that open Beryl Manager>Advanced Beryl options>Rendering Path> and select "Copy" option.
This brought back my title bars. The onboard graphics says it has 256MB memory, but that might be shared.

---

### Post by spockrock on 2007-02-17
ahhh, I see, yeah it happens on random to my, yeah my card has 256MB as well, running at 3200x1200 can eat through the memory, more so when your run blurfx, and I get the black windows...but thanks for the tip!

---

