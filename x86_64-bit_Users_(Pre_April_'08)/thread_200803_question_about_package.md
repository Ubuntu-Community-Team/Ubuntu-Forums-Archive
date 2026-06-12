---
title: "question about package"
date: 2006-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by loserboy on 2006-06-20
I have an AMD64 so i got the 64 version but when i look at synaptic it shows that i have the "linux-image-amd64-generic" package installed.
should i have "linux-image-amd64-k8"? 

go easy on me i'm new and i did try searching for an answer

thanks in advance
mike

---

### Post by Winblowz on 2006-06-20
As far as I know, the linux-image-amd64-generic is the kernel for compatability with all 64-bit processors, while the linux-image-amd64-k8 is only for select 64-bit processors. The amd64-k8 kernel is only for AMD 64-bit processors, and since you're using AMD, you could probably use either kernel. The amd64-k8 kernel might give you a little better performance, but I doubt it. I can't say for sure though, because I've never used the amd64-k8 kernel.

---

### Post by loserboy on 2006-06-20
well that pretty much answers my question cuz i mean everything is working fine now, i just wonder about the performance gain like u said
thanks

---

### Post by incubus on 2006-06-20
It's for AMD's Athlon 64, Athlon FX, and Opterons.
Read here:
[http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-25-amd64-k8]("http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-25-amd64-k8")

But as Winblowz said, I don't think there's much performance gain in switching. I'm using the one for Intel EM64T myself, but can't tell any difference.

If you feel comfortable, go ahead in give it a try (as long as it's for your processor). Worst case scenario, you just revert to the generic. 

Well, I love testing just for the sake of it.

incubus

---

### Post by loserboy on 2006-06-20
thanks 
yea ill prolly try it,  im used to screwing stuff up in win and having to fix it.... im just nervous about experimenting right off the bat   :)

---

### Post by Winblowz on 2006-06-20
I just tried it myself. I'm using an AMD X2 +3800, but notice no real difference between the linux-image-amd64-generic and linux-image-amd64-k8 kernels. Just so you know though, I had to 

```
sudo apt-get install linux-image-amd64-k8
```
then...
```
sudo apt-get install linux-amd64-k8
```
and finally...
```
sudo apt-get remove linux-amd64-generic
```

Then, you can remove the listing for Ubuntu in your /boot/grub/menu.lst which uses the old amd64-generic kernel. You will see another listing which is for the amd64-k8 kernel, which you will keep. Do this and you will have no problems:D

---

### Post by loserboy on 2006-06-20
cool ill try that, but only when i get more comfortable with typing commands   hehe

---

### Post by loserboy on 2006-06-21
hey you've been really helpful mind if i ask you a couple of questions that i posted elsewhere with no help?

i have a geforce 7800 pci-e
and i have the nvidia-glx pack, do i need to enable something from default to use 3d?

cuz i wanted to test my card to see how well it works in ubuntu and i downloaded neverball and tuxracer but when i click to run them nothing happens, also some screensavers arent working

---

### Post by incubus on 2006-06-21
If you are risk-averse, remember you don't have to remove the generic kernel.  It won't conflict or do anything, you can have it there in case some upgrade doesn't go well.  That said, I usually do just as Winblowz: I remove it. :) 

It's probably a good idea to start a new thread instead, loserboy (better for other people who have the same question).

But just so you know, run:
```

$glxinfo |grep direct

```

And if 3D rendering is working, you should get yes in "direct rendering".

incubus

PS: By the way, what's in your /etc/X11/xorg.conf file?

---

### Post by Winblowz on 2006-06-21
[QUOTE=incubus]If you are risk-averse, remember you don't have to remove the generic kernel.  It won't conflict or do anything, you can have it there in case some upgrade doesn't go well.  That said, I usually do just as Winblowz: I remove it. :)[/QUOTE]
Actually, I only did the 1st command I posted and then rebooted into the amd-k8 kernel. It showed the graphical loading screen, and once it was finished, instead of booting into the login manager it showed another graphical loading screen, which didn't do anything. I had to reboot into Recovery Mode and fix it. I think the 2 kernels were interfering with each other.

---

### Post by loserboy on 2006-06-21
I screwed up something trying to enable 3d acceleration, now i cant even get into gnome, so ill get back to ya when i fix this   :(

---

### Post by incubus on 2006-06-21
loserboy,

You can always revert back to vesa by switching the driver name in your /etc/X11/xorg. You're probably trying to use "nvidia" or "nv". 

"vesa" should get your Xserver back to work.

incubus

---

### Post by loserboy on 2006-06-21
lol  thanks,

I got all nervous and just re-installed though....im so used to xp where sometimes its just easier too....i noticed with ubuntu or even linux in general almost everything can be fixed without going that far, oh well

---

### Post by incubus on 2006-06-21
loserboy,

Don't worry, I used to do that a lot. Until you gain the confidence and experience in configuring your Linux box, it's great to know that worst case scenario you can start again!

After a while, you'll see you can configure most things without much effort.  One thing I would recommend you is to relax and enjoy your system.  Don't waste too much time trying to get Everything working perfectly. Get the essential first and take advantage of that to learn well how things are managed.

(of course, at the end of the day you will have to get your hands dirty, but it's good to learn from other people's experience/mistakes).

So, are you getting the right output from "glxinfo"?

incubus

---

### Post by loserboy on 2006-06-21
actually i havent tried it, i can just tell the divers are working...no window tracers


oh yep its says "yes"

---

### Post by incubus on 2006-06-21
Very good sign. That means you got 3D rendering, at least at some level*.

$ glxgears

...is another way of verifying that.

incubus

(*) People who are crazy about/need performance go further and try the latest proprietary drivers. I would save that hassle for later, unless you really need it.

---

