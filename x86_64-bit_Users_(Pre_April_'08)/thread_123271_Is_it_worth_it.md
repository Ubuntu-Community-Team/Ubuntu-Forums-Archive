---
title: "Is it worth it?"
date: 2006-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by hippomofatumas on 2006-01-29
Hello all,

I have been having difficulties with Ubuntu, or just linux in general. It's all pretty new to me, but I do kinda know some stuff. The question is: is the 64 bit version worth it? Is Ubuntu worth it?

After all the research I've done I'm already attached to Ubuntu, and I've only been actually running it for about one day. I've learnt a lot, and there's a lot I like. But it's been impossible to get my ati radeon xpress 200 working with Ubuntu, no matter what I've done. That's annoying.

Also, I've been trying to get firefox 1.5 and all the plugins, like flash and java and others, and it's hard to do. Is this just a linux thing, or is it because I'm running the 64 bit version of Ubuntu? 

If I switched to the i386 or whatever version, would some of my problems go away? Would I be able to do that inside of my current Ubuntu or do I have to burn a new iso and reinstall? What do I really gain by using the 64 bit version? Is it necessary? 

I don't mind doing some research, tweaking, trying, pulling hair out, etc. It's fun for me. This is all an experiment anyway. (Yes, sorry but I have my windows intact.) But it's been a bit extensive really. I just want my monitor/video card driver to work right and to install all the necessary plugins and software. 

Thanks for your help,
hippomofatumas

hp a1230n
amd 64 3800
1 gb pc3200 ddr400 ram
200 gb sata hd
hp mx705 17" crt

---

### Post by psomas on 2006-01-29
i had also installed the 64bit version but i couldn't find some packages and i had some problems,so i installed the 32 bit...
of course you can have a 32bit environment in your 64bit ubuntu...
search the forum for 'chmod'...
however,ch,od didn't work for me and so i switced to the 32 bit version...
no problems,i have all the packages i need, and i didin't notice any difference in speed...
i don't run demanding applications and so i cant notice a speed change...

---

### Post by Randomskk on 2006-01-29
psomas means chroot; and that kinda works.
Personally I'd go with the 32bit version. I run the 64bit one and have just had trouble after trouble with it, but eventually have hammered out the biggest problems, and now that I've spent enough time tweaking it I don't really want to change.

If you've not setup anything much in it, I say go for the 32bit one. It's more supported right now.

---

### Post by pbaehr on 2006-01-30
I did exactly what you're doing. I'm new to linux, too. I installed the 64 bit version since I have a 64 bit architecture, played around, got frustrated with the lack of support and posed the same question. I got mixed results but enough people sided with my initial feelings to reinstall ubuntu as the 32 bit version until (a) I get more familiar with the OS and (b) the 64 bit version has better support.

Unfortunately, one of the reasons I changed to 32 bit was to correct the problems I was having with my ATI graphics card (the same one you have...I posted a response to your other thread regarding that) and am still unable to enable hardware acceleration. Other than that, though, a lot of other small problems I was having getting adjusted to linux were solved and I'm confident it was the right choice for me.

---

### Post by trigg on 2006-01-30
Last week I had 32-bit, but my mobo bit the dust and now with my shiny new 64-bit system, I decided to install 64-bit ubuntu.  So far, I love it.  I just compile any applications that aren't in the repositories and use "checkinstall" to create packages that can be managed with dpkg (and therefore Synaptic)!

Installing from source can be pretty daunting, but once you get the hang of it - its not too bad, and as long as you can keep track of it via synaptic, its easy to uninstall if you don't like it!

Of course, I have an Nvidia card, so I haven't had to deal with the ATI nightmare on amd64 (gave my radeon to my wife, since she runs WinXP anyway . . .).

---

### Post by slavik on 2006-01-30
I'd say 'tough it out' ... my new lappy when received back will run 64bit ubuntu ...

why?

because I can provide feedback on what works and what doesn't ... since I am a comp sci major, I might be able to actually look at the code and help the devs pin point the problems.

If less and less people use 64bit, then less and less bug finding/testing/reporting will get done ... less of that means the devs simply won't care much because there will be no need to care.

did the russians just give up after being beated on by germans during ww2? NO! It was their land and they were fighting for it! 64bit land is MY land!!!

---

### Post by RAOF on 2006-01-30
[QUOTE=slavik]I'd say 'tough it out' ... my new lappy when received back will run 64bit ubuntu ...

why?

because I can provide feedback on what works and what doesn't ... since I am a comp sci major, I might be able to actually look at the code and help the devs pin point the problems.

If less and less people use 64bit, then less and less bug finding/testing/reporting will get done ... less of that means the devs simply won't care much because there will be no need to care.

did the russians just give up after being beated on by germans during ww2? NO! It was their land and they were fighting for it! 64bit land is MY land!!![/QUOTE]
For a laptop, 64bit is particularly necessary - I don't think that powernowd works on amd64 processors in anything but the amd64 kernels, and that should dramatically increase battery life.

---

### Post by slavik on 2006-01-30
it's a sempron though :)

---

### Post by octico on 2006-01-31
Yeah. I have a compaq v5000 laptop. I installed ubuntu 5.10 no probs there. Next I just followed the a how-to located here to ATI 3d acceleration [http://mypage.iu.edu/~abatto/essays/Install-Ubuntu-5.10-Compaq-v2410.html](http://mypage.iu.edu/~abatto/essays/Install-Ubuntu-5.10-Compaq-v2410.html)

BE SURE TO FOLLOW INSTRUCTIONS IT WILL WORK. Also be sure to use his xorg.conf
. I did not use fglrxconfig!One last note: you make have to modify his xorg.conf to match your resolution.

---

### Post by slavik on 2006-02-01
[QUOTE=octico]Yeah. I have a compaq v5000 laptop. I installed ubuntu 5.10 no probs there. Next I just followed the a how-to located here to ATI 3d acceleration [http://mypage.iu.edu/~abatto/essays/Install-Ubuntu-5.10-Compaq-v2410.html](http://mypage.iu.edu/~abatto/essays/Install-Ubuntu-5.10-Compaq-v2410.html)

BE SURE TO FOLLOW INSTRUCTIONS IT WILL WORK. Also be sure to use his xorg.conf
. I did not use fglrxconfig!One last note: you make have to modify his xorg.conf to match your resolution.[/QUOTE]
I feel so poor :(

---

### Post by roderikk on 2006-02-12
[QUOTE=hippomofatumas]I have been having difficulties with Ubuntu, or just linux in general. It's all pretty new to me, but I do kinda know some stuff. The question is: is the 64 bit version worth it? Is Ubuntu worth it?[/QUOTE]

Hi!

I am also a complete newbie to linux. I posted this exact question in the newbie forum, couldn't find this before. I haven't installed Ubuntu yet but wanted to be prepared, my new computer is not here yet so I can't install yet either...

[QUOTE=trigg]Last week I had 32-bit, but my mobo bit the dust and now with my shiny new 64-bit system, I decided to install 64-bit ubuntu. So far, I love it. I just compile any applications that aren't in the repositories and use "checkinstall" to create packages that can be managed with dpkg (and therefore Synaptic)!

Installing from source can be pretty daunting, but once you get the hang of it - its not too bad, and as long as you can keep track of it via synaptic, its easy to uninstall if you don't like it![/QUOTE]

So you say that if I learn how to compile from the source I will be able to use any program I like on the 64 bit system? Does anybody know a good tutorial for newbies on how to learn these 'more advanced' stuff?

I've already downloaded and burned the 64 bit version, so I guess I'll stick to that. But any tips would be appreciated.

Thanks!

---

### Post by RAOF on 2006-02-12
The top row of links in my sig (gratefully stolen from aysiu's sig) are excellent guides to basic setup/concepts for Ubuntu, particularly the "installing stuff" one.

As you see from that page, installing from source is really the option of last resort - it's not really difficult, but it can take a bit of fiddling to get right.

---

