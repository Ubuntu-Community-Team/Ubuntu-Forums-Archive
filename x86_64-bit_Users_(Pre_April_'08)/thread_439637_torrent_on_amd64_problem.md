---
title: "torrent on amd64 problem"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by queency on 2007-05-10
Hi all

I installed feisty and have some torrent problem.
i use the built in torrent downloader but it can download just 1 file at a time!
how can i config it to download more !!
I have router but it does not block outside requests !

tnx

---

### Post by John Jason Jordan on 2007-05-10
> **queency said:**
> I installed feisty and have some torrent problem.
i use the built in torrent downloader but it can download just 1 file at a time!
how can i config it to download more !!
I have router but it does not block outside requests
I like Ktorrent. Others like Azureus, and BitTornado is also popular. These are all in System > Administration > Synaptic. There are also others, but I'm not sure if they're in Synaptic.

---

### Post by queency on 2007-05-11
I prefer using the installed torrent program !!
Isn't any way to configure it to recive more then 
just 1 file ??

---

### Post by John Jason Jordan on 2007-05-11
> **queency said:**
> I prefer using the installed torrent program !!
Isn't any way to configure it to receive more then just 1 file ??
No, Bittorrent is a bare-bones program with practically no advanced features. Bittorrent is to Ktorrent or Azureus as Text Editor is to OpenOffice.org Writer.

---

### Post by LuisGMarine on 2007-05-12
I'm curious, I thought the Azureus packaged in the repos was broken.  I would love to get Azureus running on 64-bit amd.  Can you be so kind as to point me to a guide that might have that?

---

### Post by John Jason Jordan on 2007-05-12
> **LuisGMarine said:**
> I'm curious, I thought the Azureus packaged in the repos was broken.  I would love to get Azureus running on 64-bit amd.  Can you be so kind as to point me to a guide that might have that?
I tried Azureus once back in the days of Edgy, and it was seriously broken. Wouldn't even launch. It's written in Java or something. Then I tried BitTornado, but it was just a shell for BitTorrent. Finally, I found Ktorrent and it is great.

---

### Post by cmost on 2007-05-12
I use Azureus on amd64 and have since Dapper.  It's certainly not broken (far from it,) and, it's the best bittorrent client around (in my opinion and many others in the tech world.)  The absolutely easiest way to install it is to use Automatix2.  It will install and configure all the necessary dependencies for you.  Good luck.

---

### Post by cn9ne on 2007-05-12
Azureus from Synaptic is rather buggy, it couldn't launch at all. Thus, I installed Automatix2, and installed Azureus from there. It worked like charm.

---

### Post by strumluff on 2007-05-12
My preference in windows in utorrent, so I have it in linux too using wine :D I like it because it's a very small application, smaller than Azureus and I also prefer it over Azureus as it's not in java, and it is just as complete in features.

---

### Post by John Jason Jordan on 2007-05-12
> **cn9ne said:**
> Azureus from Synaptic is rather buggy, it couldn't launch at all. Thus, I installed Automatix2, and installed Azureus from there. It worked like charm.
Seeing the above I decided to give Azureus another chance. I already had Automatix installed on my Feisty amd64 laptop, so I used it to install Azureus. Indeed, it launched just fine and appeared to run OK. Not quite as nice as Ktorrent, but it worked OK. However, I have to say I was annoyed to see Automatix install Sun Java 6 -- if I had known it was going to require it I would never have started the installation. Sun Java 6 is still buggy and I don't want it on my computer. It also installed a bunch of fonts that I don't want.

But having installed it I decided to take it for a trial run because I've been meaning to download the ISO for Fedora 7 test4 amd64. It downloaded about 35%, then locked up the computer with the CPU at 100%.

Azureus is now uninstalled and will remain so. So is Sun Java 6 and the stupid fonts I didn't want.

---

