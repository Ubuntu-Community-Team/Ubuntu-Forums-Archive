---
title: "screen problems"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by tikal26 on 2005-10-18
hey:
i am having the following problems with my system. its fine for a while and then i get this form the screenshot below.

(update)
I think that it is really weird becuase if i use firefox and synaptic nothing happens, but as soon as i use konqueror or adpt the thing fails, even when i use things like karbon or krita it is just kind o fwier that I get this problem with kde application cosindering i am using kubuntu. This migh also help whne I go to kinfo or sometinh like that and I try to loook for the opengl info i get an error CANNOT START OPEN GL and crash. any help would be apprecited.

---

### Post by tyga on 2005-10-20
I have this problem too.

It seems random, no obvious cause.

BTW, I had the same issue with Mandiva 2005, it cleared up after I installed the Nvidia video drivers.

I haven't bothered seeing if I can fix it so far as I have had other issues to contend with, the stupid admin mode issue, grrrrrr

---

### Post by tikal26 on 2005-10-20
tyga:
thanks for replying that did it. I installed the nvidia drivers trough adept but had to go to 
sudo dpkg-reconfigure xserver-xorg and actually pu the nvidia not the nv.
As for your problem maybe you can explain more because I don't have such a problem.

---

### Post by tyga on 2005-10-20
Excelent, I thought that would fix it. :D 

The admin mode issue is when we try to access admin mode, inputing password doesn't work, it simply closes not allowing access.

There is a work around though, kdesu kconsole.

I think this is a problem endemic to Ubuntu ( predominantly Kubuntu ) because of the disabled root account, a feature I for one, would like to see removed.

---

### Post by Greyfoxwolf on 2005-11-02
yeah i have the same problem, it only happens if i use the scroll wheel with konqueror. so which drivers do i need to install ? nvidia-glx ??

---

### Post by tyga on 2005-11-02
Yes greyfoxwolf, if you have a Nvidia graphics card then install the Nvidia drivers. Install the drivers that are available through synaptic, this saves you having to edit the config file later on.

Then type at the console:  "sudo nvidia-glx-config enable" ( minus the quotes ) Then type your password and that should be it.

You will have to restart X in order for the drivers to be enabled.

:)

By the way, I found that this problem only happened with Kubuntu not with Ubuntu.

Also, just to clear up the admin mode problem from an early post, it can be fixed easily by typing at the console, sudo passwrd, then typing a new password. Then su will be accessible rather than just sudo.

---

### Post by tikal26 on 2005-11-02
greywolf even after you install the drivers from nvidia you must reatart your x server and since I did not know what that menat her eis the command sudo dpkg-reconfigure xserver-xorg there is a section where it asks you what drivers to use use nvidia not nv

tyga thanks for your help

---

### Post by tyga on 2005-11-03
thanks tikal26,

My drivers worked fine without using the command you suggested. I'm not sure why? 

Did you install the drivers via synaptic or did you install the drivers from the Nvidia website?

I installed the synaptic drivers which were pretty much all done except for activation via the 'sudo nvidia-glx-config enable' command.

---

### Post by Greyfoxwolf on 2005-11-03
thanks dudes, it cleared up the problem.

---

### Post by tikal26 on 2005-11-04
tyage I ca't remeber, but I installed a new version of ubuntu on my laptop and found out about easy ubuntu or something like that its a scrip that installs all the extra stuff and detects the nvidia driver ans intslls them automatically so that might be the way to go now

[http://ubuntuforums.org/showthread.php?t=84742&highlight=flash](http://ubuntuforums.org/showthread.php?t=84742&highlight=flash)

---

### Post by tyga on 2005-11-04
Thanks for the tip tikal26,

I didn't even know about Automatix. Looks like a nice little app, I will give it a try

cheers.

:D

---

