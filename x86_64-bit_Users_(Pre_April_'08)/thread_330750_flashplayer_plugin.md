---
title: "flashplayer plugin"
date: 2007-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by citreonman on 2007-01-03
Hi all
I have been using ubuntu 6.10 x64 for a few weeks now and have had a few problems which i have by one way or another managed to solve. I have used a few different linux programs in the last two years i have found this to be one of the easer to use. One problem that pops up a lot is flashplayer a lot of sites seem to want flashplayer to open items on the site. firefox is always asking for flashplayer plugin i have tryed to install it without success. is there a flashplayer plugin for x64 or is it one of those programs that as not been built yet. any help please.
    happy ubuntin
       brian

---

### Post by bruenig on 2007-01-03
There is no flash for 64 at least not natively. 
There are ways to get it though by installing 32 bit firefox and then adding them to those.
[http://ubuntuforums.org/showthread.php?t=202537]("http://ubuntuforums.org/showthread.php?t=202537")

---

### Post by pross on 2007-01-03
OR you can use nspluginwrapper to use 32bit plugins with 64bit firefox...works perfectly with flash9 beta2 just search the forums for the debs and instructions :)

---

### Post by rajeev1204 on 2007-01-04
hi

Follow this post [http://www.ubuntuforums.org/showthread.php?t=324698](http://www.ubuntuforums.org/showthread.php?t=324698)



regards

rajeev

---

### Post by Peebo on 2007-01-04
I'm using libgnashplugin, all I did was 
apt-get install libgnashplugin.

I'm assuming it's 64 bit

There is an issue though, it runs soooooo sloooowww and it slows my whole system down when I am on a website that uses flash. It's the redrawing of animations that is slow.
I don't think it's a video driver issue as everything else seems to work OK.

AMD Sempron 64 3300+ with VIA integrated graphics chip 512M RAM.

---

### Post by rajeev1204 on 2007-01-04
hi

gnash doensnt work for me either

Try the nspluginwrapper for 64 bit firefox . Its works super.

It enables flash32 bit inside 64 bit firefox

Just follow the instructions in my previous post

---

### Post by John Jason Jordan on 2007-01-04
> **Peebo said:**
> I'm using libgnashplugin, all I did was 
apt-get install libgnashplugin.
I'd like to try libgnashplugin, but it's not listed in Synaptic and apt-get install says it can't find it. No doubt I need to add a repository. But which one? Thanks!

Edit: I'm on Dapper, not Edgy.

---

### Post by kuja on 2007-01-04
Even if you could get GNASH up and working, you're not missing much really. I don't think it has even caught up to flash 7 yet, and most websites nowadays expect at the very least flash 7, if not 8 or 9, so what it can work with is rather limitted.

---

### Post by Peebo on 2007-01-04
> **John Jason Jordan said:**
> I'd like to try libgnashplugin, but it's not listed in Synaptic and apt-get install says it can't find it. No doubt I need to add a repository. But which one? Thanks!

Edit: I'm on Dapper, not Edgy.

I'm with kuja on this one. I have gnash and it is useless. I'm going to try rajeev1204s' suggestion.
It appears that is what everyone else is on 64 bit is using.
PS I'm on 6.10 which I think is Edgy.

---

### Post by Azakus on 2007-01-05
> **Peebo said:**
> I'm using libgnashplugin, all I did was 
apt-get install libgnashplugin.

I'm assuming it's 64 bit

There is an issue though, it runs soooooo sloooowww and it slows my whole system down when I am on a website that uses flash. It's the redrawing of animations that is slow.
I don't think it's a video driver issue as everything else seems to work OK.

AMD Sempron 64 3300+ with VIA integrated graphics chip 512M RAM.

Gnash is still beta software, so that it is slow is no surprise to me.

---

