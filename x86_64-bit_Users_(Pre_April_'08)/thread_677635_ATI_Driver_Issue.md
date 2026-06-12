---
title: "ATI Driver Issue"
date: 2008-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by antisomnic on 2008-01-25
Ok, I actually got compiz working fine and had desktop effects using the ATI Accelerated Driver that comes with gutsy, it worked great... but a friend who has been using Ubuntu for a lot longer than me told me I'd get better performance if I downloaded the ATI driver from their website. I backed up my xorg.conf file and installed it. Now visual effects are extremely laggy. I tried restoring my previous xorg.conf file and restarting and it's still the same. Not sure how to get it to use the previous driver. I'm thinking I may have screwed it up because I didn't disable the restricted driver before installing the ATI driver... but I don't know because I'm a n00b. I also tried rebuilding the xorg.conf file with dpkg-reconfigure xserver-xorg but either it locks up or it's done after 2 steps and it didn't help. Any help is appreciated.

---

### Post by Spydr4590 on 2008-01-25
Please goto [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) Click on Ubuntu and choose your Ubuntu version. Then follow step two esactly. This will install the ati driver correctly.

The known issues you may have are these. You'll be able to get compiz working and x11 for video output while running compiz. However, you won't be able to use opengl games or other types of video output. The drivers are pretty much being devloped by one man at ATI. You can visit the unoffical ati forums where this ATI Dev Posts via this link [http://www.phoronix.com/forums/forumdisplay.php?f=19](http://www.phoronix.com/forums/forumdisplay.php?f=19)

It will probally take about two years to get ATI/AMD drivers caught up to nvidia. I would suggest switching to nvidia. I have and am much happier. Everything works and the install is so simple.

---

### Post by SebMKd on 2008-01-25
I've had my share of prb with the ATI Driver install. However, I found a solution that worked for me and wrote it down:

I've followed some of the sections from [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) mentioned above, and [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

**Before installing all this I had to go to the Restricted Driver manager (Preference>Admin) and disable the Proprietary(restricted) drivers first.**

1. Download [ati-driver-installer-8.443.1-x86.x86_64.run]("http://ati.amd.com/support/driver.html") from ATI (Select you OS and then you graphic card)
2. In the terminal type:
[FONT="Courier New"]sudo apt-get install dkms[/FONT]
3. Go to where you have downloaded the .run package and right click to look in the properties: ensure the you have the execute flag set. (It's a check box in one of the properties tabs)
4. In the terminal run:
[FONT="Courier New"]./ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/gutsy[/FONT]
5. This will generate 3 .deb files in the same folder where the .run is. Install them one by one with the following command (just modify the <version>, or just past and copy the name of each deb file):
[FONT="Courier New"]sudo dpkg -i fglrx-kernel-source_<version>.deb
sudo dpkg -i xorg-driver-fglrx_<version>.deb[/FONT]

During the Xorg-driver install (which I did at the end) I noticed that compiz and aticonfig were installed and configured.

6. Last step. In the terminal:
sudo aticonfig --initial

In order to check if this worked fine, run the following in the terminal:
[FONT="Courier New"]fglrxinfo[/FONT]
You should see something like that:
[FONT="Courier New"]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550
OpenGL version string: 2.1.7170 Release[/FONT]

If you still see the MESA driver in OpenGL, then it didn't work. 
Good luck.
_________

In the other hand, if you want to try an easier method, I would recommend Envy: 
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Disable the restricted drivers first and run Envy's script. That should set up ATIconfig and Compiz at once.

---

