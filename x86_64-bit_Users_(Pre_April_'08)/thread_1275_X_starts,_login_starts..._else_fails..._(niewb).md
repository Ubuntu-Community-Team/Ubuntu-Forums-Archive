---
title: "X starts, login starts... else fails... (niewb)"
date: 2004-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by latrine on 2004-10-19
Just like that... X starts, i type the login/pwd combination, the login screen disapears, and I have a beautifull grey screen with an operational mouse pointer that does nothing... at least the mouse works...

keyboard seems not to work except that num lock light is functional...

I have tried in all Gnome option in the login screen, and it is always the same...except for the comand line that works... exactly the same way as never having started X

I know I have no internet cos I am on wireless and will need ndiswrapper working to get this part...

The only time I got it working in text mode was starting in safe mode from grub menu, and typed

sudo apt-get install nvidia-glx 

and the answer was exactly the same.. nothing... except this time there was no grey (X wasn't started ;) ) and the keyboard worked... at least it wrote on the screen...but never got to ctrl+c properly and ctrl+alt+del did nothing...

Computer:

A64 3200
abi kv8pro
nvidia geforce 4400
Portuguese as language...
------------------------------

Edit

I re-installed the system and it does almost exactly the same, just now ctrl+alt+F1 opens another login window as usual. keyboard works ok


So I have now command window access... what can I do? is there some "test" I can do? 

I have  VI"ed" /etc/X11/XF86Config-4 and it seems to be in order, it even has detected my geforce 4400...

I have tried to do a 
sudo dpkg-reconfigure 

and systems just does nothing, but I have keyboard output... (cannot ctrl+c)

I am going lunatic here...

Good work by the way!
Latrine

---

### Post by Baloo on 2004-10-27
I've got exactly the same problem. Did you manage to fix it?

---

### Post by Pluk on 2004-10-27
I get that when my session file refuses to work.

Maybe you could try to delete:
/home/username/.gnome2/session

---

### Post by Baloo on 2004-10-27
[QUOTE=Pluk]I get that when my session file refuses to work.

Maybe you could try to delete:
/home/username/.gnome2/session[/QUOTE]

Even sudo not working?

---

### Post by latrine on 2004-10-27
Not exactly...

I discovered that doing this:
ctrl+ alt+f1 
login+ password
then type

ps aux 

look for the number of a process (#pid) called bonnomo-activation

kill #pid

seems to unblock the situation... and then gets to an alt again... 

can you try to see if it happens to you also?  I believe this would be enough to be considered a bug :)

I See you also have an abit kv8 pro (from other threads)... you have internet connection via the gigabit port?

---

### Post by jdong on 2004-10-27
Yeah, that's a bug.... file it!

---

### Post by latrine on 2004-10-28
I am just wating for the shiped cds to try it once more...

---

### Post by daniels on 2004-10-28
I believe you need to install and start using the 'nvidia' driver on AMD64 -- the 'nv' driver with X.Org does not support AMD64.  See [http://wiki.ubuntu.com/BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto).

---

### Post by Baloo on 2004-10-29
[QUOTE=latrine]Not exactly...

I discovered that doing this:
ctrl+ alt+f1 
login+ password
then type

ps aux 

look for the number of a process (#pid) called bonnomo-activation

kill #pid

seems to unblock the situation... and then gets to an alt again... 

can you try to see if it happens to you also?  I believe this would be enough to be considered a bug :)

I See you also have an abit kv8 pro (from other threads)... you have internet connection via the gigabit port?[/QUOTE]

I'll give it a go.

As for the network port, no and I get a seg fault when booting up although the boot continues. I'll have time to play around some more tonight so I'll see what happens.

---

### Post by latrine on 2004-10-29
[QUOTE=daniels]I believe you need to install and start using the 'nvidia' driver on AMD64 -- the 'nv' driver with X.Org does not support AMD64.  See [http://wiki.ubuntu.com/BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto).[/QUOTE]


Well sudo doesn't work and I haven't got internet.

Starting in a "recovery mode" and typing 

apt-get install nvidia-glx

seems to work, but it replies that doesn't find the package...

I have mounted the ubuntu cd Can I get this package from the CD? How?


1- trying something else... I have reconfigured X to start with a vga card... let´s see what I can do of it...

X doesn't start

2- reconfigured to start with nv but with glide deactivated...
Same result as with NV with glide enabled

3-

---

### Post by Baloo on 2004-10-29
The problem with the network is a bit of a chicken and the egg situation. The kernel supplied with Ubuntu doesn't support the lan chip, you need to download either a newer kernel or the driver from via, which, of course you can't do without a network ;)

---

### Post by latrine on 2004-10-29
Now if to that you add the fact that I am acessing the internet with a linksys wmp 11 pci 2.7 wireless card with a broadcom chip that has no driver in linux, I have to install ndiswrapper that is only on the repository in the internet...

I can't get this to do anything... I have even downloaded the contents of nvidixxxxx directories on ubuntu rpositories, burnthem into a cd, and started a recovery mode... tried via apt-setup to add my cd as a repository and now it asks for a "dist" directory...
What must i write into this directory? can someone tell me? How can I install the packages I have in CD ROM?

---

### Post by latrine on 2004-10-29
That's it.... I Give up. filed a bug report

---

### Post by latrine on 2004-11-02
Solved here:

[http://www.ubuntuforums.org/showthread.php?t=2967](http://www.ubuntuforums.org/showthread.php?t=2967)

---

