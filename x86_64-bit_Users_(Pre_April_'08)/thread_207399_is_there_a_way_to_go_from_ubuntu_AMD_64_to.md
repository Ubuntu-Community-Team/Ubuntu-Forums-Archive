---
title: "is there a way to go from ubuntu AMD 64 to"
date: 2006-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Adam4491 on 2006-07-01
ubuntu 32bit without loosing data?

like downgrading?


because the software support for it is kinda crap :/ (amd 64 version, that is)

---

### Post by Kilz on 2006-07-01
[QUOTE=Adam4491]ubuntu 32bit without loosing data?

like downgrading?


because the software support for it is kinda crap :/ (amd 64 version, that is)[/QUOTE]
Nope, delete away if you want. But the software support is not crap. You just may not be looking in the right place for the info.

---

### Post by Adam4491 on 2006-07-01
Maybe it's just because I'm a linux n00b, but I can't find how to install nvu. and I really need it to edit my sites.

Well, I can do the PHP work in the text editer

but the HTML work is just alot easier in an HTML editer

I guess I'm lazy? heh :P

---

### Post by Winblowz on 2006-07-01
Isn't Nvu available for 64-bit? Have you tried 
```
sudo apt-get install nvu
```

---

### Post by Kilz on 2006-07-02
[QUOTE=Adam4491]Maybe it's just because I'm a linux n00b, but I can't find how to install nvu. and I really need it to edit my sites.

Well, I can do the PHP work in the text editer

but the HTML work is just alot easier in an HTML editer

I guess I'm lazy? heh :P[/QUOTE]
You can also use synaptic to install nvu. Its in System > Adminastration > Synaptic Package Manager. You might also want to take a look at scream for php editing.

---

### Post by Adam4491 on 2006-07-02
nope, I get an error

---

### Post by Adam4491 on 2006-07-02
[QUOTE=Kilz]You can also use synaptic to install nvu. Its in System > Adminastration > Synaptic Package Manager. You might also want to take a look at scream for php editing.[/QUOTE]
I've looked before, and I can't find it


I looked just now and I still can't find it

:/

---

### Post by lotheac on 2006-07-02
nvu is available for amd64 - sounds like you just don't have universe repositories enabled.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Adam4491 on 2006-07-02
ah, now that worked
installing now
thanks alot :D

---

### Post by robogock on 2006-07-05
Even though the original poster solved things without downgrading, I'd love to see an answer to his question.  I'm just tired of having to figure out workarounds to the various 64-bit issues, and I want to downgrade. (Heck, I mostly just use this box for email and internet, so it's not like I'm getting anything extra for having the 64bit kernel.)

I'm at a loss as to how, though. I don't see what I'm supposed to change where to install a 32bit version of ubuntu. Help?

---

### Post by Kilz on 2006-07-05
[QUOTE=robogock]Even though the original poster solved things without downgrading, I'd love to see an answer to his question.  I'm just tired of having to figure out workarounds to the various 64-bit issues, and I want to downgrade. (Heck, I mostly just use this box for email and internet, so it's not like I'm getting anything extra for having the 64bit kernel.)

I'm at a loss as to how, though. I don't see what I'm supposed to change where to install a 32bit version of ubuntu. Help?[/QUOTE]
If you mainly use the box for email and the internet, what work arounds have you had to figure out? What havent you been able to get working that you want to go through all the trouble and risk of moving to 32bit?

---

### Post by robogock on 2006-07-05
Flash and my (crappy but free) printer, for example. Yes, I know there are work arounds at least for flash, and probably for the printer, too (something about running cups as a 32bit chroot I think).  But you know what? I don't want to deal with working around things like that. I want things to Just Work.  I'm lazy, see? And if a one-time reinstall makes it so I never encounter things that need work-arounds, well, I'll take that reinstall.  All my data is on a separate drive, so I'm not too worried about a reinstall.... I just can't even figure out how to install a 32bit version.

My linux fu is weak, I admit.

---

### Post by Kilz on 2006-07-06
[QUOTE=robogock]Flash and my (crappy but free) printer, for example. Yes, I know there are work arounds at least for flash, and probably for the printer, too (something about running cups as a 32bit chroot I think).  But you know what? I don't want to deal with working around things like that. I want things to Just Work.  I'm lazy, see? And if a one-time reinstall makes it so I never encounter things that need work-arounds, well, I'll take that reinstall.  All my data is on a separate drive, so I'm not too worried about a reinstall.... I just can't even figure out how to install a 32bit version.

My linux fu is weak, I admit.[/QUOTE]
Looking at your posts, you have a Lexmark printer. No matter what version you run you are going to have problems. Lexmark is notorious for having the worst Linux support ever.
A one time reinstall will not solve all your problems. [I think you might benefit from reading this page. ]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by robogock on 2006-07-06
[QUOTE=Kilz]Looking at your posts, you have a Lexmark printer. No matter what version you run you are going to have problems. Lexmark is notorious for having the worst Linux support ever.
A one time reinstall will not solve all your problems. [I think you might benefit from reading this page. ]("http://linux.oneandoneis2.org/LNW.htm")[/QUOTE]

No OS is perfect, obviously. I use linux for programming... but my laptop is a mac. :)  And regarding my printer: well, yes, the only reason I have a lexmark is because my old printer broke and this one was free.  I'm just frustrated because supposedly other folks *have* gotten it to work with the 64bit version of ubuntu, but after several hours of trying things, I had to admit that I just Don't Get how to set it up.  But there's plenty of information on how to run it in a 32bit OS.

Let me ask you this: is there a straightforward way to run any 32bit application in the 64bit OS? Such as, if I did want to use 32bit printer drivers, would I need to run 32bit cups? If so, how?

---

### Post by Kilz on 2006-07-06
[QUOTE=robogock]No OS is perfect, obviously. I use linux for programming... but my laptop is a mac. :)  And regarding my printer: well, yes, the only reason I have a lexmark is because my old printer broke and this one was free.  I'm just frustrated because supposedly other folks *have* gotten it to work with the 64bit version of ubuntu, but after several hours of trying things, I had to admit that I just Don't Get how to set it up.  But there's plenty of information on how to run it in a 32bit OS.

Let me ask you this: is there a straightforward way to run any 32bit application in the 64bit OS? Such as, if I did want to use 32bit printer drivers, would I need to run 32bit cups? If so, how?[/QUOTE]
I will tell you I battled a lexmark printer at my brothers house for 2 days, and he has a 32bit computer. In the end he bought an Epson and it was plug it in, click, click,setup, print.
I'm not sure if its possible to run 32bit drivers on the 64bit, but since you have read success stories it may be. Getting 32bit cups running may be possible, but its a lot of packages to force in.
[During my look around I came across this post.]("http://ubuntuforums.org/showthread.php?t=83456") That describes how to set up the printer you have. I didn't notice any posts by you on it. I don't know if you have tried it, but it looks easy cut and paste. Let me say that reading the topic its a 50/50 chance of getting them to run in 32bit.
Like I said above Lexmark has the worst printer support. You may not get it to run even if you change to 32bit.

---

