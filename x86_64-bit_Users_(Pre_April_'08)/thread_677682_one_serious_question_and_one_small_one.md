---
title: "one serious question and one small one"
date: 2008-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by mike941 on 2008-01-25
I was trying to get ubuntu to give better support for gnash so i switched my GPU driver to the vesa driver because that's what i read in a thedownlaodsquad.com article. Right after i do that it says my computer has to reset for the changes to take effect. So i reset the computer and wait for the login screen then wait some more then wait some more then i press keys on the keyboard to see if that helps and the keys that i'm pressing start showing up on the keyboard. The login screen never shows up and now this is all that my laptop ever does.  It will show me information about what it's doing as i turn it off but aside from that and showing what keys i press it deosn't do anything else. So my question is: How do I switch to the old driver which i'm assuming was the default one in safe mode? Will i have to uninstall the partition and reinstall ubuntu? O and i don't have a restore point to fall back on to the best of my knowledge unless ubuntu installs one with when you install the live CD. O and ubuntu's only been installed on the laptop for a few days
        My small question is how do i get gnome to recognize that i'm using a laptop and show me how much battery time i have left, I put the battery display on my botum panel already it just deosn't recognize the battery.
O and i'm running 7.10

---

### Post by saru411 on 2008-01-25
im not sure what gnash is but it sounds like you messed up your video configuration. you should load the install cd and boot in safe graphics mode. then set the driver back to what it was.

---

### Post by xeth_delta on 2008-01-25
> **mike941 said:**
> I was trying to get ubuntu to give better support for gnash so i switched my GPU driver to the vesa driver because that's what i read in a thedownlaodsquad.com article. Right after i do that it says my computer has to reset for the changes to take effect. So i reset the computer and wait for the login screen then wait some more then wait some more then i press keys on the keyboard to see if that helps and the keys that i'm pressing start showing up on the keyboard. The login screen never shows up and now this is all that my laptop ever does.  It will show me information about what it's doing as i turn it off but aside from that and showing what keys i press it deosn't do anything else. So my question is: How do I switch to the old driver which i'm assuming was the default one in safe mode? Will i have to uninstall the partition and reinstall ubuntu? O and i don't have a restore point to fall back on to the best of my knowledge unless ubuntu installs one with when you install the live CD. O and ubuntu's only been installed on the laptop for a few days
        My small question is how do i get gnome to recognize that i'm using a laptop and show me how much battery time i have left, I put the battery display on my botum panel already it just deosn't recognize the battery.
O and i'm running 7.10

I really don't think you will need to reinstall. You will just need to boot in recovery mode and replace your current /etc/X11/xorg.conf with the back-up. If you did not make a back-up of the file, just change the driver to the one you had before, given you did not make any other changes to the configuration file.

If non of these work, from the terminal run:

```
sudo dpkg-reconfigure xserver-xorg
```

Remember to always make back-ups of the files you change, just in case.

Xeth

---

### Post by mike941 on 2008-01-25
Xeth_delta i typed in that sudo command and by pure luck I got what looks like my old display back. I don't really know what i typed in but i do remember not giving the card any default  shared memory. Will this be an issue? everything looks just like it used too. Its really weird. Can i use the GUI to set w/e driver i was using before? and does anyone know what is was based on after looking at the hardware in my signature? O and mostly all i did was press escape and enter alot and let the autodetect handle almost everything w/e i used asked me.

---

### Post by xeth_delta on 2008-01-25
> **mike941 said:**
> Xeth_delta i typed in that sudo command and by pure luck I got what looks like my old display back. I don't really know what i typed in but i do remember not giving the card any default  shared memory. Will this be an issue? everything looks just like it used too. Its really weird. Can i use the GUI to set w/e driver i was using before? and does anyone know what is was based on after looking at the hardware in my signature? O and mostly all i did was press escape and enter alot and let the autodetect handle almost everything w/e i used asked me.

I think that reconfiguring the package should auto-detect the card. The driver it is probably using now is the open source one. If you want to install a proprietary one, you will have to use the restricted drivers utility.

To find out your graphics card:
```
sudo lshw -C video
```
or
```
lspci | grep -i graph
```

To know if hardware acceleration is working:
```
glxinfo | grep -i direct
```

---

