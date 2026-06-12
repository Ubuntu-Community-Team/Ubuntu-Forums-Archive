---
title: "Changing a 32-bit install to a 64-bit install"
date: 2005-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by gnu2tux on 2005-06-24
Hey everyone.

   Is it possible to do an apt-get dist-upgrade in the same way I upgraded from Warty to Hoary in order to upgrade from Hoary-32 to Hoary-64. 

I have had an AMD64 since Warty, but I found I had a number of stability issues with the software in 64-bit mode, so I reformatted and have been 32 bit since.

I hear from all around that there is lots of performance benefits to using 64-bit now.

So my question is twofold:

1) can I easily upgrade to 64-hoary without doing a reformat?
2) are there any problems with 64-hoary that I should be aware of. For example, I use apps like VmWare and I play some games like Doom3, RTCW / ET and so forth. Or do these 32-bit apps still stay the same 

BTW: I have an Nvidia 5200 AGP graphics card - will there be any driver issues there?

Thanks in advance,

Alistair Ross

---

### Post by ::DoGG:: on 2005-06-24
Well as far as my expereinece with nvidia goes you shouldn`t have any problems with nvidia on 64 bit ubuntu (apt-get nvidia-glx).
About going to the 64 without reformat.. 
welll... since 64 bit arch uses 64 environment, 64 libraries, 64 kernel it`s pretty sure that Yu have to install from scratch all the system (if you got any configs  from 32 you can backup them, so tjhe 64 ver of application can read it as good as in 32 bit)
About apps, well, i had some problems with audio delays (esd sound server issues) and also it`s pretty impossible to run flash plugin in 64 bit ( only in 32 chroot), also wmv codecs since they are made for 32 bits , you won`t be able to play any of the new wmv format files ( it goes i think from wmv 8.0 above, but i`m not sure..)
I don`t know about gaming in linux, but i`m able to run all the basic win application through crossoveroffice.
But i think that you can easily run them (gamnes etc..)in 32 chroot environment ( also setting up 32 chroot is very easy with howto that you can find on this forum)
Hope that helps.

---

### Post by Drain on 2005-06-24
I think if you are planning on going from a 32-bit Hoary install to a 64-bit Hoary install, you'll have to reformat and start all over for the most part. I don't know if this relates directly to Ubuntu, but reading about <a href="http://wilsonet.com/mythtv/>installing MythTv on Fedora</a> there is a note about apt having a problem when 32-bit binaries are mixed with 64-bit binaries. (hopefully this will get corrected across distrobutions a little further down the road) 

However, if your /home directory is on a seperate partition, then the majority of your settings will be saved, no problem. Just format the root partition that you installed to, and boot it up. 

Let us know how it goes.

---

### Post by Gnobody on 2005-06-27
Either back up your home directory, or you could turn your 32-bit install into a chrooted enviroment for use in the AMD64 version.  Or both if you want to be totally pain free transition to AMD64.

---

