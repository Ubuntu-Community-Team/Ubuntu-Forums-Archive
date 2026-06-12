---
title: "glibc for beryl"
date: 2006-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by StandardBlueCaboose on 2006-10-13
I'll try to keep this post short.

```
caboose@caboose-desktop:~$ beryl-manager
beryl-manager: /lib/libc.so.6: version `GLIBC_2.4' not found (required by beryl-manager)

```

I don't think I really need to say anything else. This may be a common problem but I haven't found the solution.

I'm pretty sure my glibc is version 2.3.

---

### Post by tuxcantfly on 2006-10-13
upgrade to edgy's libc6

---

### Post by StandardBlueCaboose on 2006-10-13
How?

---

### Post by tuxcantfly on 2006-10-13
sudo gedit /etc/apt/sources.list

replace every "dapper" you see with "edgy"
sudo apt-get update
sudo apt-get install libc6

---

### Post by StandardBlueCaboose on 2006-10-13
I can do that? O.o

I will do it, but I'll save a backup and change back. 

Btw, can you fill me in here?

What is Dapper/Edgy? Is edgy just a new version of the kernel? I'm still trying to learn all of this terminology. Is it still in testing?

---

### Post by PriceChild on 2006-10-13
Please DO NOT follow this advice.

Edgy is the name for the unstable development version of ubuntu (6.10)

I am guessing that you have followed an edgy guide to install beryl.

Could you please post the instructions you have followed and i'll sort you out :)

---

### Post by StandardBlueCaboose on 2006-10-13
What... if... say... what if I did?

---

### Post by PriceChild on 2006-10-13
Change it all back to dapper, ```
sudo apt-get update
```and then tell me what instructions you have followed regarding beryl.

---

### Post by StandardBlueCaboose on 2006-10-13
*sigh* oh boy, it takes a while to change around here.

I honestly have no idea what instructions I followed. I just tried a whole lot of things to get it working.

...Maybe it will just be better if I start over? Care to help me out?

---

### Post by PriceChild on 2006-10-13
Could you tell me your video card?

I have a handy link in my sig: [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by StandardBlueCaboose on 2006-10-13
Nvidia (Geforce 6200)

I just removed compiz. Xgl is installed, I don't think it starts, because when I ps aux | grep xgl it just returns the grep. I dunno.

---

### Post by StandardBlueCaboose on 2006-10-13
Btw I did try to follow a few of the guides in your sig. The repositories had problems, I think.

(double btw, I like your avatar.)

---

### Post by PriceChild on 2006-10-13
I haven't tested this.... but it "should" work. I'm advising you this as a forum member, not staff.

Please follow [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

But use```
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main main-amd64
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main main-amd64
``` Instead, when you add sources.

EDIT
10 brownie points if you can tell me what game it is from before i go to bed in 10 minutes.

---

### Post by StandardBlueCaboose on 2006-10-13
That's exactly the page I was just looking at.

---

### Post by PriceChild on 2006-10-13
Use the sources i have posted above though isntead of those in the howto.

---

### Post by StandardBlueCaboose on 2006-10-13
Halo 2!


EDIT: That was extremely unfair. I was posing a response to your "brownie points" and I pressed shift + backspace. It seems that my gui has broken. X and Xgl don't work. (I'm assuming Xgl, I ran startx, I was more concerned about the brownie points than trying to start kdm) So I kind of need a howto on how to use the howto GUI-less. Oh, and Windows takes forever to boot. I wonder if I made the ten minute deadline?

Also I don't actually know if it's Halo 2. It's bungie something, but the avatar is used in halo 2. ILoveRvB if you ever want to play or something.

Double EDIT: Looks like I missed the brownie points. They meant so much to me, too... :'( You went to bed in like eight minutes though.

---

### Post by PriceChild on 2006-10-14
He he you can have those brownie points.

Could you please describe the problem you're having more accurately? What errors?

(you can use "lynx" browser to browse from the command line)

---

### Post by killkoy on 2006-10-14
It looks like you probably installed beryl from an edgy repo, if this is the case you should remove the version of beryl that you installed ```
sudo aptitude remove beryl beryl-dev beryl-core beryl-plugins beryl-plugins-data emerald emerald-themes beryl-settings beryl-manager
```

I havn't been able to find any repos that contain beryl packages for amd64 dapper (if anyone knows of one please inform me)so I built it from source
[http://ubuntuforums.org/showpost.php?p=1609787&postcount=5](http://ubuntuforums.org/showpost.php?p=1609787&postcount=5)

---

### Post by StandardBlueCaboose on 2006-10-14
> **PriceChild said:**
> 
Could you please describe the problem you're having more accurately? What errors?


I remember seeing this somewhere else on the forum; (I think it was this forum) I use 'startx' and my nvidia logo flashes quickly, then crashes. It says something about the number 11. Error code 11, or something to that effect. If I get a chance I'll post what it says more accurately.

When I run /etc/init.d/kdm start nothing really happens, and startkde doesn't flash the logo, but X returns a different error.

---

### Post by PriceChild on 2006-10-15
Well it would be a lot more helpful to see the exact error :)

---

### Post by killkoy on 2006-10-15
can you post your xorg.conf file up
```
nano /etc/X11/xorg.conf
```

---

### Post by StandardBlueCaboose on 2006-10-15
> **killkoy said:**
> can you post your xorg.conf file up
```
nano /etc/X11/xorg.conf
```

I could, but I didn't alter it in any way since I had a working configuration. I guess I will, I don't have much time today, though.

---

### Post by StandardBlueCaboose on 2006-10-16
My xorg.conf is pretty screwed up.

Anyway, it said:

```
Fatal Error: Server caught signal 11.
```

I'm pretty sure. I tried my very best to remember it. 

Can anybody help me out. My monitor is a IBM G97 and my graphics card is an nvidia geforce 6200, if anybody has those specifications in their xorg.conf I'd be glad to hear them.

---

