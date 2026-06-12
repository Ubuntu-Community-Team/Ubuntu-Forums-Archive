---
title: "AMD Turion 64 x2, how to choose (And find) the right Kernel SMP"
date: 2007-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkmaster on 2007-01-10
Hi all. I just bought a new PC, it's an Asus a6000 series, a6T with an AMD Turion 64x2 processor. Since it is a double core, I would like Ubuntu to recognize both of my CPUs, I don't think it's asking too much from the distro but.... the standrad i383 install won't notice both the processors.

I've seen around the net and this forum that I need an SMP Kernel. First of all, I installed the 32-bit version of Ubuntu. It's much more compatible and I've been old that I'm not loosing so much. I also have a massive use of wine and vmware player and with the 64 bit version, maybe wine wouldn't work (Since windows apps are 32-bit..) 

In any case, don't spend any time trying to make me change the entire systm please :) I'm happy with the 32bit version but.... the processors. I need them to work.

I've been looking in the repositoryes using Synaptic for a smp kernel but if I look for -smp all I find is:

kernel-headers-2.4.27-2-686-smp
kernel-headers-2.4.27-2-k7-smp
kernel-image-2.4.27-2-686-smp
kernel-image-2.4.27-2-k7-smp

Surely the one I need is the k7 one but the kernel is very old! How's it possible? We are not at version 2.6.... but this is 2.4.... what can I do, assuming I don't whant to compile the kernel myself? I wouldn't know what to choose during the configuration and I have no time to spend on this process... please help, I'm running Ubuntu Edgy Eft, I've activated all the extra repositoryes, universe, multiverse and even installed automatix 2 and Automatix bleeder, so, I've got a lot of repos intalled.... still I can't find a recent precmpiled Kernel version for my system! 

Also, if I search for linux-image I also find version 2.16.17-10-386 wich is the one I've got installed by now. There are also the corrisponding headers but no pther smp version. Any clue? What am I doing wrong? ](*,) 

Nice day to anyone who reads this topic aniway :)

---

### Post by darkmaster on 2007-01-10
An update. If I go to packages.ubuntu.com and search for -smp I find that my repos are not guilty... infact, even on the web there're only those files I told you.... and others wich I don't think would make the job. Please, tell me wich package do I have to use or what I have to do....

---

### Post by kuja on 2007-01-10
Edit: sorry, I misread things.

If you're using the 32-bit version, it makes not a lot of sense to post in the 64-bit section of the forums. As per else, if you're using Edgy, there are only two kernels for 32-bit, and they are linux-generic and linux-386. The linux-generic is fine for most, and linux-386 is kept around for compatibility reasons. IIRC linux-generic has smp enabled, then again, I don't use 32-bit, so it's possible that my memory is off.

Extra note: all of the packages you metioned, for example, the k7 packages, are dummy packages in edgy that just install linux-generic, as they are "obsoleted"

---

### Post by darkmaster on 2007-01-10
Hi, thanks for the answer. Loooking in the repos, I reached the same conclusion and tryed to download Linux-generic just 5 minutes ago. That's because looking for the k7 smp, I found it was a dummy package obsolated by linux generic... wich is exactly what you are telling me now. BUT! I've got installed the Nvidia Ge Force GO 7600 wich doesn't work out of the box. When I tryed to install the beta proprietary drivers from the file in the nvidia ste, the installer told me he had to compile a kernerl version for my system or something oike that... or download it from the net. The installer than sayd it was impossible to find a version on the ftp site matching my kernel and that it was impossible to build one too.. so it quitted.

I managed to make my nvidia card work only by using automatix bleeder and asking it to install the beta invidia drivers. It worked!!! But now, since I rebooted after installing Linux-generic, the orrible X cannot start message displays at boot up and I'm stuck in a console... wich I don't know well how to use! I don' know what should I do to save my system without formatting and reinstalling Ubuntu. Configuring the ethernet card and downloading everything was a real pain.. I cannot do it again with a 56k modem!!!

I think that Linux-generic, wich installed linux-restricted-modules... made something bad to my Nvidia driver or installation. The Xorg outpoot is that there's no device named nvidia. I uninstalled linux generic and restricted modules but nothing changed, guess the damage is done, at this stage, useless to remove the packages.... how can I solve this? Can you help me?

---

### Post by kuja on 2007-01-10
I suggest re-asking this in the Multimedia & Video forum. You've gone and broke things good, that's all I can say. Rather than trying to undo the damage, you might be better off trying to make things work again with the drivers from nvidia's site. Try using the envy script to pull it off, I've had good luck with it.

> envy is a Python script that eases installation of the official Nvidia drivers. Please see [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) . Developers may be interested in [https://launchpad.net/products/envy](https://launchpad.net/products/envy)

Edit: I hadn't read all the way through, only glanced at things as I went regarding the reading of your post (sorry). Anyhow, if you install the nvidia drivers from nvidia's site, you have to recompile every time you change/update your kernel. And you did. So time to re-run the nvidia installer eh? Of course, envy would work too.

---

### Post by darkmaster on 2007-01-10
Nevermind, at least you're trying to give and hand! I used dpkg-reconfigure xserver-xorg and selected a vesa video display driver. At least now I'm running on X. I downloaded the script you suggested me. It is running now, downloading a 14mb file, guess it's the nvidia driver... looks like it is working... we'll see, I've got a 56k connection so I'll have a result in some. In case It'll fail, I'll post in the other forum. 

I tryed to run synaptic befor trying this script, but if I ask syn to install nvidia-glx, it tells me that nvidia-kernel-common is needed and after I choose ok, it replys that nvidia-kernel-(here's a number I don't remember, a version of the file..) is not available! Getting creazy, really. If only I made a damned backup... Linux is very sensible to modifications damn me, Next time I try and mess things up, system rescue cd is the keyword :)

For my problem with the double core, where do you suggest posting? hardware issues?

---

### Post by mips on 2007-01-10
Yes, use Alberto Milones scripts, repos & files.

See his thread here:
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)
[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

---

### Post by kuja on 2007-01-10
With regards to the nvidia driver issue, here is basically what's happening, I think. It's trying to load the latest installed version that it can find, in short, what you installed, but it's failing to load it. If you were to uninstall it (perhaps easier said than done at times), it might let you use the nvidia-glx from the repos again. As per else, you can switch back to the linux-generic kernel without a problem, so long as you re-install the nvidia driver afterwards.

---

### Post by darkmaster on 2007-01-11
Very well, I solved the issue. I reninstalled linux-generic, reconfigured X to use a vesa driver and accessed to the X window system. I tested the cpu with hwconfig (A very useful utility found on the repos, using synaptic) and found that with Linux-generic my 2 CPUs are loaded well! WOnderfull, even my mouse with built in scroll wheel simulator now works!

After that, I used the envy script as suggested by Kuja to Unistall the nvidia driver (Allways kuja's suggestion, thanks so much man...) because if I tryed to install the driver it gave me a dependency error of some kind. After unistalling I installed again, allways using envy and et voilà! I'm now fully accelerated, with 2 CPUs recognized and every good thing else working :)

Beryl's running with super speed and smoothness, kiba dock too and all I'm disappointed about is that I have to use xgl because aiglx's really slow, even if I installed the yeld hack... argh, guess with time it'll get better. FOr now, xgl wins with a lot of distance. But that's another story ;)

Thanks a lot guys!

---

