---
title: "Help Me Please (cedega)!!!"
date: 2007-09-11
forum: Wine
---

### Post by xoron on 2007-09-11
hello i am a pretty new user of ubuntu but i have manages to get around things by using the internet.

but i have a problem... i want to play games on my ubuntu so i got cedega

once installed and i rant the tests it said
"OpenGL direct rendering failed"
"3D acceleration failed"

i have had this problem every time..i tried nvidia drive but they dont seem to work...i think i may be doing somthing wrong.

this has on a number of occasions and has resulted in me reformatting my computer...because even glxgears stops working.

this is a fresh format...i have decided not to do anithing in terms of installing untill i get cedega to work From your help.

Please help!

if it help i have an BFG nvidia 8800 GTS
if you need any more information please ask

again this is a fresh format nothing has been done but updated...(this mean no nvidia drivers either)

Please help, i have tried soo many times and still no luck.

ask if you need more information!

---

### Post by splintercellguy on 2007-09-11
Have you installed the restricted drivers in the Restricted Driver Manager?

---

### Post by xoron on 2007-09-11
nope...fresh format in that exact meaning..no restricted drivers enables

just gimme the word and it will be enabled :)

---

### Post by cogadh on 2007-09-11
The default drivers in Ubuntu don't have full direct rendering capablility, you need to install the restricted driver to get that. Most 3D enabled games will not work without it.

---

### Post by xoron on 2007-09-11
how do i install them ?

---

### Post by cogadh on 2007-09-11
I usually use this how-to:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

---

### Post by Dark Aspect on 2007-09-11
> **xoron said:**
> how do i install them ?

Open your terminal and type:

sudo apt-get install nvidia-glx

sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by frodon on 2007-09-12
If you are using ubuntu feisty fawn then maybe just use the restricted driver manager (in System > administration > restricted drivers manager), for sure the more convenient way to install drivers when you are a beginner :
[IMG]http://www.linuxseekers.com/images/stories/testing-on-ubuntu7.10-tribe2-RESTRICTED-DRIVERS-MANAGER-ON-presarioV322AU/2a_RESTRICTED_DRIVERS_MANAGER-on-my-presarioV3222AU.png[/IMG]

Nice GUI isn't it :)

---

### Post by xoron on 2007-09-12
i have tried all 3 suggestions abouve...nothing works

in fact they all end up damaging the xsever so i had to restore it

would i have to install another dirver?

anithing directly related to OpenGL rather than the hardware?...or os it the hardware that runs the OpenGL?

all suggestion welcome no matter how far-fetched

i have tried from what i think is about everithing...no luck!

please help!

---

### Post by frodon on 2007-09-12
without error log or explaination about how it failed it will be rather difficult to help you sorry.

EDIT: wait a minute i beleive 8800GTS card are a special case leave me 5 min to check.

EDIT2: ok this is indeed a known issue with ubuntu feisty, there is a bug in the driver in Ubuntu's repositories which affects geforce 8xxx cards.

So to install your nvidia drivers sucessfully you have no other choice than following one of these 2 methods :

1) install the driver from Nvidia's website by following method 2 of the tseliot's guide:
[http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126)

2) try Envy (at your risk) and solve the problem in few clicks:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

if you are beginner envy will surely be eaier to use for you

Be warned that the drawback of using nvidia drivers outside the ubuntu repositories is that you will need to install them again each time you will upgrade your kernel. And as explained in the tseliot blog you will have to remove this driver before trying to upgrade ubuntu to the next release if you want to do so. This is not a big deal but it's better for you to know this ;)

---

### Post by xoron on 2007-09-12
sorry envy does not work..i dont imaqine that it is nessesary to try it manually...is it?

still dont work is there summit wrong with my hardware (BFG Nvidia 8800 GTS) ???

---

### Post by frodon on 2007-09-12
> **xoron said:**
> sorry envy does not workPlease explain, this don't tell us much about what didn't work with envy.

Manual install should also work if you follow tseliot's instructions.

---

### Post by xoron on 2007-09-12
well envy worked as how it should it installed stuff did all the stuff in the middle(build essential, etc with no problems) and then asked me do i wanna set op the xorg.conf file aswell so i did it and then i restarted my computer

then i got the blue screen saying that the xserver was not working so i had to restore it. no nvidia splashscreen came up.

ask if you need more information

---

### Post by xoron on 2007-09-12
i had the same problem on my old computer and i just passed it off as being ''old computer''. i dont think that it is me though cos what i am doing is all working, i just dont get the results

---

### Post by frodon on 2007-09-12
You should contact Tseliot directly giving him the envy log (don't forget to give the log), i'm sure that he will know what went wrong because he's the envy developer and adapted it espcially to solve the nvidia 8xxx issue.
Otherwise you can try to install the drivers manually if you have some time.

---

### Post by hikaricore on 2007-09-12
In situations where Envy failed.  I've always had success manually installing the driver: [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

8xxx cards can be a pain to get working in some cases.  >.<

---

### Post by xoron on 2007-10-02
hi
so the 100.14.11 driver works....but a problem has arisen

everitime i restart the computer, it gives me blue screen telling me the xserver got something wrong with it.

to fix this i have to reinstall the nvidia driver and then it works.

(this is how i an typing this message right now...chances are that i will have to do this again next time i start ubuntu)

would any of this be related to the xorg.conf file
during the driver installation i have t change the xorg file accordingly.(and it works by the fact that i am typing this message....

please ask if more information is needed.

---

