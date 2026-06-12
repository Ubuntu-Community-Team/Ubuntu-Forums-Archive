---
title: "Problems booting ubuntu cd"
date: 2007-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bob0106 on 2007-03-31
I have made 4 different Ubuntu cd's in the past year and I cannot seem to get the cd to boot Ubuntu. The first time I tried I could not see anything past the first screen(right when my computer starts and is first reading the cd). Now i get as far as a screen that shows a scrolling bar but not further. I would really like to experience Ubuntu for myself. Any help would be Great. Thanks

---

### Post by Kilz on 2007-03-31
> **Bob0106 said:**
> I have made 4 different Ubuntu cd's in the past year and I cannot seem to get the cd to boot Ubuntu. The first time I tried I could not see anything past the first screen(right when my computer starts and is first reading the cd). Now i get as far as a screen that shows a scrolling bar but not further. I would really like to experience Ubuntu for myself. Any help would be Great. Thanks

Ok, lets start with the basics, 
1. did you check the md5sum of the iso files you downloaded. The md5sum is a hash of the file. It makes sure you got a good file to burn.
2. Were you able to use the check the cd for errors function in the boot up screen?

---

### Post by Bob0106 on 2007-03-31
Kind of new to this i currently use slax because I got that to work.  Not sure what to look for in the md5sum file but I am as I'm writing this looking at it and it looks fine. When i put the cd in and start to boot it it appears to be well on its way to booting then it freezes.

---

### Post by ronocdh on 2007-04-01
Well, apparently the main Download page has been redone, so I can't very quickly link you to the md5 checksums. The second point Kilz mentioned was in reference to your live CD. When booting from the live CD, ideally before installing ;), use the Check Disc for Errors option. It's essentially a post-burn checksum. If you have errors, it'll let you know, in which case don't use that disc to install!

---

### Post by dptxp on 2007-04-01
Download using Bittorrent. 
(First install Bittorrent, then download the corresponding torrent file of UBUNTU - abt 25 kB,
and open the torrent file in Bittorrent)

If your iso is corrupt you don't have to download it all again - use torrent ([http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/) e.g. [http://releases.ubuntu.com/6.10/ubun...86.iso.torrent](http://releases.ubuntu.com/6.10/ubun...86.iso.torrent) ), and when bittorrent application asks you for directory where to download -> enter directory where your iso is.
Bittorrent app will check iso image and only download corrupt pieces.


You will find what you need at 

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

How to burn iso :

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Installation Details Here:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)


Follow procedure, you will not go wrong.

---

### Post by Bob0106 on 2007-04-01
Thank you for the advice I will give it a try and see if I can figure out what is going on

---

### Post by onyx69 on 2007-07-31
Hi, I have the same problem of booting the installer of ubuntu... did the checksum, it was ok, burned 3 disc, and all failed to differents stages... can't do a cd check.  Actually I managed to boot into the environement once but couldn't install and wasn't able to boot into the environement since.  I know I'm in the thread for the 64 bit version of the OS but since I have the same problem with the 32 bit version I would like to know if any one got a fix for this ... I getting tired of burning cd's and it's doesn't seem to fix the problem anyways!

and just for the record I did burn the cd's at the lowest speed possible which is 4X

thanks in advance

---

### Post by six on 2007-07-31
It seems lots of people are having problems getting the 64-bit live CD to run, where the 32-bit one works perfectly on the same hardware. I had the same problem myself.

Most people suggest burning slower, or trying various combinations of noapic, nolapic etc. in the kernel parameters.

For me, I got it working simply by doing this:

Press up or down arrows to highlight "Start or Install Ubuntu" off the live CD when the text menu comes up.

Press F6 so you can edit the kernel parameters. Move the cursor left or right until you see the word **splash**. Delete this, then press **ENTER** to start the live CD.

Wait for the live CD to finish booting. The (K)ubuntu desktop should appear after a few minutes, then you can click on the icon to install to HD.

Be aware that when you reboot (typically after performing updates), you will need to edit the kernel parameters manually off the Grub menu. It's easily done by pressing **e** to edit the top-most option (for the most current kernel), use the cursor keys to select the kernel line, and delete the word **splash** as before. Then press **b** to boot.

To make the change permanent, edit the /boot/grub/menu.lst file and delete the **splash** parameter from there as well. That way you won't have to manually edit the Grub kernel parameters each time.

---

### Post by ahchong on 2007-07-31
em.. this stil new to me. but i think maybe ur HD have the problem or maybe not..
cause ive used windowxs before, n i have the same problem. but mine can download, but cannot format my laptop. during the blue screen it shut down immediately. i tought my HD damage, but seems when install ubuntu it turn OK??!!! but i still can  see there been HC prob, sometime lag, cannot find file, cannot save and some more...

also maybe ur internet connection. others, maybe ur CD damage>???

---

### Post by alejandro.mc on 2007-07-31
F6 or F7 (Kernel parameters) can't remember right now and add at the end of the line:

noapic

Did it for me. you should try it. Be patient with the install depending on your hardware.

Bye

---

