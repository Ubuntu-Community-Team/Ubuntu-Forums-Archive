---
title: "Crippling Nvidia Driver Issues"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by Dan1317 on 2008-07-10
Hello, I have an issue with Ubuntu.  I don't have much experience with linux, only a month or two.  I have a Nvidia 9600GT graphics card and use the driver from nvidia's site for x64 Linux.  For about a month after installing everything went fine. 
[This is what I did to install the drivers
sudo /etc/init.d/gdm stop
Alt+F2
sudo sh driver.run
sudo /etc/init.d/gdm start]
 My machine is dual boot between Ubuntu and Vista.  For that month when everything was ok, I hadn't booted into vista.  Recently I did boot into vista (I'm there now) and then booted back into Hardy.  When ubuntu was loading, the box saying ubuntu is using VESA 800x600 came up.  I thought it was weird so I reinstalled the drivers.  During re installation the nvidia installer said there is already a driver installed but I said overwrite.  That worked for about a week.

Now, no matter what I am stuck at using 640x480 and I can't even get ubuntu to use the driver.  The installer says everything is installed but when I go to Applications/System Tools/Nvidia X Server it continues to say no driver installed despite following the instructions at the prompt.  EnvyNG didn't detect my card.  I tried following instructions in these two threads but still did not work.  

[http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia)
[http://ubuntuforums.org/showthread.php?t=819210&highlight=nvidia+drivers&page=2](http://ubuntuforums.org/showthread.php?t=819210&highlight=nvidia+drivers&page=2)

Any help would be greatly appreciated.  Hopefully I didn't leave anything out.

Also I have my xorg txt file if needed

---

### Post by mwgnz on 2008-07-11
I had a similar problem on my XFX 9600GT. Each time I ran the NVIDIA installer, it would complete successfully, however the settings manager would complain that the driver wasn't loaded. So, I ran 

```
sudo nvidia-xconfig
```

Then rebooted. It worked, but for some reason I couldn't get any resolution higher than 640x480, even when I specified it in the xorg.conf file. 

After reading through some forum posts and following everyones instructions, I decided to run:

```
sudo dpkg-configure xserver-xorg
```

Just said yes to all the prompts. I then reinstalled the NVIDIA driver using the NVIDIA install script, rebooted and it worked! I'm now able to set the res and run Compiz :)

Might be worth a shot?

---

### Post by Firedude88 on 2008-07-11
my terminal isnt saying that that is a runnable command.  sudo dpkg-configure .....

any thing im doing wrong?

---

### Post by Dan1317 on 2008-07-12
Did not work for me either but thank you a lot for the effort, here is how I got it to work.

First I shut down X server 
Then i ran these commands

```
sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules
```

and

```
sudo rm /etc/init.d/nvidia-*
```

after that I reinstalled the linux driver and so far it is working.  I lost the link to the thread I used but it's on this forum somewhere

Hope this helps you firedude

---

### Post by mwgnz on 2008-07-12
> **Firedude88 said:**
> my terminal isnt saying that that is a runnable command.  sudo dpkg-configure .....

any thing im doing wrong?

Sorry it should be:

```
sudo dpkg-reconfigure xserver-xorg
```

Dan: Good news :)

---

### Post by Artemis3 on 2008-07-12
Well here is the trick, keep the .run you downloaded from nvidia's site. Everyone using these drivers, must pay close attention to system updates offered by update-manager (the orange/reddish thing you click when there are "updates available").

Read the list of packages carefully, look out for linux, any package with that in the name means the linux kernel, meaning your nvidia drivers will stop working or get crippled at best. Either delay updating anything with "linux" in the name, or right after you update (usually offers a reboot) go to the text console, reinstall the nvidia drivers and reboot again.

In short, anytime you update any "linux" (kernel) package, you must reinstall the nvidia driver. Thats the pain of using nvidia site drivers instead of the ones in the ubuntu repositories; and is of course a direct result of being chained to [proprietary blobs](http://en.wikipedia.org/wiki/Binary_blob).

---

### Post by Dan1317 on 2008-07-12
Thank you that makes sense.  So it would be best to install from repository instead of site?

---

### Post by Firedude88 on 2008-07-13
yes thank you for the help.  i will try it and let you know how it goes.  so is it best to just use the restricted drivers in the driver manager?  or should i use the nvidia drivers?

---

### Post by Ducksgoquak on 2008-07-13
For me (7800 GTX) i seem to be having a lot better results with the newest driver from nvidia's site. The restricted driver makes me crash and requires a hard reboot when i install it:(

Although i still can't get compiz to work... grr

---

### Post by Dan1317 on 2008-07-14
I have a 9600gt and I guess drivers are only from nvidia directly because I don't have any proprietary drivers in use or available.  Driver is still working ok btw

---

### Post by Firedude88 on 2008-07-16
Ok so i thought i had fixed this problem but apparently i haven't. I went to install the new nvidia drivers about a week ago and my distro got all screwed up because i forgot to turn off the restricted drivers first. i figured that problem out. but ever since then whenever i restart ubuntu this low graphics box apears before the login screen. it says my graphics card cant be identified and that i need to manually set up my monitor or something. and when i say continue to Ubuntu (becuase i tried configuring it manually and couldnt figure it out.) it loads up ubuntu in a really really low resolution and the Nvidia manager under applications>system tools says that i dont have any nvidia drivers installed. but then i do the ctrl alt F1 and re install the Nvidia drivers and when its done i have nice resolution and can turn on all nifty features like desktop cube and such. but the second i reboot, everything goes to hell again. any suggestions?

Hardy Heron
2GB Memory
AMD Athalon 5400+ (i think, dont remember off the top off my head)
Nvidia Geforce 8600 GTS
Firedude88 is offline Report Post   	Edit/Delete Message

---

### Post by Dan1317 on 2008-07-21
Yeah I was getting that too.  This worked for me.

```
sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules
```

then, 

```
sudo rm /etc/init.d/nvidia-*
```

After that I reinstalled a fresh driver from nvidia

---

### Post by Firedude88 on 2008-07-24
what do i put for the *  that you have in the second line?

---

### Post by slick_nick on 2008-07-24
I have a 9600GT, and as far as I know, you guys are making it way too hard on yourselves, because EnvyNG works great:
[https://launchpad.net/envy](https://launchpad.net/envy)
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by xen-uno on 2008-07-25
> **Firedude88 said:**
> what do i put for the *  that you have in the second line?

Keep the asterisk ... it's a wild card character so that all files matching the base of nvidia- will be picked up (ie nvidia-8800gt).

---

### Post by Odrodzona-Sarmacja on 2008-07-26
> **slick_nick said:**
> I have a 9600GT, and as far as I know, you guys are making it way too hard on yourselves, because EnvyNG works great:
[https://launchpad.net/envy](https://launchpad.net/envy)
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

No. It is not a sweet ride with EnvyNg. Sure it works awesomely at first, but then my gdm crashed (it does crash on nv driver too from time to time) and after crash I re-logged and it worked normally at first. However after reboot I was offered only general VESA driver by gdm. Only reverting to NV driver saved me from VESA menace. Now I tried purging EnvyNg, reinstalling it and making a new driver, but after rebooting I get now always this only option of using VESA driver. Also, I don't think I was updating anything with "Linux" in name, so... I think I will go with NVidia installer now to see if it will make better choice then EnvyNg did.

PS. I have Asus EN9600GT card & I am using 32bit Xubuntu.

---

### Post by Odrodzona-Sarmacja on 2008-07-27
The howto for install nvidia driver from nvidia manually:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

IT WOKRS!!! Even GDM doesn't crash any more :D

---

