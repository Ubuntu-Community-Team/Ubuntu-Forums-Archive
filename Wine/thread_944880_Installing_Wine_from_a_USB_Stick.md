---
title: "Installing Wine from a USB Stick"
date: 2008-10-11
forum: Wine
---

### Post by ronateah on 2008-10-11
I am running emc2 on a un networked Ubuntu 8.04 machine. I am extremely please with the results. I want to load wine 1.0 and can not find or figure out any clear method of getting wine install program on to the USB. I am pretty new to this so I not to sure where to start.

---

### Post by david_kt on 2008-10-11
> **ronateah said:**
> I am running emc2 on a un networked Ubuntu 8.04 machine. I am extremely please with the results. I want to load wine 1.0 and can not find or figure out any clear method of getting wine install program on to the USB. I am pretty new to this so I not to sure where to start.

I am not sure what do you want to do:
1. Do you want to install wine on USB?
2. Do you want wine to install program on USB?
3. Do you want to install wine on you un-networked computer?

Please choose one and I will try to answer it.

DK

---

### Post by ronateah on 2008-10-11
David thanks for the reply #3 please


> **david_kt said:**
> I am not sure what do you want to do:
1. Do you want to install wine on USB?
2. Do you want wine to install program on USB?
3. Do you want to install wine on you un-networked computer?

Please choose one and I will try to answer it.

DK

---

### Post by david_kt on 2008-10-11
> **ronateah said:**
> David thanks for the reply #3 please

O, that is easy one:

1. Download wine-1.0 from below link:
[http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb)

2. Copy it to your usb, and transfer it to your un-networked pc.
3. Double click wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb on your un-networked pc to install it.
4. If it complains about dependencies, record it and download it as well and install those dependencies on /var/cache/apt/archives directory of your networked computer.

Please let mw know if you still could not install wine.

DK

---

### Post by ronateah on 2008-10-12
DK

Thanks so much, I will try and let you know how it goes


> **david_kt said:**
> O, that is easy one:

1. Download wine-1.0 from below link:
[http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb)

2. Copy it to your usb, and transfer it to your un-networked pc.
3. Double click wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb on your un-networked pc to install it.
4. If it complains about dependencies, record it and download it as well and install those dependencies on /var/cache/apt/archives directory of your networked computer.

Please let mw know if you still could not install wine.

DK

---

### Post by RealG187 on 2008-10-12
I use a [Local Repository]("http://kubuntuforums.net/forums/index.php?topic=3087550.0")

This way works for installing anything, without using the internet (and saving bandwidth, even if you do have it)

---

### Post by david_kt on 2008-10-12
> **RealG187 said:**
> I use a [Local Repository]("http://kubuntuforums.net/forums/index.php?topic=3087550.0")

This way works for installing anything, without using the internet (and saving bandwidth, even if you do have it)


If I read it correctly, that would require you to copy all debs package manually, and it would not update automatically as well if there are new packages available in the internet, so that you have to copy them again to the computer manually.

So far I am using apt-proxy, that would automatically update itself as and when there is new packages available. It then provide repository for all computers in the LAN. So, you only have to download (automatically) once for all computers. And all computers could update it automatically as well. That would much better if you have more than one computer.

[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)
[http://apt-proxy.sourceforge.net/](http://apt-proxy.sourceforge.net/)

DK

---

### Post by RealG187 on 2008-10-12
You can get all the DEBs automatically and then copy the folder.

It doesn't take that long to update, but [even so...]("http://ubuntuforums.org/showthread.php?t=944949")

---

### Post by david_kt on 2008-10-12
> **RealG187 said:**
> You can get all the DEBs automatically and then copy the folder.

It doesn't take that long to update, but [even so...]("http://ubuntuforums.org/showthread.php?t=944949")

Ah, you agree with my writing on other post and give me a medal :) thank you.

By the way, go back to apt-proxy, if you only have 2 or 3 computers, yes it is easy to just copy and paste the new debs. But If you are like me, having more than 10 computers to maintain, definitely it is boring (if not time consuming) to copy new debs to all computers.

May be you could synchronize your local repository to the one connected to internet using rsync, that would be much better than keep copying new debs. But for me,  I will stick with apt-proxy at the moment.

Apt-proxy has some flaws though, sometime it stop responding and I have to restart apt-proxy (sudo /etc/init.d/apt-proxy restart) especially when I update a few computers at the same time. It is also very slow when downloading new packages.

So, I am still open to new method of updating ubuntu system that is better than apt-proxy.

DK

---

### Post by RealG187 on 2008-10-12
I don't think Apt-proxy would be good for this guy

[quote=https://help.ubuntu.com/community/AptProxy]you can access the packages from other computers on your **network**[/quote]
> I am running emc2 on a **un networked** Ubuntu 8.04 machine.
(Sorry for trying to correct you but instead of "on a **un networked** Ubuntu 8.04 machine" I think it would be on an unnetworked Ubuntu 8.04 machine")


With that said, if a computer is networked, that could be a cool thing to have, I could startup a apt-server on my network.

---

### Post by david_kt on 2008-10-12
> **RealG187 said:**
> I don't think Apt-proxy would be good for this guy 

You are right, it is for me. I switched my "mode" from "helping others" to "learning". I still have a lot to learn. I thought I would evaluate the link you give as apt-proxy replacement. For this guy, than your link is more appropriate than apt-proxy for sure. I hope I don't confuse him.

> **RealG187 said:**
> 
(Sorry for trying to correct you but instead of "on a **un networked** Ubuntu 8.04 machine" I think it would be on an unnetworked Ubuntu 8.04 machine")

Yes, I tried to correct him from un networked to un-networked, not sure which one is the correct one, un-networked or unnetworked. May be the correct one is "without network connection" :) .

> **RealG187 said:**
> 
With that said, if a computer is networked, that could be a cool thing to have, I could startup a apt-server on my network.

Sure, I search and evaluate some softwares quite sometime before I settled down with apt-proxy. So far the best one (sorry, for me, not for ronateah's case). It is similar to having local mirror. The different is it does not hold all packages, just packages you need (better than mirror?). And we could also decide how long packages would be hold, we could decide depending on the space constraint.

DK

---

### Post by RealG187 on 2008-10-12
Do you have to do anything special on the client machines to make them use apt-proxy?

> I switched my "mode" from "helping others" to "learning".
Can I be in both modes?

---

### Post by david_kt on 2008-10-13
> **RealG187 said:**
> Do you have to do anything special on the client machines to make them use apt-proxy?

Yes, it is to change repository, but it is very simple. Open sources.list:

```
gksudo gedit /etc/apt/sources.list
```

Replace web address of the repository:

```
deb http://archive.ubuntu.com/ubuntu hardy main restricted
```

To local address with 9999 port:

```
deb http://192.168.X.X:9999/ubuntu hardy main restricted
```

192.168.X.X is the ip address of your apt-proxy server.

You could use replace function in gedit to change archive.ubuntu.com to 192.168.X.X:9999 so that you do not need to type it over and over again.

> **RealG187 said:**
> Can I be in both modes?

Sure, I always do that.

DK

---

### Post by RealG187 on 2008-10-13
In the method I gave the apt line was to the user's home folder, I am sure it could be made to goto a samba share...

---

### Post by david_kt on 2008-10-13
> **RealG187 said:**
> In the method I gave the apt line was to the user's home folder, I am sure it could be made to goto a samba share...

NFS is better I guess, as you are not sharing to any MS Windows OS, just among linux OS.

DK

---

### Post by RealG187 on 2008-10-13
I guess it could be if I share a file with a name like "\?" Windows get's confused lol.

C:\Windows\Folder

That means under the "C" drive there is a folder named windows, and in that folder a folder named "Folder" but how do we know if that doesn't mean inside the "C" drive is isn't a folder called "Windows\Folder", simple a folder with that name can not exist.

I think that's why windows can't have "\" in a file name, same for linux not having "/"

Or if I type in *.*, how do I know if I am searching for wildcard (anything) or an actual file/folder named "*.*"? Simple, file names cannot have "*" in them.

I bet if windows didn't use "\" as a seperator or "?" and "*" as wildcards, we could use them in the names.

And I guess Windows uses "/" too for FTP and HTTP paths, as a seperator.

Funny Linux uses "/" and the internet uses "/", if Bill Gates really invented the internet like he claims, then woldn't the internet use "\" as a seperator?

---

### Post by ronateah on 2008-11-22
DK - Apologies, as it has taken a while to get back.  Thanks for the advice.  I am up and running.

Ron

---

### Post by ronateah on 2008-11-22
And thank also to everyone else

---

