---
title: "Performance is bad"
date: 2005-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by reuben on 2005-05-02
I used to run Mandrake 10.1 32 bit on this machine (AMD 3200 64 bit, 1GB RAM). I installed Hoary 64 bit and now I'm noticing distinct performance glitches. 

E.g.: the GL screensaver hiccups periodically. Full screen video has hiccups, both audio and video freezing and jumping 1/2 a second, every couple of minutes.

How can I debug this? I looked at the running processes, and there is nothing stealing CPU (according to top). There doesn't seem anything unusual in the process list. 

I have an NVidia Gforce with 128MB RAM; the nvidia drivers are installed, and load correctly (the nvidia splash comes up before kdm).

I would like to continue using Ubuntu, as in many ways it is much better than Mandrake. But performance will ultimately be the deciding factor, and if I can't fix this I'll have to switch back. Please help! 

Thanks

---

### Post by defkewl on 2005-05-02
1.) Try using a lighter WM such as WindowMaker or xfce
2.) Turn off some services during bootup such as isdn etc

Well there's more to this when talking about tuning, this is all I came up to :)

---

### Post by nocturn on 2005-05-02
This sounds like an Nvidia problem (and believe me; there are many).

Try running with the nv driver, are things as bad?

If not, try nvidia driver again, but make sure RenderAcel and composite are off.

---

### Post by reuben on 2005-05-04
defkewl - not so useful. I ran kde on mandrake, why should I not have to on ubuntu.

nocturn - thanks for giving me a lead. i am still using the nvidia driver, BUT now i specified 128MB of memory during a dpkg-reconfigure xserver-xorg, and now everything is much better. Ubuntu seems to have xorg issues...

---

### Post by Terracotta on 2005-05-04
Not only ubuntu, it's more a xorg (64bit) thing, maybe you should try to install the NEW nvidia drivers, not the ones included on the install cd, they have solved the problems for me, [http://ubuntuguide.org/](http://ubuntuguide.org/) this site tells you what to do to install the new drivers.

---

### Post by nocturn on 2005-05-04
[QUOTE=reuben]defkewl - not so useful. I ran kde on mandrake, why should I not have to on ubuntu.

nocturn - thanks for giving me a lead. i am still using the nvidia driver, BUT now i specified 128MB of memory during a dpkg-reconfigure xserver-xorg, and now everything is much better. Ubuntu seems to have xorg issues...[/QUOTE]

It seems there are many problems with the Nvidia drivers, all upto 7xxx worked fine on my GForce2, but now it is hanging.
According to one of the Ubuntu devs, the Nvidia drivers are of rather bad quality.

---

### Post by spartus4 on 2005-05-11
[QUOTE=reuben]I used to run Mandrake 10.1 32 bit on this machine (AMD 3200 64 bit, 1GB RAM). I installed Hoary 64 bit and now I'm noticing distinct performance glitches. 

E.g.: the GL screensaver hiccups periodically. Full screen video has hiccups, both audio and video freezing and jumping 1/2 a second, every couple of minutes.

How can I debug this? I looked at the running processes, and there is nothing stealing CPU (according to top). There doesn't seem anything unusual in the process list. 

I have an NVidia Gforce with 128MB RAM; the nvidia drivers are installed, and load correctly (the nvidia splash comes up before kdm).

I would like to continue using Ubuntu, as in many ways it is much better than Mandrake. But performance will ultimately be the deciding factor, and if I can't fix this I'll have to switch back. Please help! 

Thanks[/QUOTE]

I was having bad performance until I remembered to take out "dri" in the modules section of the xorg.conf file.  Now that I have done this things seem much better.

---

### Post by Optimal Aurora on 2005-05-12
I am currently using Ubuntu, but even on Fedora and Kubuntu xorg hiccups every now and then.

I personally have to agree that it is xorg 64bit. Because even the 64bit Windows system that we made in a class of mine as well as my 64bit home system running 32bit windows has hiccups in it but they are more numerous in linux... So it may be a general flaw in the 64bit architectures.

Well that's my two cents...
Later...
Optimal Aurora

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=reuben]

I would like to continue using Ubuntu, as in many ways it is much better than Mandrake. But performance will ultimately be the deciding factor, and if I can't fix this I'll have to switch back. Please help! 

Thanks[/QUOTE]

Do you use any programs that require more than 4Gigs of RAM? If not, the 64 bit version is no better- in fact it has many quirks not in the other version. 

Ask jdong (the smartest poster on the forum), 64 bit Ubuntu is overrated. Until the apps get there, there is no use in using it.

Give the 32bit version a chance before you run back to a 32bit mandrake please.

---

### Post by Optimal Aurora on 2005-05-12
[QUOTE=poofyhairguy]Do you use any programs that require more than 4Gigs of RAM? If not, the 64 bit version is no better- in fact it has many quirks not in the other version. 

Ask jdong (the smartest poster on the forum), 64 bit Ubuntu is overrated. Until the apps get there, there is no use in using it.
[/QUOTE]

Like I said before, I am a Fedora users when it comes to servers and all, but I am using debian's ubuntu linux for farthering my expertise in using linux. (More hands on work than the super stable fedora) 

However with that said fedora is the only linux I know of that actually run 64bit programs and compared to the 32 bit version we use at my college, it is absolutely more stable and secure than the 32bit. However, Flash player doesn't work with the 64bit OS.

I have also found out if you have an amd64 athlon64 or opteron you should use the amd64 bit K8 kernel. It seems to make the amd64 a bit more faster and with less hiccups than when using it in the x86_64 generic kernel.

Later...
Optimal...

---

