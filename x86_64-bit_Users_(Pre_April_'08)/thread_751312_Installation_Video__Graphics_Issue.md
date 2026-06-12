---
title: "Installation Video / Graphics Issue"
date: 2008-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by LostBear on 2008-04-10
Hi. when i boot off the 7.10 64x disc to install i get past the inital boot menu, press the number for live install. i see the kernal progress bar go accross (the blue one in the little grey dialogue box) and then it all goes black. it appears to be booting correctly, the CD drive is still going crazy and after a couple of minutes it stops. I think it is actually booting properly (its a proper pressed disc sent to me from Ubuntu so it cant be a glitch with burning an ISO incorrectly) and im sure i even heard the ubuntu drums when it go to the desktop.

Is there a command line i can use at the boot menu to force it to use basic video and resoloution? im guessing that it is failing to automatically display properly on my  24inch widescreen dell truecolor monitor (Dell E248WFP) and my graphics card is a Stock OEM Nvidia 8800 GTX.

Any suggestions would be great :)

cheers

LB

---

### Post by ericson578 on 2008-04-10
There's a shortcut key combo that will take you to a shell, I believe it's alt-ctrl-f1. 

Hope that works :)

-Eric

---

### Post by Therion on 2008-04-10
I've had this same issue for ages with plain vanilla installs of Ubuntu and my nVidia 8800GT.  Try the following and see if this fixes things.  You&#8217;re going to have to edit a file called menu.lst a bit to make this fix permanent.  It takes longer to read than to actually perform. 

Ready?  Good.  Let's do this...

Reboot your PC.
When you see GRUB (it&#8217;s the countdown timer) hit the ESCape key.
Keep your selection on the first line of the menu and hit "E" to enter Edit mode.
Using the arrow keys, go to the second line of text and and hit "E" again to edit this line.
* Delete the words **splash** and **quiet**. (See below...)
Hit &#8220;Enter&#8221;, then "B" to continue booting.

With any luck, this will get you to the Ubuntu desktop where you can do a proper install to the hard drive.

Once you're in Ubuntu, open up the Terminal and enter:

```
gksudo gedit /boot/grub/menu.lst
```
Find and delete the words **quiet** and **splash** from the line that starts with Kernel  one more time.
Save the file, Exit&#8230; And you&#8217;re done.

* Alternatively, sometimes changing **splash** to read **nosplash** instead of deleting works.  If one doesn't work, you could try the other.

Now do all your updates and such and *THEN* installl the Restricted Driver for your video card, if needed.  I use Envy for installing my drivers, but you can also let the Restricted Driver Manager do it if you prefer.  

Let me repeat: Updates first, THEN your video driver.  NOT the other way around.  The Restricted Driver Manager is going to pop up and want to install your drivers right away.  Don't do it.  Updates first.

---

### Post by LostBear on 2008-04-10
Thanks** therion** 

I tried to to be clear but i guess ive been slightly misunderstood. im guessing i can apply this to the boot CD. I havent been able to install from the Live CD (so no GRUB bootloader yet) since i cant see anything! Ill give it shot.

---

### Post by Therion on 2008-04-10
When you boot from the LiveCD can you get to a menu?  If you can, that menu should have extra boot-options, like using F6 and so forth (sorry, it's been a while since I've had to do this and I'm not behind a linux machine at the moment).  One of the options on that menu should allow you edit out "splash" and "quiet".

If you can get to the menu that look something like this one:

[img]http://ubuntumasfacil.blogsome.com/wp-admin/images/gfxboot-big.png[/img]

Use F6.

---

### Post by LostBear on 2008-04-10
yeah i can get tot hat menu, its goes black after selecting option one.....ill ty to edit it in a mo. ill post back after i have installed.

Cheers

---

