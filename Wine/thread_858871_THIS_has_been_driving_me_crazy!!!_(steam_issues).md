---
title: "THIS has been driving me crazy!!! (steam issues)"
date: 2008-07-14
forum: Wine
---

### Post by em4g.3ht on 2008-07-14
first thing is first, I am a n00b when it comes to linux, i just recently switch from vista (finally). I love everything about the open source community and I'm learning fast.

there is only one problem, steam games are not working. Steam itself works, and same with some other windows programs i couldn't live without (dvdflick, gpl dvd authoring tool works amazing in wine). I have 2 games i have tried. team fortress 2, which will get through the intro video's then crash before the game menu, and UT3 which doesn't even work at all. I haven't tried many things because i have been busy playing, ETQW :).

here's what i have tried:
forcing DX8 and selecting my native resolution
updating WINE

hardware:
i have a intel quad core (q6600); hd 2900xt; x38 mobo; if you need more specs just let me know.

I do have compiz fusion running, but i turn it off when i play games.

ANY help would be much appreciated!!! this has been annoying me for a while now!!

oh and would prefer not to use cedega if i have to...

oops i forgot: Im using the new hardy 8.04 64bit edition. I was also reading through some forums, and it appears that wine has a 64bit edition now and I was wondering could my problem be because i did not get the 64bit edition? I just used the apt-get to get wine, off the default ubuntu repositories

---

### Post by Spydr4590 on 2008-07-14
Hello, and welcome to the forums! You're going to have some issues with gaming because you're using ATI/AMD for linux. I suggest using these following links.

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) (Tells you how to install ATI Drivrs correctly)

[http://www.phoronix.com](http://www.phoronix.com) (Great forum support for ATI users. Offical ATI Engineers post on this board)

As for your problem with steam or any other games. You're not going to get any to work using directx with an ATI card. I suggest you use wine registry hacks and force opengl rendering. [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) This will be listed under Direct3D.

---

### Post by em4g.3ht on 2008-07-14
Thank you for your reply!!! I will deffenetly look into that tomorrow. ( I woke up for no reason 3:30am here)

I thought ati was getting much better linux support in general, with support out of the box with there newest hd 4xxx series.


As for the not being able to use directx (I could be really wrong here) but i belive this thread had someone with a similar set up get steam games working. However, this didn't fix my problem. :(

[http://ubuntuforums.org/showthread.php?t=841864&highlight=steam+games]("http://ubuntuforums.org/showthread.php?t=841864&highlight=steam+games")

As for ati game support, though these opengl it looks like support is getting better.

[http://www.phoronix.com/scan.php?page=article&item=824&num=4]("http://www.phoronix.com/scan.php?page=article&item=824&num=4")

---

### Post by em4g.3ht on 2008-07-14
I am currently updating to the new 8.6 drivers, from the 8.4 drivers using the guide Spydr4590 sent me (THANKS), when i type sudo apt-get update, i get this wine error 

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

can anyone help me with what this means?

---

### Post by em4g.3ht on 2008-07-14
UPDATE! i used the guide provided

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

 and i get an error at the end, right after i edit the xorg file with this command

sudo gedit /etc/X11/xorg.conf

i then proceed to type (copy paste, cause i'm a n00b) 

sudo aticonfig --initial -f

which gives me this error

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  146 (ATIFGLEXTENSION)
  Minor opcode of failed request:  7 ()
  Serial number of failed request:  10
  Current serial number in output stream:  10


when i try to force it with this command

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1


i get the same error



that was the last step of the guide, i am a little afraid to restart, without knowing what this error means....

thanks again for any help, and I appologize for my ignorance.

---

### Post by Spydr4590 on 2008-07-16
I would post on the phoronix forums, they will be able to assist you better then I can. I haven't used a ATI card on Ubuntu since January. I'm using Nvidia right now.

---

