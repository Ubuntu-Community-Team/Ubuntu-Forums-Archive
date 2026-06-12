---
title: "Has anyone got Realplayer working in amd64?"
date: 2006-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by JungleBeast on 2006-04-28
Hello there, just wondering if anyone has managed to get realplayer working in amd64 without chrooting?     
Maybe in a similar manner to firefox32 with flash and java?

If so I'd love to know how!  :D

---

### Post by John Jason Jordan on 2006-04-28
[QUOTE=JungleBeast]Hello there, just wondering if anyone has managed to get realplayer working in amd64 without chrooting?     
Maybe in a similar manner to firefox32 with flash and java?
If so I'd love to know how!  :D[/QUOTE]
Yes, I have it working perfectly on my Ubuntu-64 Breezy computer. But I had to set up a 32-bit chroot environment and install it there. I tried and tried to install it in the 64-bit world, but eventually gave up.

---

### Post by merlin666 on 2006-04-28
It worked fine under Fedora 64 ... haven't tried it with Ubuntu yet. I'm not really sure how the packages etc work here, only used the synaptic stuff.

---

### Post by crwban on 2006-04-28
It works without any hassle in the latest dapper.

Before upgrading to dapper, I was running it successfully in breezy - this post [http://ubuntuforums.org/showthread.php?t=128757]("http://ubuntuforums.org/showthread.php?t=128757") describes what you need to do to get it running...

Unfortunately, you can't use the (32bit) realplayer plugin in 64bit firefox/mozilla. To get that working, you can either install a (non chroot) 32bit firefox [https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava"), or wait for Real to release a 64bit version of realplayer - which they are apparently working on.

---

### Post by JungleBeast on 2006-05-01
Thanks for that! I saw that page before but couldn't get any confirmation as to whether anyone else had succeded. And as last time I tried realplayer I lost firefox, I was feeling a bit more cautious.  So got it up and working, although a few of my lines  differed a bit. I'm not exactly sure why either. 
The link has changed, I used "chown -R " instead of chmod . I think that was what the author meant. and a few other hicups, but it works fine now, all be it without a few pretty icons. 
However it doesn't work with the BBC radio player, is this because it's not integrated with Firefox? any ideas, on how i'd go about fixing this?

---

### Post by John Jason Jordan on 2006-05-01
[QUOTE=JungleBeast]However it doesn't work with the BBC radio player, is this because it's not integrated with Firefox? any ideas, on how i'd go about fixing this?[/QUOTE]
Sorry, no idea on how to fix it. I have it running in 32-bit chroot along with 32-bit Firefox. It works fine, but I can't get BBC to work either. Almost all other streaming radio stations work, though. I listen to nothing but classical and I have dozens bookmarked. Got them from 

[http://mikesradioworld.com/ft_classical.html]("http://mikesradioworld.com/ft_classical.html")

(He has listings for all other genres as well.)

---

### Post by warp99 on 2006-05-01
I have Real Player installed using the same method as Firefox 1.5 using the IA32libs/pangorc work around:

[https://wiki.ubuntu.com/FirefoxAMD64FlashJava?highlight=%28amd64%29]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava?highlight=%28amd64%29")

When making the executable just replace Firefox32 with Realplayer32. Works great with the plugins, but the icons on the player are missing. 

Realplayer tries to load libpixbufloader from the standard GTK libs instead of the 32-bit libs, therefore the icons are missing. I beleive the path for libpixbufloader 32-bit libs may be hardcoded in realplayer since I tried to symlink libpixbufloader 32-bits libs without any success. :cool:

---

### Post by crwban on 2006-05-02
[QUOTE=JungleBeast]However it doesn't work with the BBC radio player, is this because it's not integrated with Firefox? any ideas, on how i'd go about fixing this?[/QUOTE]
This is suprisingly straightforward :) - you need a (non-chroot) 32bit installation of firefox.

A simple way to do this is to download the 32bit (i386 or i686) .tar.gz from [http://www.mozilla.com/firefox/]("http://www.mozilla.com/firefox/"), untar this into /usr/local/firefox, or something similar. Then, you'll notice that the directory where you installed Realplayer has a 'mozilla' directory - this should contain 2 files. Copy both of these files into the 'plugins' directory wherever you installed firefox (e.g. /usr/local/firefox/plugins). Now, if you run the 32bit firefox, and type ```
about:plugins
``` into the address bar, you should see the realplayer plugins there - and the bbc radio player should work.

[QUOTE=JungleBeast]it works fine now, all be it without a few pretty icons.[/QUOTE]
[QUOTE=warp99]Realplayer tries to load libpixbufloader from the standard GTK libs instead of the 32-bit libs, therefore the icons are missing. I beleive the path for libpixbufloader 32-bit libs may be hardcoded in realplayer since I tried to symlink libpixbufloader 32-bits libs without any success. [/QUOTE]
This problem is slightly more involved - but can also be sorted out. The solution depends on whether you're running breezy or dapper.

Dapper:
If you're running dapper, all you need to do is to set the GDK_PIXBUF_MODULE_FILE environment variable to /etc/gtk-2.0/gdk-pixbuf.loaders.32. Typing something like the following into a terminal should work:
```
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32
realplayer-executable-file
```
(Where 'realplayer-executable-file' points to wherever you've installed realplayer, e.g. /usr/local/RealPlayer/realplay). This could then be automated with a script - like the one used to run firefox as described in [https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava"). 

Breezy:
Unfortunately the gdk-pixbuf.loaders.32 file doesn't exist in breezy, so we need to create it. Something like the following should work:
```
sudo cp /etc/gtk-2.0/gdk-pixbuf.loaders /etc/gtk-2.0/gdk-pixbuf.loaders.32
sudo sed 's:/usr/lib/:/usr/lib32/:' < /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders.32
```
Then follow the instructions for dapper, and you should see all the icons in realplayer...

Good luck! :)

---

### Post by JungleBeast on 2006-05-03
Thanks for that! 
Yes, i thought it was just me who wasn't getting the icons! :) 

I'm in Breezy. I tried what you said to get the icons up and running, but I ran into difficulties. I'm new so go easy.. here's my code:

```
chris@ubuntu:~$ sudo cp /etc/gtk-2.0/gdk-pixbuf.loaders /etc/gtk-2.0/gdk-pixbuf.loaders.32
Password:
chris@ubuntu:~$ sudo sed 's:/usr/lib/:/usr/lib32/:' < /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders.32
bash: /etc/gtk-2.0/gdk-pixbuf.loaders.32: Permission denied
chris@ubuntu:~$ chown -R
chris@ubuntu:~$ chown -R chris:chris /etc/gtk-2.0/gdk-pixbuf.loaders.32 chown: changing ownership of `/etc/gtk-2.0/gdk-pixbuf.loaders.32': Operation not permitted

```

Any ideas greatly appreciated!!

---

### Post by crwban on 2006-05-03
Hmm... just tried that myself and got the same problem...
You can try this way - it works for me:
```
sudo -i
cp /etc/gtk-2.0/gdk-pixbuf.loaders /etc/gtk-2.0/gdk-pixbuf.loaders.32
sed 's:/usr/lib/:/usr/lib32/:' < /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders.32
```
Hope that works for you...

p.s. Make sure you log out of that shell with a Ctrl-D afterwards - 'sudo -i' drops you into a root shell, so you can do things requiring root privileges without typing sudo before each command.

---

### Post by JungleBeast on 2006-05-17
Hi there! sorry i've taken so long to get back to you!

Thanks for that, I don't get permission denied now, and it all seems to work fine in the terminal, but when i open realplayer, i still don't have the icons.   
Any ideas?

---

### Post by crwban on 2006-05-17
If the problem is with the gdk-pixbuf loaders, then you should be getting some error messages.
Could you run realplayer from a terminal using: ```
export GCONV_PATH=/usr/lib32/gconv
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32
realplay
``` and show us what output (& error messages) you get on the terminal. Obviously, replace 'realplay' with the full path to your realplayer executable, if it isn't in your PATH variable.

---

