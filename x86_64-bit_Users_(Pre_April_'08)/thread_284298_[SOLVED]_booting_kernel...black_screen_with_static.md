---
title: "[SOLVED] booting kernel...black screen with static"
date: 2006-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by HappyHenry on 2006-10-25
Okay so I read through many pages and tried them, (I have tried the Fkey combos, I have tried the x86 Alt, 6.06 64bit and 32bit) but still all distros of Ubunto and Linux in general give me the same prob on this PC.

Processor = AMD Athlon 64 X2dual 4600+
RAM       = 2Gigs @ 2.41 Ghz
Monitor   = ViewSonic VA720
M board   = Winfast 6100M2MA-RS2H
Vid Card = EVGA Nvidia Geforce 7300GT
Finally got me dream machine, now if I can get it to work;) 

The problem is on Install, I boot with downloaded(and checked good) CD. All distros CDs work on old machine fine.
I get as far as
Uncompiling...OK booting kernel
Then I get black screen with horizontal static stripes. Since I have installed Ubunto on other PCs I reconize the color of the startup screen and this seems to be the right color of static for that.
Although I have installed it many times on other PCs and used it some I never got past the "window" mentality and using the GUI for everything. The above monitor works fine with Ubunto.:) 
I did try the install with out gui and at least I got as far as having an Ubunto splash screen with options for typ of install I wanted, but it still trys to load a options screen and I end up with a black screen with blue and white static stripes in center of screen.
So...any ideas how to get this monster in the box?](*,)  I would be willing to go with the 32bit version as most of what I have read I shouldnt really come up on any difference that would effect a new user like me. So any new solution I would be willing to try the correct version for it. I have read and tried previous threads so I need some new advice.
If you have the same set up and it all works maybe some bios settings would help??? Thank you for reading and any ideas you could post.:mrgreen:

---

### Post by John.Michael.Kane on 2006-10-25
HappyHenry have you tried installing ubuntu using the onboard graphics cards?

Also in the bios did you set it use your pci-e geforce card as the main vga device?

---

### Post by HappyHenry on 2006-10-26
Hi SD-Plissken
Thank you for your quick response. I tried your ideas. I changed the bios to let onboard graphics as init display and hooked up monitor to it. Still same thing, black screen and orange/brown static lines. BUT that got me to looking more carefully at the bios settings and thinking. The page for init display set also has a setting for the  "PCI Express relative items
                        Maximum Payload Size [4096]"
Now I assume that is supposed to reflect the PCIe Video Card onboard RAM. ?? The Vid card I have only has 512 onboard ram.
Do you think this may be a problem. I'm going to try setting it to 512 and see what happens.
I wanted to thank you right away for your response and let you know I tried your ideas. Thank you.

---

### Post by HappyHenry on 2006-10-26
Success,,kinda
THANK YOU SD-Plissken. You got me on the right track of thinking. I went and Put the onboard card as inti display
changed the "Maximum Payload Size of 4096 to 512 and
then on install did f4 and picked 800x600 16 color
TADA i am writting this from the live version on the beast. AWSOME SD-Plissken. Now I will go back and reread some of the other posts on xconfig. I recall reading things on getting the vid driver installed and such. I will also try and use the GForce vid card with the "maximum Payload set like it is and f4 on bootup to change resolution and color.
Things are looking promissing.

---

### Post by HappyHenry on 2006-10-26
Okay it must have something to do with the "Max Payload Setting" I stated earlier. I tried the Gforce card with Max Payload set as 512 and all the screens came up clear but...The "failed to start x server came up with I/O error device sde. So looks like bios is the place to work around this issue. I still need to look back at older posts about getting x server corrected. Maybe install on Hard drive with onboard video and then get x server straightend out for my video card. Thanks SD-Pissken. After I get it all config'd I will post all the things I did to get it smoothed out. It lives.

---

### Post by John.Michael.Kane on 2006-10-26
HappyHenry your welcome

You can look over one of these two guide for getting you nvidia drivers installed.
[http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)


Also "The failed to start x server" error means that your drivers are not configure under xorg for the card you was using. 

what you could try is using the onboard gpu to get your OS installed including the video drivers. shut down the machine install the new card set it  up right under the bios "Making sure to disable the on board gpu",and try booting with the new card. the nvidia drivers should then pick up the new card.

---

### Post by HappyHenry on 2008-06-30
I have/will not post anymore info on this as Johns links cover it all. Just reading through the links he placed here you should get the solution to any video probs. Ubuntu Forums are sooooo nice!! Thank you to all that share there knowledge!!

---

