---
title: "i386 or 64-Bit Install?"
date: 2008-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by fifth on 2008-03-15
I'm ready to install a new hd in my x60 and was about to download a fresh Ubuntu iso.

I've always used the i386 version as I've heard people having problems with 64bit installs due to compatibility and availability of 64bit packages. Has the situation for64bit improved? Will i run into any problems installing the 64bit version?

---

### Post by BKonkle on 2008-03-15
I used 7.10 64-bit for awhile, and things were pretty stable.  With Automatix, Flash and Java worked just fine.  VirtualBox is not included in Automatix 64, so I had to install that manually, but with a little configuration it worked just fine.  Now that I've upgraded to Hardy Alpha6, I'm having some problems with my nvidia drivers, but I don't think that is related to 64-bit architecture or not.  We'll see.

I'd say give it a shot - it's a lot better than it was a year ago.

---

### Post by Kilz on 2008-03-15
64bit is good to use, [I would not recommend Autiomatix though]("http://mjg59.livejournal.com/77440.html"). Everything you need is in the repositories and Synaptic can install it.

---

### Post by fifth on 2008-03-15
Thanks guys. Think i'll give it a try.

I've never been a fan of the automatic scripts. I prefer to install the packages myself and know whats going on. Most of what i need is in the Hardy repos anyway.

---

### Post by BKonkle on 2008-03-15
Good information!  I'm doing a fresh install of 7.10 (gave up on Hardy for now) and I'll leave Automatix off.  Thanks!

---

### Post by fifth on 2008-03-15
btw is there any noticeable performance improvement when using the 64 bit version?

---

### Post by jayson.rowe on 2008-03-15
It's subjective - somethings will be faster, some things not.

I've always run the AMD64 version on my Athlon x2, the times I tried the i386, I'm not going to say it felt "slower" but it definately didn't feel as "smooth".

---

### Post by ansicplusplus on 2008-03-15
Hy,
I also use amd64 on my quadcore and agree that everything works fine with gutsy. There had been some issues using flash on feisty, but they got solved with gutsy.
Yours, ansicplusplus

---

### Post by fifth on 2008-03-15
> **ansicplusplus said:**
> Hy,
I also use amd64 on my quadcore and agree that everything works fine with gutsy. There had been some issues using flash on feisty, but they got solved with gutsy.
Yours, ansicplusplus

Thanks for the info. The flash issue was one of the problems i came across while searching the forums. Good to know its been fixed. I've installed the i386 version for now, but have left a partition free for the 64-bit version. Going to try it out tomorrow.

---

### Post by fifth on 2008-03-15
> **jayson.rowe said:**
> It's subjective - somethings will be faster, some things not.

I've always run the AMD64 version on my Athlon x2, the times I tried the i386, I'm not going to say it felt "slower" but it definately didn't feel as "smooth".

Thanks Jayson. All the feedback seems positive, so I'm going to give it a go.

---

### Post by Jiffyman on 2008-03-15
I am also currently running a 64bit version of gusty and I have to say that I enjoy it. There are a few hiccups here and there, but almost everything has worked. The only problem I am experiencing right now is with JAVA on 64bit. Luckily I don't really need it that bad at this moment in time. I have however seen many guides and workarounds to get it working. A 32bit OS will also run slower on a 64bit machine don't ask me why, but that seems to be the case as I have experienced it. I hope this will help give you some useful insight.

---

### Post by jayson.rowe on 2008-03-16
I also wanted to add how much easier everything has become in Gutsy (and hopefully in Hardy as well).

Simply install ubuntu-restricted-extras and flashplayer-nonfree and everything just worked (automatically installs and configures nspluginwrapper).

You can also add the medibuntu repo and install w64codecs - I never do though, as everything I personally have plays, but I'm sure there must be some formats that require the win codecs, and I just don't happen to have any of those file types.

---

