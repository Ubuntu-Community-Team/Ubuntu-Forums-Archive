---
title: "Prospects for 64bit in Feisty"
date: 2007-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Raptor45 on 2007-02-23
What is Ubuntu's commitment to 64bit looking like in feisty? Are they trying to do a better job of smoothing out the bugs compared to the Edgy release? (I'm not talking about incompatable proprietary stuff here, I realize they can't do much about that.) Although I have everything all right now, 64 bit Edgy wasn't exactly "just working" right out of the box compared to the 32 bit release. Is the situation improving, or is 64 bit still not getting there yet?

---

### Post by madmetal on 2007-02-23
> **Raptor45 said:**
> What is Ubuntu's commitment to 64bit looking like in feisty? Are they trying to do a better job of smoothing out the bugs compared to the Edgy release? (I'm not talking about incompatable proprietary stuff here, I realize they can't do much about that.) Although I have everything all right now, 64 bit Edgy wasn't exactly "just working" right out of the box compared to the 32 bit release. Is the situation improving, or is 64 bit still not getting there yet?

i use ubuntu x86 since 5.04.
i knew the situtation about the 64bit version and never tried it.
but i tried feisty fawn 64bit edition at my amd 64bit and it was pretty nice..
well i am looking forward for the final release, i think its going to be a step further...

---

### Post by Kilz on 2007-02-23
> **Raptor45 said:**
> What is Ubuntu's commitment to 64bit looking like in feisty? Are they trying to do a better job of smoothing out the bugs compared to the Edgy release? (I'm not talking about incompatable proprietary stuff here, I realize they can't do much about that.) Although I have everything all right now, 64 bit Edgy wasn't exactly "just working" right out of the box compared to the 32 bit release. Is the situation improving, or is 64 bit still not getting there yet?

Exactly what do you want to "Just Work" compared to the 32bit version?

---

### Post by madmetal on 2007-02-23
> **Kilz said:**
> Exactly what do you want to "Just Work" compared to the 32bit version?

i suppose what is at your signature, but as i had a look at feisty fawn 64bit i was really glad :)

---

### Post by Raptor45 on 2007-02-23
It was a long while ago I installed, but I recall the startup splash screen being messed up, and also no detection of my NTFS drives as two examples. Both pretty easily fixable issues, but both also things which shouldn't have to be dealt with.

Plus things could be done to make the transition easier; to make work-arounds less complicated for the time being. Why not throw a 32bit version of firefox in the official repos as firefox32 for example? Why not do that for other common must-have programs which have issues under 64 bit?

Sure these problems can be gotten around, but I don't feel it should require a forum visit and searching for how-to's for normal functionality.

---

### Post by madmetal on 2007-02-23
> **Raptor45 said:**
> It was a long while ago I installed, but I recall the startup splash screen being messed up, and also no detection of my NTFS drives as two examples. Both pretty easily fixable issues, but both also things which shouldn't have to be dealt with.

start-up splash and ntfs were fine at herd 3 i used..

---

### Post by Kilz on 2007-02-23
> **Raptor45 said:**
> It was a long while ago I installed, but I recall the startup splash screen being messed up, and also no detection of my NTFS drives as two examples. Both pretty easily fixable issues, but both also things which shouldn't have to be dealt with.

Plus things could be done to make the transition easier; to make work-arounds less complicated for the time being. Why not throw a 32bit version of firefox in the official repos as firefox32 for example? Why not do that for other common must-have programs which have issues under 64 bit?

Sure these problems can be gotten around, but I don't feel it should require a forum visit and searching for how-to's for normal functionality.

I would like to know why myself. In fact I asked the Developers when Edgy was under development why we cant have a 32bit firefox available. After all it isnt like they are not making a 32bit version.  They more or less told me that they dont care because you plan to use proprietary plugins. That the 64bit version is just fine and dandy to them and I was free do the work if I wanted to. I guess editing the control file is just to difficult for them so that 64bit installable package will never be made.
Dont expect the Developers to make 64bit Feisty "Just Work" if what you want to work is proprietary. The developers want newbies to either Jump through hoops or not empower their hardware where they can by just running a 32bit OS

---

### Post by Raptor45 on 2007-02-23
Ah, I was not aware that the developers had this mindset. Makes sense though.

What frustrates me is that it is possible to get just about anything working in 64 bit, yet in most cases its far more difficult than it has to be. I understand why proprietary things cannot be included, but I don't understand why they can't be easily installable for users who want them. With that kind of mindset, Ubuntu really sounds like a dead end.

Why not have a popup to some official documentation with step by step instructions on how to install flashplayer on 64 bit the first time I try to view a flash movie? Why must it be mysterious and confusing, forcing me to search forums for howtos, some of which work while others don't?

Well I think my question was answered, and now I'm just ranting. If madmetal was correct, the big showstopper bugs have been fixed, but it seems all the minor annoyances have been purposefully left in.

---

### Post by Raptor45 on 2007-02-23
Just found this:

[https://wiki.ubuntu.com/32bitBrowserOnAmd64?highlight=%28flash%29%7C%2864%29%7C%28bit%29](https://wiki.ubuntu.com/32bitBrowserOnAmd64?highlight=%28flash%29%7C%2864%29%7C%28bit%29)
[https://launchpad.net/ubuntu/+spec/32bit-browser-on-amd64](https://launchpad.net/ubuntu/+spec/32bit-browser-on-amd64)

Seems like exactly what I was saying. Hope it doesn't get shot down, as I think the average user would benefit GREATLY from it.

---

### Post by Kilz on 2007-02-23
> **Raptor45 said:**
> Just found this:

[https://wiki.ubuntu.com/32bitBrowserOnAmd64?highlight=%28flash%29%7C%2864%29%7C%28bit%29](https://wiki.ubuntu.com/32bitBrowserOnAmd64?highlight=%28flash%29%7C%2864%29%7C%28bit%29)
[https://launchpad.net/ubuntu/+spec/32bit-browser-on-amd64](https://launchpad.net/ubuntu/+spec/32bit-browser-on-amd64)

Seems like exactly what I was saying. Hope it doesn't get shot down, as I think the average user would benefit GREATLY from it.

Take a look at the dates on those, they were spec's for Edgy. It never happened I was told because no one spelled out how to do it. Yes Im very seriously telling you that the developers said they couldnt figure out how to make a 32bit package. It is sooooo hard, thats why a user (me) who is self taught, cant code, and read to off a website how to make deb's can do it.

Take a read [https://lists.ubuntu.com/archives/ubuntu-devel/2006-October/thread.html#21424](https://lists.ubuntu.com/archives/ubuntu-devel/2006-October/thread.html#21424) The "How long will 64bit Ubuntu users have to wait? " thread.

---

### Post by pay on 2007-02-23
Try using nspluginwrapper. It runs 32bit plugins in a 64bit browser. I've used it with flash flawlessly. I still agree with you guys though. They should put in a 32bit browser. Even Gentoo does.

---

### Post by Kilz on 2007-02-23
> **pay said:**
> Try using nspluginwrapper. It runs 32bit plugins in a 64bit browser. I've used it with flash flawlessly.

How about the sites that make the browser crash?

---

### Post by pay on 2007-02-23
> **Kilz said:**
> How about the sites that make the browser crash?I haven't experienced that yet. But I guess it could happen.

---

