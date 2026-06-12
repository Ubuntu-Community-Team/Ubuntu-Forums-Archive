---
title: "Help me to install the 64 bit flash player"
date: 2009-09-28
forum: x86 64-bit Users
---

### Post by hoboy on 2009-09-28
I have 
Linux ubuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

So I need a compatible flash version, and how to install it.

---

### Post by Yellow Pasque on 2009-09-28
Installation is very easy if you don't have any kind of flash already installed.

```
cd ~
mkdir ~/.mozilla/plugins
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xzf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
mv libflashplayer.so ~/.mozilla/plugins
```
(Restart your browser)

If you do have other Flash versions (gnash, swfdec) and/or 32-bit Flash (with nspluginwrapper), search this forum for a script that purges all of that stuff.

---

### Post by hoboy on 2009-09-28
> **Temüjin said:**
> Installation is very easy if you don't have any kind of flash already installed.

```
cd ~
mkdir ~/.mozilla/plugins
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xzf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
mv libflashplayer.so ~/.mozilla/plugins
```
(Restart your browser)

If you do have other Flash versions (gnash, swfdec) and/or 32-bit Flash (with nspluginwrapper), search this forum for a script that purges all of that stuff.

They other flash installed.

---

### Post by hoboy on 2009-09-28
I need script to flush all the old flash that are installed

---

### Post by hoboy on 2009-09-28
Tks Temujin
I did run the following 
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
sudo apt-get remove ia32-libs nspluginwrapper

Then then follow your advice, it work like a charm.

---

### Post by michael37 on 2009-09-29
[thread=1259102]A sticky thread right on the top of x86_64: Adobe Flash install information for AMD64 (September 2009 update)[/thread]

Next time, try searching for answers first... ):P ):P

---

### Post by Slim Odds on 2009-09-29
> **michael37 said:**
> [thread=1259102]A sticky thread right on the top of x86_64: Adobe Flash install information for AMD64 (September 2009 update)[/thread]

Next time, try searching for answers first... ):P ):P

Or just look    :)

---

### Post by Guy Sibley on 2009-10-01
I hope no one mistypes what you wrote... like rm-rf etc.
also, I am using 64 bit jaunty and for firefox flash I simply did
 
Sudo apt-get remove flashplugin-nonfree
Sudo apt-get install flashplugin-nonfree
 
now flash works pretty well, and it was very simple.

---

### Post by michael37 on 2009-10-01
> **Guy Sibley said:**
> I hope no one mistypes what you wrote... like rm-rf etc.
also, I am using 64 bit jaunty and for firefox flash I simply did
 
Sudo apt-get remove flashplugin-nonfree
Sudo apt-get install flashplugin-nonfree
 
now flash works pretty well, and it was very simple.

Works "pretty well" is a relative term in your statement considering your are running 32-bit flash in a wrapper and you probably briefly tested it on one or two sites.  Try to gauge performance with a high definition content on a full screen (e.g. from Youtube, click HD and full screen)... let us know whether your "pretty well" holds.  Please post your experience and your computer specs.

P.S. Please validate your statements before making recommendations to the greater Ubuntu community.

---

### Post by Slim Odds on 2009-10-02
Just download and install the 64 bit flash player from Adobe. Follow the instructions that they give.

It's alpha, but it works great.

---

### Post by HappyFeet on 2009-10-02
Once and for all:

[Here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") is the 64bit flash file. I will assume it is now on your desktop. Right click>extract here. Open terminal.
```
sudo cp /home/your_user_name/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Restart firefox. Have a nice day on youtube.

---

### Post by NoaHall on 2009-10-03
Follow the advice in my sig if the above doesn't work.

---

### Post by thewanderer on 2009-10-05
And to reiterate further.

Fresh install of 64bit Karmic Beta.

> To install the 64bit flash player in Karmic:

Download from here -> [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/


Done.

---

