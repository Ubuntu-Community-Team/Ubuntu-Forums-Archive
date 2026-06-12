---
title: "Dual head display always in &quot;clone mode&quot;"
date: 2005-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Navyblue on 2005-08-02
Hi guys,

I have Ubuntu 5.04 for AMD64  installed.

I use an ATI Radeon 9550 with one analog and one DVI output. I have one monitor connected to each output.

I have installed the fglrx driver through Synaptic and selected it on the xorg.conf file. I have also installed the ATI control panel.

I can adjust the individual gamma setting for each monitors with the control panel. However, I the two screen mode always stays in "clone mode". If I were to select other mode, after rebooting (which is required for the change to take effect) the option would revert back to clone mode. The same thing happens when I log in as root.

Another problem is, although both monitors displays fine after booting and starting X, if I were to log out from WM to the login screen, the display connected to the analog output would go crazy. As in when I move the mouse cursor the whole screen moves while the mouse cursor stay put in one spot. The other screen is fine though.

I am not sure if is related, I was unable to start Enemy Territory with hardware OpenGL acceleration, it always looks for xfree86 driver.

Thanks. :)

---

### Post by DRF on 2005-08-02
You need to also edit the xorg.conf file otherwise it will continue to use the default generic graphics driver rather than the one you want it to use.

With the ATI cards try running from a terminal:
sudo cp /etc/X11/xorg.conf /etc/X11/xorgBackUp.conf
sudo fglrxconfig

Remember to make a few backups when editing the xorg.conf file incase you get a value wrong and you end up at a text prompt rather than a graphical login screen.

That should ask you a number of questions and setup your xorg.conf file for the specific ATI features. (The control panel isn't all that useful I find. More often than not I end up just changing my xorg.conf files)
I can't remember if you have to select the options again in the ATI control panel after editing the xorg.conf file or not, but I hope this helps.

Daniel

---

### Post by Navyblue on 2005-08-02
Hi Daniel,

I have ran fglrxconfig and apparently it didn't touch xorg.conf and it saves its setting in XF86Config-4. And when I rebooted nothing has changed.

What should I do next?

Thanks.

---

### Post by Sam on 2005-08-02
Are you trying to use Xinerama? I read somewhere that it was impossible to do with fglrx drivers.

---

### Post by Navyblue on 2005-08-02
[QUOTE=Sam]Are you trying to use Xinerama? I read somewhere that it was impossible to do with fglrx drivers.[/QUOTE]
 Nope, I'm not using it, in fact I tried to install it but it is not in the 64 bit repository I think.

Is Xinerama a must to have?

---

### Post by autocrosser on 2005-08-02
Look in your xorg.conf to see if "Xinerama" is a Option in "Server Layout"---If so--comment it out or set it to "false or no" Then reboot---

Edit: you also might compare what was generated in the XF86Config-4.conf to your xorg.conf--The Xserver will always default to xorg.conf first--then other .conf files after if xorg was not found--The XF86Config-4.conf might have your answer--- :)

---

### Post by Navyblue on 2005-08-03
[QUOTE=autocrosser]Look in your xorg.conf to see if "Xinerama" is a Option in "Server Layout"---If so--comment it out or set it to "false or no" Then reboot---

Edit: you also might compare what was generated in the XF86Config-4.conf to your xorg.conf--The Xserver will always default to xorg.conf first--then other .conf files after if xorg was not found--The XF86Config-4.conf might have your answer--- :)[/QUOTE]

Nothing is mentioned about Xinerama in my xorg.conf.

How do I make the system make use of the XF86Config.conf?

Thanks.

---

### Post by DRF on 2005-08-03
I seem to remember the fglrxconfig program giving you an option to output the result to a location of your choosing (instead of the default). If so you could have it output the conf file to your home dir and then backup the current xorg.conf and replace it with the one outputted by fglrxconfig manually that might help. 

(I think if you anwser 'n' to the question that asks if you want to save it to /etc/X11/xorg.conf or Xfree86 it asks you to type in your own location)

Daniel

---

### Post by Navyblue on 2005-08-03
[QUOTE=DRF]I seem to remember the fglrxconfig program giving you an option to output the result to a location of your choosing (instead of the default). If so you could have it output the conf file to your home dir and then backup the current xorg.conf and replace it with the one outputted by fglrxconfig manually that might help. 

(I think if you anwser 'n' to the question that asks if you want to save it to /etc/X11/xorg.conf or Xfree86 it asks you to type in your own location)

Daniel[/QUOTE]

Could I just rename the xfree86 to xorg?

---

