---
title: "to Chroot or not to Chroot"
date: 2006-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by artik on 2006-12-21
There are lots of discussions on "HOWTO" run specific application under 64. Wine/real etc etc.

Most of them require some kind of work or figuring out howto do. These HOWTOs do not cover 100% of possible programs or issues I might want to install:
Games/3d part programs etc.

Isn't it simpler to install chroot at the beginning and solve all the issues in one strightforward way - apt-get32 it?

What pros and cons of each way?

---

### Post by xopher on 2006-12-21
The simplest way would be to install a 32-bit system. 

No, but I've never taken the time to install a system inside a system to run an application that I should be able to 'just run'(tm). I've been using ia32libs, which work quite well. For flash, I use nspluginwrapper, which works just fine. .

For me, chroot has always meant more work. That's why I don't use it. I don't like having to do 2 things to accomplish 1. I like it the other way around.

Im not telling you not to do this, just to think it over. Maybe re-evaluate your need for 64-bit, if you really need 32-bit programs still. Everything is shifting towards 64-bit, true. But it won't be ready over night. It'll take time to complete the conversion. And Im sad to say, we have to wait for the windows world to change first. Because major companies won't do the work if it's not required it seems.. 

Oh well, hope I didn't confuse you even more, this was just an opinion, and you should in no case take it too seriously. Make up your own mind.

---

### Post by artik on 2006-12-21
Actually I do not have 1000 32bit programs to run...

But I have found nspluginwrapper not stable enoght, and I need Epiphany 32... I need to run a game that uses lots of libraries that not exist in ia32 etc. So in many cases it looks like much simpler to do a chroot and not to look for certain solution each time I want to run a program (where to get libraries etc).

---

### Post by mojoman on 2006-12-22
I've been running 64-bit dapper for a couple of months now, and the few 32-bit programs I've been running have been with forced architecture and it works well enough. However, this morning I installed a 32-bit chroot, because, well, I like things clean and stable and I reckon that the chroot option is just that. Also, I wanted to learn the basics of chroot and there's no better way then learning by doing. Apart from clean and stable it's easier to install things in chroot BUT it's more work to launch them. Chroot so far looks good to me but who knows what worries I'll run into ahead, given that I just installed it? ;) 

Best regards
/Mojoman

---

### Post by pseudonym on 2006-12-22
I'll cast another vote for the chroot method. I built my 64-bit desktop system a couple weeks ago and have been running AMD64 Debian (my main OS) for about a week. I'm about to throw on AMD64 Ubuntu as well, because I like to keep my hand in with how the distro is progressing.

Anyway, back to chroot. Like many here, I don't want to live without Flash, Java, and Acrobat browser plugins (not to mention w32codecs). Having looked at the HOWTOS for the ia32-libs approach, I'm more attracted to the ability to install, update, and remove 32-bit programs in the relatively uniform and seamless fashion that chroot offers. Then using schroot, you are able to start these programs in a fairly transparent way, too.

Some problems I've noticed -

1. I had some inexplicable issues creating valid symlinks to browser plugins when using the 'official' Firefox from getfirefox.com (I won't go into all the details). The situation was resolved by simply installing the packaged browser, which creates all the necessary links during installation.

2. Depending on which programs you run, and how complex your disk partitioning scheme is, you have to create a lot of bind mounts if you want the chrooted programs to have access to all your data. This is not necessarily a problem, but it does add an extra level of administration to your system.

I guess in terms of extra work, both chroot and ia32-libs involve some degree of it. But from the perspective of the most ordered system, I think chroot is the better option.

But maybe that's because I'm anal about it all ;)

I will be using ia32-libs to install the few games I run under Linux, though (I'm keen to see how Quake4 goes on this new machine). The others I play reside on my 'Wintendo' - wine/cedega are a waste of time IMHO if you have one of those.

---

