---
title: "File Sharing Programs in 64-bit"
date: 2006-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by dahli.llama on 2006-01-23
I am trying to find a decent p2p program to use in my 64-bit Ubuntu install.  I like BitTorrent and all, but I find it difficult to actually find anything useful, and too often I can't get any decent speed out of the download.  I have aMule or whatever it is installed, but I find that to be a real pain to setup and get any kind of search results.

I've used Limewire and Bearshare in the past and found them very useful, but there doesn't seem to be a 64-bit compatible version of Limewire available.

I know I could setup a 32-bit chroot for this, but I haven't had to do that for anything else so I figured I'd ask here first to see if there were any good 64-bit native programs.

Thanks.

---

### Post by FluffyElmo on 2006-01-24
There are several giFT frontends in the repositories. Enable universe and multiverse in Synaptic and you should be able to install them. I use *Apollon*, but if you don't want to install all the KDE libraries *giFToxic* is very good.

Two tips...first, when installing make sure you search for *giftd* and install all of it's recommended packages. *libopenft-gift* and *libgnutella-gift* add support for the Kazaa and Gnutella protocols respectively...a file sharing program isn't much good without networks to connect to :)

Second, after you've installed the packages you then have to run *gift-setup* from the command line and configure the various options for it to work. As a rule, after this if *giftd* runs from the command line without errors then the front-ends should both work.

Another thought is that any of the Java based programs like Limewire work fine. I simply prefer gift because it connects and searches multiple networks at the same time.

---

### Post by awi on 2006-01-26
I use [COLOR="DarkOliveGreen"]azureus[/COLOR] for bit torrent, and [COLOR="DarkOliveGreen"]amule[/COLOR] for edonkey network.

---

### Post by chrisv on 2006-01-27
now how do you get azerus to work on ubuntu 64? Doesnt that use Java 1.5 for which supposedly there is no 64 bit version?

---

### Post by FluffyElmo on 2006-01-27
There is a 64bit version of Java 1.5, several of them actually. Just no 64bit browser plug-in (Even then Blackdown has a plug-in I think, though it may only be 1.4.x). Azureus , Eclipse, Limewire and other Java applications run perfectly. 

You can search the forum for instructions on installing a JVM using apt but personally I just download the AMD64 JDK from [http://java.sun.com]("http://java.sun.com") or the JRockit JDK from [http://www.bea.com]("http://www.bea.com") and install them from the command line. 

Just *chmod 777* the .bin file you download and then run it. Also, when you download Azureus make sure you choose the AMD64 version.

---

### Post by D_frag on 2006-09-17
> **FluffyElmo said:**
> There are several giFT frontends in the repositories. Enable universe and multiverse in Synaptic and you should be able to install them. I use *Apollon*, but if you don't want to install all the KDE libraries *giFToxic* is very good.

Two tips...first, when installing make sure you search for *giftd* and install all of it's recommended packages. *libopenft-gift* and *libgnutella-gift* add support for the Kazaa and Gnutella protocols respectively...a file sharing program isn't much good without networks to connect to :)

Second, after you've installed the packages you then have to run *gift-setup* from the command line and configure the various options for it to work. As a rule, after this if *giftd* runs from the command line without errors then the front-ends should both work.

Another thought is that any of the Java based programs like Limewire work fine. I simply prefer gift because it connects and searches multiple networks at the same time.

i tried using this but when i type giftd at the command line i get this nothin it doesnt even take me to a new line the cursor just goes down

i installed then the gifttoxic and it doesnt seem to connect it says not connected and it doesnt see my shares 0 shares 0 mb

---

### Post by FluffyElmo on 2006-09-17
It's normal for giftd to not have output on the command line unless there is an error. Giftoxic also can take a short while to connect without any feedback. If it still doesn't connect after a few minutes make sure you installed at least one of the protocol packages and configured it when you ran giftd-setup.

Also, if you have a firewall make sure that you have opened all necessary ports. Giftoxic doesn't really give any useful errors if they aren't. The ports you need should be in the config file or viewable through giftd-setup.

Apollon is slightly more configurable and may give more feedback than Giftoxic. It will at least show what network plug-ins are installed.

---

### Post by FatalAstro on 2006-10-04
The best p2p is ktorrent for linux ubuntu. I am using it now, and it is very fast, reliable, and if the pc needs to be shut down fast, or it does by itself, the files doesnt need to be rechecked as in windows, so they start up fast again when restarted. Rocks my p2p world.

---

