---
title: "BBC iPlayer on Ubuntu 8.10 AMD 64 - start of a solution??"
date: 2009-03-02
forum: x86 64-bit Users
---

### Post by gdbutcher on 2009-03-02
I have used a variation of this [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins") to install BBC Iplayer on Ubuntu 8.10 AMD64 using 32 bit firefox. 

Unfortunately Iplayer doesnt download anything yet. 

I'm fairly new to Ubuntu, so I thought I'd turn what i've done over to you guys.
Someone more experienced maybe able to take it further, or suggest better ways of doing this. 

Any comments, suggestions, corrections are more than welcome.

Here goes:

1. Copy and paste into terminal:

```
sudo apt-get install ia32-libs lib32asound2 util-linux
```

2. Copy and paste this into the terminal to download Firefox:

```
wget http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.6/linux-i686/en-GB/firefox-3.0.6.tar.bz2 
```

3. Back into the terminal, copy and paste the following:

```
cd Desktop
tar  -xvjf firefox-3.0.6.tar.bz2
sudo mv firefox /usr/local/firefox32 
```

4. Copy and paste the following into the terminal:

```
sudo mkdir /etc/pango32 
```

then 

```
gksudo gedit /etc/pango32/pangorc & 
```

In the open pangorc file copy and paste the following lines, when done, save and close gedit:
```

[Pango]
ModuleFiles=/etc/pango32/pango.modules
[PangoX]
AliasFiles=/etc/pango/pangox.aliases 
```

5. Copy and paste the following into the terminal:

```
gksudo gedit /usr/local/bin/firefox32 & 
```

then these lines into gedit, when done, save and close gedit:

```

export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32
linux32 /usr/local/firefox32/firefox "$@" 
```

6. Back into the terminal, copy and paste the following:

```
 sudo chmod +x /usr/local/bin/firefox32 
```

7. Copy this line into terminal to download Flash 10 Plugin:

```
 wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz 
```

Extract Flash:

```
 -zxf install_flash_player_10_linux.tar.gz 
```

Install plugin:

```
 sudo mv install_flash_player_10_linux/libflashplayer.so /usr/local/firefox32/plugins/ 
```

***Now Close all firefox windows***

7. Back into terminal,Start firefox32 with the command: 

```
 firefox32 
``` 

8. Go to [http://www.bbc.co.uk/iplayer/labs]("http://www.bbc.co.uk/iplayer/labs") then click on "I want to be a Labs tester" Then click "start using iPlayer labs features" 

You should now be at the iPlayer itself select a show your interested in, click on "To Computer" 

Then "Install BBC Iplayer Desktop" follow the instructions to install. 

It does install but I can't download anything once its done. Unfortuateley thats as far as I can get it, anyone got any ideas?

---

### Post by gdbutcher on 2009-03-10
I suspect the problem is that the iplayer opens the 64 bit firefox, not the 32 bit one when trying to download anything. 

I tried removing firefox 64, and setting firefox 32 as default browser in System > Preferences > Preferred Applications but that didn't work either.

Is there a way of completely replacing the 64 bit firefox with the 32 bit version? or am I just wasting my time?

---

### Post by gdbutcher on 2009-04-09
It appears to be impossible to get the iplayer working natively on Ubuntu 64. 

Martin's solution here at the bottom of this page is the closest I got to it: [http://wiki.flexion.org/BBCiPlayer.html?index]("http://wiki.flexion.org/BBCiPlayer.html?index")

The Iplayer installed but wouldn't download anything.

I've spent hours trying to get it to work on Ubuntu 64. In the end I downloaded the Ubuntu 9.04 32 Bit beta and within 35 mins the Iplayer was installed and downloading. I haven't noticed any drop in performance from going from 64 bit to 32 bit.

I love Ubuntu 64 and I have learnt a hell of a lot from using it but sometimes you just want things to work without the hassle and it seems to me that unforunately 32 bit is the way to go for me for the time being. Gutting. :(

---

