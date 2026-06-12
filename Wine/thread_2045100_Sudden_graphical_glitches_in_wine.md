---
title: "Sudden graphical glitches in wine"
date: 2012-08-20
forum: Wine
---

### Post by relik1989 on 2012-08-20
I have been using Ubuntu since 9.10 and have always gamed in wine without an issue. I have been running 12.04 since its release and have been playing the Sims3 and Wow in Ubuntu flawlessly. However I recently upgraded my video card from a Radeon HD 6850 to a HD7870, when I did the upgrade I reformatted and reinstalled Ubuntu 12.04 with the version of fglrx available through jockey. Now when I run games in wine they still play OK and 90% of the graphics are there, but not all. For example in the Sims3 everything renders just fine except the trees, they render as green cubes with the texture displaying as a flat image protruding from the center. There is a screen shot below. 

[IMG]http://i.stack.imgur.com/8PwXd.png[/IMG]

Wow isn't any better, flags and banners in the game just display as large textured rectangles, however Wow is so bad it wont even load completely into the game, but the errors are evident on the character select screen.

I am not sure what to do, I had both of these games running fine with the same fglrx version just a few weeks ago, and now they do not work properly. I know its not a hardware issue seeing how all these games run flawlessly in windows, If I can get 50-60 FPS in BF3 on Ultra, then I think the card is OK. 

I attempted to install the (Post release updates) version of fglrx but it fails every time (seems to be a know issue, so its not just me.) I installed "fglrx-updates" and the corresponding amdcccle package through synaptic, and it broke my system, so I had to remove them and revert back to the open source driver. Lastly I attempted to install the latest driver from the AMD website, it installed with no errors however once I restarted I was still using the open source driver and the catalyst control center was nowhere to be found even though the software center claimed that it was installed. 

I am out of ideas, any help would be very appreciated. Thank you.

---

### Post by ergo-proxy on 2012-08-22
You can either change wine version (to the one you use before or try the stable one) or try to install the latest fglrx driver.

---

### Post by thatguruguy on 2012-08-22
> **ergo-proxy said:**
> You can either change wine version (to the one you use before or try the stable one) or try to install the latest fglrx driver.

The issue isn't the Wine version he's using, it's because he changed graphics cards.

To the OP: You may consider removing the fglrx driver and installing the catalyst driver. You can find a fairly detailed explanation [here]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx").

---

### Post by relik1989 on 2012-08-22
> **thatguruguy said:**
> To the OP: You may consider removing the fglrx driver and installing the catalyst driver. You can find a fairly detailed explanation [here]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx").

I have attempted to follow the instructions on the page but I almost immediately ran into an error ```
E: Package 'fglrx-modaliases' has no installation candidate
``` when attempting to run the command ```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
```I should probably mention that I also followed the guide [here]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide") for both [SIZE=2]**"**[/SIZE][SIZE=2]Installing Catalyst Manually (from AMD/ATI's site)[/SIZE]" and "[SIZE=2]Alternative Manual Installation [/SIZE]". Both failed, when I rebooted I was brought to a login prompt on a black screen. Also each time I reformat and start fresh to avoid any other issues.

---

### Post by relik1989 on 2012-08-23
Problem solved. I tried for a second time to follow the guide [here]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide") and this time it worked. I'm now at Catalyst 12.8 and everything is running just fine.

---

### Post by thatguruguy on 2012-08-23
Glad you got it working.

---

