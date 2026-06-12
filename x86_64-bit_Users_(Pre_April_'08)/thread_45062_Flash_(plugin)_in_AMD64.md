---
title: "Flash (plugin) in AMD64?"
date: 2005-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by WMCoolmon on 2005-06-28
Obviously it's possible via the 32-bit [chroot](http://ubuntuforums.org/showthread.php?t=24575). But isn't there some way to get it to work, like telling it use the 32-bit libs (as you can do with cedega) so you don't have to boot up a separate instance of firefox?

---

### Post by dmn_clown on 2005-06-28
You can try this:

install the 32 bit Flashplayer on 64 bit linux by editing the install script so that the uname-m check is ignored or just pretends it is i386 rather than x86-64.

or just run your firefox out of your 32-bit chroot.

from this [thread](http://www.macromedia.com/cfusion/webforums/forum/messageview.cfm?catid=184&threadid=994967&enterthread=y) 

Also if you'd like to annoy Macromedia until they do release a 64-bit linux player go [here](http://www.macromedia.com/cfusion/mmform/index.cfm?name=wishform)

---

### Post by Big Venus on 2005-06-29
[QUOTE=dmn_clown]You can try this:

install the 32 bit Flashplayer on 64 bit linux by editing the install script so that the uname-m check is ignored or just pretends it is i386 rather than x86-64.

[here](http://www.macromedia.com/cfusion/mmform/index.cfm?name=wishform)[/QUOTE]
How the world do you get this to work like that because the way I did it, it said that it couldn't load the flash (something) and its libflash(something)...

---

### Post by ::DoGG:: on 2005-06-29
dmn_clown

For me the only way to get flash working without the chroot in pure 64 is to use it with onqueror which uses the 32 bit libraries to launch the flash. If You use konqueror and flash with the tweaked flash you can be quite succesfull ( done that once on Fedora Core x86_64). I don`t think that 64 bit firefox will work with 32  bit flash player, tried that, didn`t get no sleep and end up with chroot. I think it just won`t work since firefox using 64 libraries and flash is 32 and want to use 32. With the tweaked script You probably end up on firefox told You  that you just don`t have the plugin, or the loading of plugin failed.
regards.

---

### Post by Big Venus on 2005-06-29
[QUOTE=::DoGG::]dmn_clown

For me the only way to get flash working without the chroot in pure 64 is to use it with onqueror which uses the 32 bit libraries to launch the flash. If You use konqueror and flash with the tweaked flash you can be quite succesfull ( done that once on Fedora Core x86_64). I don`t think that 64 bit firefox will work with 32  bit flash player, tried that, didn`t get no sleep and end up with chroot. I think it just won`t work since firefox using 64 libraries and flash is 32 and want to use 32. With the tweaked script You probably end up on firefox told You  that you just don`t have the plugin, or the loading of plugin failed.
regards.[/QUOTE]
I have had problems with chroot, so I thought modifying the code would help and it didn't...

---

### Post by Terracotta on 2005-06-29
Hehe, I filed to complaint's on the macromedia request site:
1) it isn't rendered well, I can't check wether it's a bug report, or a request,
2) there's no 64 bit flash player.
Ohh, all this complaining is fun.

Just one more question, how do you get konqueror use the 32bit libs??? when you can't install flashplayer since it's a i386 file???
Tx anyway.

---

### Post by dmn_clown on 2005-06-29
> I have had problems with chroot, so I thought modifying the code would help and it didn't... 

Maybe with enough polite requests Macromedia will port flash to Linux AMD64...

The thread I linked to isn't very clear on how well it worked or what additional libs were needed.  Myself, I run firefox out of a 32 bit chroot when I need multimedia support.  Neither of which is really a solution.  The solution IS Macromedia porting flash to Linux AMD64.

I got the chroot setup by hacking together [this](https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id274326) and [this](http://www.seanius.net/linux/amd64/cedega-hl2-amd64.html) You do not need to mount the passwd, group, or shadow files, just copy them into the chroot's /etc directory (assuming a single user system, with multiple users the files should be bind mounted to eliminate any future copying on the admin's part).  This will work in Ubuntu, just type 'sudo bash' in your favorite shell and the difference is negligible.

---

