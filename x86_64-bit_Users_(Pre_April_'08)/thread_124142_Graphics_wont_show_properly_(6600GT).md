---
title: "Graphics wont show properly (6600GT)"
date: 2006-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by xb00t on 2006-01-31
I am not quite familiar with the linux architechture as I am a Windows user. I decided to give Ubuntu a try since most of the linux users I know share an opinion that it is quite something impresive. I installed the amd64 version and everything went as smooth as possible. Until I reached the login screen (I believe). After Ubuntu installed itself from the hard drive it flashed (gave a black screen) and then instead of showing me the login screen all I could see was a very funny multicolorful picture. As if someone kicked my PC case and the video card went loose out of its slot. Like a bad signal on an analogue TV but without the movement. As far as I know the linux video engine is refered to as X. I can see from some of the post in this forum that some nvidia cards are not "fully" compatible with Ubuntu 5.10. My question is - Is this the problem I am having aswell? Anyway I can fix it? I hear a little drum sound when I press Enter. Maybe I am trying to login without inputing any user details? So... any ideas?

:-k 

Specs:
MB: Asus A8V Deluxe (socket 939)
CPU: AMD Athlon 64 3200+
VGA: BFG 6600 GT OC
HDD: Seagate 200GB SATA
RAM: 512 DDR Samsung

P.S. I will try the live 64bit version now and if that doesnt work and you guys have no ideas I will give the 32bit version a go. :)

---

### Post by RAOF on 2006-01-31
[QUOTE=xb00t]I am not quite familiar with the linux architechture as I am a Windows user. I decided to give Ubuntu a try since most of the linux users I know share an opinion that it is quite something impresive. I installed the amd64 version and everything went as smooth as possible. Until I reached the login screen (I believe). After Ubuntu installed itself from the hard drive it flashed (gave a black screen) and then instead of showing me the login screen all I could see was a very funny multicolorful picture. As if someone kicked my PC case and the video card went loose out of its slot. Like a bad signal on an analogue TV but without the movement. As far as I know the linux video engine is refered to as X. I can see from some of the post in this forum that some nvidia cards are not "fully" compatible with Ubuntu 5.10. My question is - Is this the problem I am having aswell? Anyway I can fix it? I hear a little drum sound when I press Enter. Maybe I am trying to login without inputing any user details? So... any ideas?

:-k 

Specs:
MB: Asus A8V Deluxe (socket 939)
CPU: AMD Athlon 64 3200+
VGA: BFG 6600 GT OC
HDD: Seagate 200GB SATA
RAM: 512 DDR Samsung

P.S. I will try the live 64bit version now and if that doesnt work and you guys have no ideas I will give the 32bit version a go. :)[/QUOTE]
The open-source nvidia drivers sometimes do crazy things, like you've seen.  Fortunately, it's easy to get the proprietry nvidia drivers installed:  
1) Boot into recovery mode (from the boot menu, select one of the options marked "(recovery mode)".  If you don't get a boot menu, press "ESC" when you're booting and you'll get one).

2) Run the command "aptitiude install nvidia-glx"
3) Run the command "nvidia-glx-config enable"
4) Type "exit"

And it should boot into X, with the nvidia drivers loaded & working.

---

### Post by xb00t on 2006-02-01
Thanks, **RAOF**. It works perfect. As a matter of fact I am typing this from Ubuntu. ;) Case closed.

---

### Post by PandabeaR on 2006-02-01
Whoya! I have the same card, same problem. Thanks, xb00t for asking the question. Thanks ROAF for answering it. Im enjoying my "cup of ubuntu" now.

---

### Post by SlackMasterFlash on 2006-02-03
I am also experiencing a video problem after my first installlation of Ubuntu and your suggestions for the Nvidia drivers worked after I rebooted once, however after I had turned the machine off and came back to turn it on again, the problem had returned.  :confused: 

My actual video problem is that everything looks green, like my new linux system is stuck in the Matrix.  Other than the odd color scheme, evrything seems to be working fine.  And as I said, I was able to see Ubuntu in all its full color glory once, but since then have only seen the "green screen" version.

Is there something I need to do to make those configuration changes permanent?  :-k 

Thanks,

Rob

System:

MB:  Biostar K8NHA, Nvidia NF3, Socket 754
CPU: AMD 64 Sempron 2600+
VGA: Rosewill GeForce FX-5500 256MB AGP
HDD: Maxtor 300GB Ultra ATA/133 16MB Cache
RAM: 1GB DDR (2 x 512MB Corsair)

---

### Post by kakashi on 2006-02-03
thanks all. i am about to go buy the 6600 gt today so that info certainly helps.

---

### Post by stoeptegel on 2006-02-03
@SlackMasterFlash
You could try 
```
sudo dpkg-reconfigure xserver-xorg
```

Choose nv and try completing the wizzard. 
I had to do this also until it worked proper. After this reconfigure i havn't had any problems with my 6600gt for half a year already. :)

---

### Post by kuratkull on 2006-03-15
very very good....thx a lot :D

#this post is partially made as a bookmark...so when i get into trouble again
#with this i can find this post easily from my profile ;)

---

### Post by Petrouchka on 2006-03-16
[QUOTE=RAOF]The open-source nvidia drivers sometimes do crazy things, like you've seen.  Fortunately, it's easy to get the proprietry nvidia drivers installed:  
1) Boot into recovery mode (from the boot menu, select one of the options marked "(recovery mode)".  If you don't get a boot menu, press "ESC" when you're booting and you'll get one).

2) Run the command "aptitiude install nvidia-glx"
3) Run the command "nvidia-glx-config enable"
4) Type "exit"

And it should boot into X, with the nvidia drivers loaded & working.[/QUOTE]

Thanks RAOF, I've had the same problem which has prevented me from ever getting Ubuntu running, and thanks xb00t for asking the question. I've got two more questions, though:

1. The computer I'm installing to is not connected to the internet. Does aptitude need to have internet access for this, or can it install the nvidia drivers from the CD? If not, can anyone suggest a solution?

2. Is it possible to get the Ubuntu live CD running this way too?

Anyway thanks for the advice.

---

### Post by RAOF on 2006-03-16
[QUOTE=Petrouchka]...
1. The computer I'm installing to is not connected to the internet. Does aptitude need to have internet access for this, or can it install the nvidia drivers from the CD? If not, can anyone suggest a solution?

2. Is it possible to get the Ubuntu live CD running this way too?

Anyway thanks for the advice.[/QUOTE]
1) I believe that the nvidia-glx drivers are on the Ubuntu CD, so you shouldn't need an internet connection.

2) Yes, but it's a bit more involved.  I think you need to boot the live cd into "expert" mode, then answer a bunch of questions, select "vesa" as the graphics driver when asked.  Then run the "sudo aptitude install nvidia-glx ..." bit, followed by "sudo /etc/init.d/gdm restart", and it **should** work.

I haven't tested 2)

---

### Post by Petrouchka on 2006-03-17
[QUOTE=RAOF]2) Yes, but it's a bit more involved.  I think you need to boot the live cd into "expert" mode, then answer a bunch of questions, select "vesa" as the graphics driver when asked.  Then run the "sudo aptitude install nvidia-glx ..." bit, followed by "sudo /etc/init.d/gdm restart", and it **should** work.

I haven't tested 2)[/QUOTE]

I've just tried 2) out. Simply selecting "vesa" as the driver solved the main problem (of the screen being filled with garbage once X started).

But -- forgive stupid questions, but I am a complete Linux n00b -- there was no point before X started up when I could type in commands. Did I miss something? (I also had another issue, later on when using Terminal in X, in that the root password that I thought I had set wasn't being recognised when I tried using sudo, but I suppose that's a separate idiocy of my own.)

The only noticeable problem of any kind was that when I shut down, the screen filled with garbage. I guessed that typing "exit" was what was expected of me, so I did ... it seemed happy with that.

So ... good news overall! Thanks. Any afterthoughts much appreciated.

---

