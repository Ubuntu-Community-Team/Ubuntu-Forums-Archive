---
title: "Windows games in Ubuntu"
date: 2008-10-21
forum: Wine
---

### Post by UpBhUiTlU on 2008-10-21
Hi,

I´m new here, please don´t shout at me if I´ve done or said the wrong thing.

I got Ubuntu on Saturday, it´s brilliant!!! So much better than Windows XP, which I used to have. Sorry if one of these have already been posted.

Anyway, I have a couple of games that I used to play reguarly when I had XP. I found out about WINE by reading these forums (thanks) and tried to play the game with WINE. Problem is, they all run extremely slowly in the menu´s, then when I go into the gameplay, the whole game freezes up, and I end up having to restart the whole computer. I found out that there is no such thing as DirectX for Ubuntu, and both games need DirectX 8.1 or above. I was wondering if it is at all possible to play Windows games successfully in Ubuntu? I would really like to play these games. Or is there a DirectX for Ubuntu?

Thanks for all your help,

UpBhUiTlU :lolflag:

---

### Post by aoanla on 2008-10-21
So, firstly, you are a little confused.

There is no such thing as DirectX for anything but Windows, this is true. That's because Microsoft wrote DirectX, and so it chooses not to make it available for any other OSs (other than their consoles, of course).

Wine, however, does provide a DirectX "translation layer" - it has to, for a large amount of Windows stuff to work. This translation layer turns DirectX calls into OpenGL (and ALSA and so on) calls, which are much less OS dependant and work in linux.
The support for DirectX 8.1 is almost totally complete.

Specific games may work more or less well in Wine. The best first thing to do is to look them up in the Wine Applications Database (which, incidentally, is linked in the sticky about "things you should do before posting here"), here:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

If there's nothing useful about them there, or the comments don't help, feel free to post here about them and ask for advice.

---

### Post by arunvir on 2008-10-23
search for winetricks.......
I installed directx 9.0c with it today in wine.........

It can help you install way lots of stuffs.......

---

### Post by rocky5051 on 2008-10-23
Did you install the accelerated graphics drivers for your video card? The open source ones Ubuntu sets up initially do not support hardware acceleration.

---

### Post by toasty_ghosty on 2008-10-23
Another thing I would try is PlayOnLinux. I got Counter Strike Source working without any real issue. Seems to work great!

---

### Post by Espryon on 2008-10-24
It is possible to get the games to outrun the fps on windows by about 250 fps if you know what your doing look on the wine or ubuntu wine faqs for the registry tweaks. Atleast from my experiance and also individual programs sometimes use individual tweaks and you should preferebly use a stable edition not a development or beta ubuntu. Ive had it for two years and ive only had to reload ubuntu once, i hope you have the same luck (:

Also if your having trouble installing graphics drivers look up envyng

---

