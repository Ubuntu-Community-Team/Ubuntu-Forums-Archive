---
title: "Broadcom wireless on HP nx6125 - another tutorial"
date: 2006-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by leche on 2006-04-23
Hello everyone,

after having spent many, many, many, manymanymany hours trying to figure out how to setup my Broadcom wireless card on my HP nx6125 laptop I am now writing this little howto.
I know there are already some tutorials out there but for me, none of them were really working and some even leave the system in a sub-optimal state.
Here now the way that worked for me and that I think is 'clean'...

1) Download the driver for your card. I tried loads of drivers and the one that finally did it for me is this one: 
[ftp://ftp.support.acer-euro.com/notebook/aspire_3010_5010/driver/xp64/80211g.zip]("ftp://ftp.support.acer-euro.com/notebook/aspire_3010_5010/driver/xp64/80211g.zip")
If this link breaks at some point, google for 'ferrari 4000 broadcom 64bit' and you should find the site. Make sure you download the 64bit driver, though.

2) Get ndiswrapper 1.14 [here]("http://ndiswrapper.sourceforge.net").
For me, only version 1.14 worked - all older versions would say everything was fine but then not load the driver.

3) Uninstall any old installation of ndiswrapper.
```

sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

```

4) Unpack and compile the new ndiswrapper and create a .deb so that you can install it with dpkg. 
```

cd <location_of_ndiswrapper.tar.gz>
sudo tar xvfz ndiswrapper-1.14.tar.gz
cd ndiswrapper-1.14

```
Note that the control files of the sources are for i386. You can compile it for amd64 as well, though.
```

cd debian
perl -p -i -e 's|i386|amd64|g' control*
cd ..
sudo make
sudo make deb
cd ..
sudo dpkg -i ndiswrapper-utils_1.8-1_amd64.deb
sudo dpkg -i ndiswrapper-modules-<your_kernel>_1.14-1_amd64

```

You now should have ndiswrapper 1.14 installed.

5) Unpack the driver downloaded previously and do the following
```

cd <path_to_driver>
sudo ndiswrapper -i bcmwl5.inf

```
It will give you some info on the config-files installed.
If you do
```

ndiswrapper -l

```
it should give you this:
```

Installed drivers:
bcmwl5          driver installed, hardware present

```

**Note:**In some tutorials you are being told to replace certain strings in your config files for the driver (RadioState etc.). Do **not** do that with ndiswrapper 1.14 or it will not work.

6) Open a new xterm (assuming you are doing this from x) and type
```

tail -f /var/log/messages

```
When you install ndiswrapper this is where you can see whether it is loaded properly or not.
So go ahead and install it:
```

sudo modprobe ndiswrapper

```
In your second xterm (the one with the "tail ...") you should now see how ndiswrapper is loaded and ** right afterwards the driver with all the configs**. If this does not happen, retry from step one or post here and I will try to help you.

7) Assuming ndiswrapper and the driver were properly loaded you should straight away be able to see the interface when you do 
```

iwconfig

```
There should be an interface in the list called wlan0. However, sometimes I had to reinit my laptop (switch runlevels or reboot) for this to show up. So if you cannot see the interface, try to reboot your system and repeat steps 6 and 7.

8) Install ndiswrapper module on startup.
```

sudo ndiswrapper -m
sudo vi /etc/modules

```
At the end of the file append a line like this
```

ndiswrapper

```

That's it - for me, wireless lan worked brilliantly after this.

To write this little howto I used ideas, hints and code from theses places:
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=64+bit+flash]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=64+bit+flash")
[http://lists.debian.org/debian-amd64/2005/08/msg00527.html]("http://lists.debian.org/debian-amd64/2005/08/msg00527.html")

and the help of some really nice people in this thread:

[http://www.ubuntuforums.org/showthread.php?p=900099#post900099]("http://www.ubuntuforums.org/showthread.php?p=900099#post900099")

I hope it helps. :)

Cheers
Che

Oh, please feel free to comment and correct. :)

---

### Post by EReckase on 2006-04-24
Does this only work with 'g'?  I have a Linksys BEFW11S4 old wireless access point that is only 802.11b, and while I get the wlan0 installed, it takes forever to configure and cannot connect to the access point.

I'm attempting to do this on a HP Pavilion dv8225nr, ML34 Turion with 1 GB RAM.

---

### Post by leche on 2006-04-24
Sorry mate, I didn't get your 'g'-point... *g*

Seriously: I haven't tried the driver with anything else than 'g' but I guess as long as you have an appropriate (i.e. Broadcom 43xx) card and 64bit the driver should be alright.
What exactly is your problem then?

Che

---

### Post by EReckase on 2006-04-24
I have a Broadcom 4318 on this machine, amd64 Breezy installed.  My wireless network is 802.11b (slower than g) - and I can't get the machine to connect.  The device appears in my System->Admin->Networking configuration as wlan0, but it won't connect to my access point for some reason.  Any ideas as to what I should try?

---

### Post by leche on 2006-04-24
Okay, so the interface is there.
When you activate it in System -> Administration -> Networking it just keeps on searching without finding anything?
Did you provide the correct ESSID?
Are you sure you provided the correct WEP key and the correct encryption?
Have you tried connecting to other networks?

Is this going in the right direction?
I mean, if you usually write your own drivers for network cards and just need me to tell you which register you should access to get the connection then ... I cannot help you! :)

What do you get when you ping the node?
Can you ping your own interface?

I just googled the stuff a little bit and on broadcom it says, the chip is a a/g band chip! So no support for b ... but I am not sure about that.
Chances are thought that if you can connect to another network, b is not supported.

Hope this helps a bit
Che

---

### Post by Maria_Firewire on 2006-04-24
Hi leche,

I am a super-newbie to Linux and this thread has been very helpful. After looking at how to's and other threads for hours I was beginning to believe it impossible for me to ever get wireless. Though this may still be the case, thanks for your clear walk-through. I still have a couple of questions if you have the time:

BTW: (I don't have the same NIC. mine is a Proxim Orinoco Gold 11/a/b/g, atheros chipset....don't know which # though...I can look on the tonight if that info will help in any way.)

1) if i install 64 bit OS (I have Athlon 64) then can i still use the ndiswrapper you posted (1.14) ?

2) if i cannot find a 64 bit win-XP driver for my card...am I out of luck, aside from becoming an uber-C programmer and writing my own (o; ?

If nothing else, this certainly has been quite the learning experience!

Thanks Again,

Maria

---

### Post by Maria_Firewire on 2006-04-24
Hi leche,

I am a super-newbie to Linux and this thread has been very helpful. After looking at how to's and other threads for hours I was beginning to believe it impossible for me to ever get wireless. Though this may still be the case, thanks for your clear walk-through. I still have a couple of questions if you have the time:

BTW: (I don't have the same NIC. mine is a Proxim Orinoco Gold 11/a/b/g, atheros chipset....don't know which # though...I can look on the tonight if that info will help in any way.)

1) if i install 64 bit OS (I have Athlon 64) then can i still use the ndiswrapper you posted (1.14) ?

2) if i cannot find a 64 bit win-XP driver for my card...am I out of luck, aside from becoming an uber-C programmer and writing my own (o; ?

If nothing else, this certainly has been quite the learning experience!

Thanks Again,

Maria

---

### Post by leche on 2006-04-25
Hi Maria,

okay, apparently there are quite a few different chipsets on those Orinoco cards, so you need be sure which one you have: for some of them linux drivers _do_ exist (and are even in the kernel source) and you definately prefer that. :)

Unless you are sure it is an atheros chipset, please do
```

uname -r
lshw
lspci

```
and post the (relevant :) output so we can check which chip you have. The model number would be very helpful, too.
Okay, done some googling too: If you really have atheros chipset with the right model, you could aparently use the orinoco drivers (modprobe orinoco). I guess you have already tried that, though...

But to answer your questions:
1) Yes, the ndiswrapper in this tutorial will be for 64bit Ubunut. That's why I put this in the 64bit Forum... ;)

2) If there really is no 64bit driver for your card then you could try madwifi. Google for it, it's an open source atheros driver. Actually, you might wanna give that a try over the Windows drivers anyway.
But let's see what your chip really is first...

Wow, very confusing post - hope it helps anyway. :)

Che

---

### Post by Maria_Firewire on 2006-04-25
hey thanks leche,

Sorry some of my questions aren't exactly REAL WINNERS...:)  hehe

Okay, so I'm typing the terminal output here so i'll just list what seems important:

product: AR5212 802.11 abg NIC
vendor: Atheros Communications, INC

So it turns out....I'm running 32 bit Ubuntu (my computers slowness is explained...no excuse for my slow brain...) but I downloaded the 64bit version and am going to install that. 

I breifly looked at that Madwifi driver....that will probably do the trick, if it works for 64 bit, that is. I don't know about the whole 'compile the source' part....but i need to learn sometime I suppose.

Thanks again. Really appreciate all your help!

Maria

---

### Post by leche on 2006-04-25
Don't mention it. Glad if I can help. :)

Okay, so madwifi is what you should be going for. Just googled for that with your chip model. 
Compiling really is not that difficult, it's all in the readme. If you need help just post it and I'll do what I can. :)

Btw: I don't think that your notebook is slow because you're using 32bit. Yes, 64bit has an advantage over 32bit but you won't be having an "AAAAAAH - this is nice and fast"-experience.
If it _really_ is slow, maybe something else is misconfigured?!


Che

---

### Post by Disabled20240622 on 2006-04-25
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAARRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRG!


That failed completely when I got to:

perl -p -i -e 's|i386|amd64|g' control*






I have never ever ever managed to install something to linux yet!!! ](*,)  It's rediculously hard. Why cant someone make a usert freindly installer!!!!

---

### Post by leche on 2006-04-25
Dude, relax! :)

Seriously, if you think it through, there is nothing wrong with linux itself. You just have to make sure you have the right things to do stuff. 
Sure, it takes a bit more time now and then if you are not too familiar with the system, but what do you get?
A virus resistent, extendable, fast and - not to forget - completely free operating system that can do anything you want! Plus - once you get past the initial "huh?"-experience after switching from windows - you actually KNOW what's going on in your system.
With MS all you can do is guess since nothing is transparent. 
If something breaks, you're stuck. 
With linux, you can change the code yourself. 
Or post in a forum to get help.

Speaking of which... :)

What do you get when you run that command? I'm guessing you maybe don't have perl installed...
Could you please post the output?

Cheers
Che

---

### Post by EReckase on 2006-05-04
One thing that really surprises me is that if I use the Trial License from those Linuxant fellows, and install their software to try to use the built-in card, it does't work - but a Linksys WPC54G V.3 with the SAME CHIPSET works just fine.

Any ideas there?

---

### Post by leche on 2006-05-05
Hey,

and you're using a NX6125?
Strange but I had the same problem: the drivers would not work with my internal card. I don't know why that is, I had to use windows drivers and wrap them.
Sorry that I cannot be more of a help - keep us posted if you figure it out, though. :)

Che

---

### Post by EReckase on 2006-05-05
No, I'm on a dx8000 series.  The external Linksys card hooks up fine to my 'b' network in  just a few seconds.

So you're saying that this process you went through worked, while the Linuxant stuff did not?

Erik

---

### Post by leche on 2006-05-05
Yeah, I tried Linuxant but they would not work. Only with the process described here I finally got it to work.
Remember to check whether your chipset actually supports 'b' wlan. It is apparently quite common to find support for a and d but not b...

Che

---

### Post by zack64 on 2006-06-12
Hi there, fairly new to this so hope you can help!

Im trying to install the ndiswrapper as per your guide, but i get 

zack@zack64:~/ndiswrapper-1.14$ make make -C driver
make[1]: Entering directory `/home/zack/ndiswrapper-1.14/driver'
Can't find kernel build files in /lib/modules/2.6.15-23-amd64-generic/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/zack/ndiswrapper-1.14/driver'
make: *** [all] Error 2

i cant seem to put it straight, can you tell me how? :p

Thanks

Zack

---

### Post by leche on 2006-06-13
Hi Zack,

It's just as the compiler claims: you don't have the kernel build files installed. 
I am in a little rush right now (just moved and we don't have inet at home yet so I am in an internet cafe paying a trillion bucks a nanosecond ;) but I'll try to post a little guide lateron. 
Otherwise you could just google for it - most of the time you get something anyway if you just google for the error message your compiler throws at you.

Che

---

