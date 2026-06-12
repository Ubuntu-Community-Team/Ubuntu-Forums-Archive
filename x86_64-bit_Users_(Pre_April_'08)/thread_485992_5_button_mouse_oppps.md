---
title: "5 button mouse oppps"
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-06-27
Ok well I redid my system so that I could have all my hard drive (160 gigs). Well I went to go and add my 5 button mouse so I could use the side buttons for going forward and backwards on web pages. I guess I messed something up and now my x server won't work right. When I start my computer it goes through loading everything but when I'm suppose to get to the login screen it won't come up with a GUI interface. I know that if I could get to the document and change it back to the orginal one than I could fix it but I can't use the gedit command. Someone help me out I don't want to fully redo the system.

---

### Post by DM0407 on 2007-06-27
Do you have Nvidia video card? if you did and you used nvidia config it makes changes to the xorg.conf file.....


[B]if you want to manually edit the file......

vi /etc/X11/xorg.conf
[/B]
you can edit the file and then save by holding shift and typing ' ZZ '   or     ' :wq '  


If you did install the Nvidia driver and used the nvidia-xconfig, then you probaly just have to change the Reference name to match what your changed in the mouse field.....

[I]
For instance:

It should be 'Configured Mouse' by default.... when Nvida changes the file they change the Reference to 'Mouse0' and then you paste the mouse information  that contains 'Configured Mouse' . Make sure the two references are the same[/I]

Section "InputDevice"
    **Identifier "Mouse0"**     I know yours look different but you should see a call to Mouse0 or something similar at the top of the page. (if using nvidia generated Xorg.conf)
    Driver "mouse"
    Option "Protocol" "Auto"
    Option "Device" "/dev/ums0"
    Option "Buttons" "7"
    Option "ZAxisMapping" "4 5"
    Option "Resolution" "800"
EndSection

[B]
To revert back to old settings:[/B]

when changes to the xorg are made using the Nvidia xconfig, it will make a back up call xorg.conf.backup
vi the back up file to make sure it has the correct info....

cp /etc/X11/xorg.conf.backup  /etc/X11/xorg.conf


I just went through this the other day..... From now on I will install what ever I can with Automatix, it went so much smoother.


Glad I can finally answer a question on here rather then ask them ;)

---

### Post by DaGGer on 2007-06-28
Ok well I couldn't figure out how to do it. So I just reinstalled my system and its relaly nice. Now my flash doesn't sound like crap anymore and its running a bit better. I don't have a bunch of junk all over the place. So its nice now.

Thanks for your help.

---

