---
title: "Installing Wine"
date: 2016-04-26
forum: Wine
---

### Post by feartheterrapin on 2016-04-26
I finally bit the bullet and am updating my Ubuntu 10.04 to Ubuntu-Mate 16.04.  I am doing a fresh install and will need to reinstall all my utilities including Wine.  Looking through the software repositories, I see Play on Linux, Microsoft Windows Compatibility Layer, Q4Wine, Wine Windows Program Loader, and Wine Tricks.  I don't see Wine.  Am I missing it or do I need to manually install Wine?

 ```
$ sudo add-apt-repository ppa:ubuntu-wine/ppa
$ sudo apt-get update
$ sudo apt-get install wine1.8 winetricks


``` And do I really need POL?  All I do with Wine is run a few small Windows apps and occasionally Microsoft Word.

---

### Post by kc1di on 2016-04-26
Hi,
Wine 1.6 is in the repositories.  if you need 1.8 you'll have to install it from a [ppa ]("https://launchpad.net/~wine/+archive/ubuntu/wine-builds")or use Play on Linux which if prefer because I can change my wine version depending upon which version of wine I need.  It's more flexible for me. 

I would also suggest that you install synaptic package manager it's better for showing all the packages available.
you can install it from the terminal with this command:
```
sudo apt-get install synaptic
``` 
Good Luck

---

### Post by feartheterrapin on 2016-04-26
> **kc1di said:**
> Hi,
Wine 1.6 is in the repositories.  if you need 1.8 you'll have to install it from a [ppa ]("https://launchpad.net/~wine/+archive/ubuntu/wine-builds")or use Play on Linux which if prefer because I can change my wine version depending upon which version of wine I need.  It's more flexible for me. 

I would also suggest that you install synaptic package manager it's better for showing all the packages available.
you can install it from the terminal with this command:
```
sudo apt-get install synaptic
``` 
Good Luck

No specific desire for 1.8  Wine 1.6 is just fine.  I do have synaptic package manager and I see Wine 1.6, however, I am not too familiar using it.  Looking closer at the description of the "Wine Windows Program Loader" in the "Ubuntu Software Center", it seems this may very well be Wine 1.6.

So if I install POL, will Wine be installed, or is there a specific installation order?  Also, with POL installed, can I still use Wine without using POL?

---

### Post by $yl9pAR%t on 2016-04-26
What I have seen in Software was confusing (I agree) so all what I did to install wine on Ubuntu MATE 16.04 32-bit was:

```
sudo apt install wine
```

I use wine to play old Championship Manager 01/02 and it works,

---

### Post by kc1di on 2016-04-26
I believe you should install wine then POL.  if you use POL you can download other versions of wine , but if you have 1.6 installed you can also use that.
and yes you can use wine without pol even if it's installed.

---

### Post by feartheterrapin on 2016-04-26
> **kc1di said:**
> I believe you should install wine then POL.  if you use POL you can download other versions of wine , but if you have 1.6 installed you can also use that.
and yes you can use wine without pol even if it's installed.

Thanks Dave.  Can you confirm if the "Wine Windows Program Loader" in the "Ubuntu Software Center" is Wine 1.6.

---

### Post by kc1di on 2016-04-26
Just go to a terminal and type
```
sudo apt-get install wine
```
it will pull wine 1.6 and all need dependencies -- believe it also pulls wine program loader. I don't have the software center installed here so can't tell what' in it.
Good Luck.

---

### Post by brian62 on 2016-05-16
> **feartheterrapin said:**
> And do I really need POL?  All I do with Wine is run a few small Windows apps and occasionally Microsoft Word.

You shouldn't have to install PlayOnLinux. Open a terminal and do:

```

sudo apt-get update && sudo apt-get upgrade && sudo apt-get install wine

```

If you can't find Wine in the repos, POL will probably fail to install anyway.

---

### Post by feartheterrapin on 2016-05-25
> **kc1di said:**
> Just go to a terminal and type
```
sudo apt-get install wine
```
it will pull wine 1.6 and all need dependencies -- believe it also pulls wine program loader. I don't have the software center installed here so can't tell what' in it.
Good Luck.

Thanks.  I finally got around to installing, this was simple and provided exactly what I needed.

---

