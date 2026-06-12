---
title: "New Skype 1.4 alpha works great,  this is my How-to"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by johnficca on 2007-05-02
there is a new alpha version of skype for linux its 1.4 alpha and it works great for me on my 64 bit box, I just downloaded the [[COLOR="DarkOrange"]skype-alpha-1.4.0.58-generic[/COLOR]]("http://www.skype.com/go/getskype-linux-alpha-generic") and did this in the terminal:
> cd Desktop
tar -xvjf  skype-alpha-1.4.0.58-generic.tar.gz
cd skype-1.4.0.58_alpha/
sudo mv skype /usr/bin/
sudo mv sounds/* /usr/share/skype/sounds/ 

note this would only work if you already have skype installed as you cannot yet create a new account in this alpha release 

so then I started skype from the terminal and it said I needed libqtgui.so.4 or something, so I went to this page [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and did a search for libqt and I found one called libqt4-gui downloaded the i386 version extracted it, clicked on the new folder and extracted the data.tar.gz, clicked on that folder then on the lib folder then copied all of that to my usr/lib32 folder the command is this if your in the libqt4-gui_4.2.3-0ubuntu3_i386.deb_FILES/usr/lib  folder.
> sudo cp * /usr/lib32 
then I tried skype again and It said I needed libqt4-core your pc might be different but I needed these   three packages 
libqt4-gui_4.2.3-0ubuntu3_i386.deb
libqt4-core_4.2.3-0ubuntu3_i386.deb
libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb

and I did the same with all of them as I did with libqt4-gui.
then I started skype and it fired right up and looks great and works better, I think I needed to play with the sound options to get the callin ringing to work so I click on options > notifications > incoming call ringing, then I click on the little box that said callringingin.wav, then I got a choose file box click on callringingin.wav then on open then clicked apply and it worked. If you have a question I don't know if I can help but I will try.

---

### Post by mikewhatever on 2007-05-02
With all this excitement, what exactly does work better? You forgot to tell. Hope you haven't forgotten it yet, and yes ..., congratulations.

---

### Post by johnficca on 2007-05-02
Oh sorry its the sound I had a lot of problems before, but with this version I don't

---

### Post by NeilBlanchard on 2007-05-02
Greetings,

If I'm not mistaken, there was no 64bit version of Skype before?  If this version works in 64bit Linux, then that is a good thing!

---

### Post by rsambuca on 2007-05-02
Man, I was shocked when I saw the article on the new alpha version.  It has been so long that I was positive skype dumped all linux support after ebay bought them out.

---

### Post by ndefontenay on 2007-05-03
Is there any webcam support for the new skype release?

---

### Post by johnficca on 2007-05-03
Yeah I was hoping for video support as well, but I guess we'll have to wait for the next release for that. The GUI has been redesigned so it takes a little time to get used, but I like it a lot more.

---

### Post by chris.olsen on 2007-05-07
I was having audio problems as well on the last one, so hopefully this will have fixed them.  

Thanks for the tips

---

### Post by evilfourzero on 2007-05-07
Thanks, your instructions worked great! I put together a nice little script to do the installation for you if anyone is interested:

[http://evilfourzero.net/skype-1.4-alpha-installer.sh](http://evilfourzero.net/skype-1.4-alpha-installer.sh)

---

### Post by johnficca on 2007-05-07
wow thanks for the script, see this is what makes the ubuntu community so great. We will need to keep the script updated as they said at the skype blog they will be releasing every few weeks or so. I would like to learn how to write scripts for ubuntu linux, could you point me in the right direction. thanks

---

### Post by Cappy on 2007-05-07
> **evilfourzero said:**
> Thanks, your instructions worked great! I put together a nice little script to do the installation for you if anyone is interested:

[http://evilfourzero.net/skype-1.4-alpha-installer.sh](http://evilfourzero.net/skype-1.4-alpha-installer.sh)

Your script only works on i386. The AMD64 should use the static binary.
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

