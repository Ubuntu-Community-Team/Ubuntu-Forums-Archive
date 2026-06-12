---
title: "Freezea like windows"
date: 2006-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by pac614 on 2006-06-11
at first i had trouble installing the dapper, cuz the live cd wouldn't work, when it's about to display the X, i get the mouse cursor and the whole thing would freeze like windows...

i got passed that problem by using alternate CD and used the text mode setup.

but then again, i get the same problem when i boot up ubuntu,
sometimes it freezes and gives me the black screen before anything happens,
some other times, it loads the X and then freezes after finishing loading
nautilus and at the desktop.

I really have no idea what's going on.

here's my spec::
AMD64 3000+
RAM 1GB 
ATI Radeon 9600 Pro

plz help me:(

---

### Post by kuja on 2006-06-11
This could perhaps be an issue with the video driver, one thing that could possibly help would be to reconfigure x.

Try rebooting in single user mode (there should be an option for this while booting), and doing the following.

In the terminal type in ```
 more /etc/X11/xorg.conf 
```

Look for a section called "Device". There should be a driver line, it will probably list "ati", "radeon", or "vesa". 

Type in ```
sudo dpkg-reconfigure xserver-xorg
```

When it asks you if you want to automatically select the video configuration, say no - choose one of those drivers (ati, radeon, vesa), one that's not already in use. Switch amongst them to things that haven't been tried already, it may be worth a try.

---

### Post by pac614 on 2006-06-11
hey, first of all thx

i don't know what you mean by "single user mode",
because i don't seem to have that as one of my options at boot up,
but i do have recovery mode, so i did what you've suggested there,
no luck.

hm..
any other suggestions ??

---

### Post by kuja on 2006-06-14
I'm really out of ideas here ... not sure what it could be to be honest. if you're desperate, there are a couple of other things you can try. Try running ```
apt-get dist-upgrade
``` in recovery mode. Another thing that could be off on a tangent would be to check your memory for errors(there's an option for that at boot as well). Do you have anything else working fine on your computer?

---

### Post by henriquemaia on 2006-06-14
[quote=pac614]hey, first of all thx

i don't know what you mean by "single user mode",
because i don't seem to have that as one of my options at boot up,
but i do have recovery mode, so i did what you've suggested there,
no luck.

hm..
any other suggestions ??[/quote]

Try reading this post:

[http://www.ubuntuforums.org/showpost.php?p=824011&postcount=3](http://www.ubuntuforums.org/showpost.php?p=824011&postcount=3)

and follow those instructions. Maybe that will help.

---

