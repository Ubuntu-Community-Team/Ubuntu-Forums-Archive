---
title: "Athlon 64"
date: 2006-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by BerlinOliver on 2006-06-20
Hi guys,

I am thinking about buying a new computer (an Athlon 64 3200+). What do you think? Should a try the 64 bit install CD, or should i install the normal i386 version? I am not that crack into linux...

Thanks for your help and opinion.

---

### Post by Winblowz on 2006-06-20
You CAN get everything working in 64-bit, but it takes a bit more work and energy. If you need everything to work right away, then i386 would work best, however, if you are willing to get your hands dirty, you can get what you need working in 64-bit.

 The main things you need to workaround with to get working in 64-bit is Flash, win32codecs, WINE, and Sun Java.

---

### Post by BerlinOliver on 2006-06-20
Hi,

thanks for this quick response. Then i think I will try the 64-bit version. Also I have enogh time to work with it, because my new dsl-line will be installed at the end of july. So I burn the install DVD and try around. Many thanks and kind regards,

Oliver

---

### Post by cidica on 2006-06-20
[QUOTE=BerlinOliver]Hi,

thanks for this quick response. Then i think I will try the 64-bit version. Also I have enogh time to work with it, because my new dsl-line will be installed at the end of july. So I burn the install DVD and try around. Many thanks and kind regards,

Oliver[/QUOTE]


I just built my first computer sporting the AMD3200+. I quickly installed 64bit Ubuntu and Kubuntu. Things work in 64bit like he said but they do require some work. Such as getting flash to work. I had to use nspluginwrapper to run a 32bit flash plugin inside 64bit firefox. But for me.. I think 64bits of linux works faster than 32bits on a 64bit processor (im sure i'll get mocked for that). I would just go for the 64bit install. Takes a little work but I believe its worth it. Heck thats why I bought a 64bit processor. (I have mine overclocked too) 8)  If you are going to OC it. Be sure at watch your temps! I can get up to about 2.6 stable. Oh yeah.. Venice core. I seen where they (websites) would get it up to 2.8 and beyond but mine dont like it past 2.7. I keep it at 2.4 so I can game and such and it still be at a respectable temp.

---

### Post by kevlarman on 2006-06-21
why would you get mocked for saying 64-bit linux runs faster? amd64's have 8 (i think) extra registers for your programs to work with; 32-bit programs just leave them unused.

---

### Post by BerlinOliver on 2006-06-22
HI again,

can anybody tell me how (or what) to change the sources.list for amd64? I couldn't find a post here for the drapper amd 64 version...

---

### Post by Winblowz on 2006-06-22
I think you just change it as you would the x86 version. Replace everything in your sources.list with the following lines (copy and paste)-

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free 

```

Then, do 
```
apt-get update
```

This is what I did, but if I'm wrong then someone please speak-up.

---

### Post by steabert on 2006-06-22
[QUOTE=BerlinOliver]HI again,

can anybody tell me how (or what) to change the sources.list for amd64? I couldn't find a post here for the drapper amd 64 version...[/QUOTE]

there is no architecture for the sources.list, all the same

---

### Post by BerlinOliver on 2006-06-28
Thanks, that's great! You guys helped me a lot!

---

### Post by jvictor on 2006-06-29
Theres a tool called Automatix that 'reduces' the pain of installing all nitty-gritty stuff , I use a 64 bit version and used it to get codecs, flash etc install without any hassles

---

### Post by Poindexter on 2006-06-30
I am a new linux/ubuntu user got sick and tired of windows. Anyways I am having an issue with the system monitor that checks my processor status. I have a athlon 64 4000+ 2.4Ghz but the system monitor is showing it at 1.3Ghz. Is my processor not being fully uitilized?

---

### Post by jvictor on 2006-07-01
Its a feature wherein your processor is used only when its needed .. It reduces heat and power consumption

---

