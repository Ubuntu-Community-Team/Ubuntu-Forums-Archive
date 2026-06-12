---
title: "Xgl displays weird graphic artifacts, gconf-editor missing keys."
date: 2006-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by nopasaran on 2006-09-10
Okay, I know that people probably annoy the heck out of you guys with their whining about XGL and compiz. I also searched the 64bit forum but apparently noone has the same problems as I do.

I am really just about to throw my computer out of the window. I have been fighting with this problem for 1 1/2 days now, and I am getting very tired of this, but I really want XGL to work properly.

I installed XGL and compiz for gnome with various tuts and howtos until it finally started. Also tried to buil xgl myself but apparently it can`t find my mesa sources, which I just installed before and I am also providing the path for.

I am using ubuntu dapper 6.06 on an AMD64 machine. I have an ATI radeon 9600 gpu with the latest drivers installed and working fine (8.28.8).

Compiz and XGL are downloaded as debian packages now, I can start both programs just fine. XGL starts as a session in gdm. Now the fun begins:

First off, XGL apparently causes horrible graphical glitches that I haven`t heard anybody talking about on the internet yet. All my window elements like borders and other theme elements become screwed (they look like static on a tv) when I click and open a new window. This seems to appear only when gnome displays that "maximize" effect. After that, I can refresh certain elements to be displayed just normal again, but it`s getting really slow.

When I want to enable the plugins for compiz, I need to edit the keys with gconf-editor like told in the howtos. Those keys should be in /apps/compiz/general/allscreens/options and then active_plugins but I can only see audible_bell as a key in there!!! This is awfull, I have no idea why that is and where to look, NOONE seems to have that error. It`s just plainly missing the key. I have tried reinstalling with all kinds of packages and everything but it doesn`t help. 

Big loada crap and I don`t know what causes all this... also I do not have window borders when compiz is started but I understand that this is a quite common problem and can be solved in different way. First I would like to sort the other stuff out though.

If anyone is willing to help, feel free to tell me to upload my xorg.conf or any other file, I just felt that this post was going to be way too huge anyway and because the progs were already running I didn`t add them.

Thank you in advance...

---

### Post by nopasaran on 2006-09-10
Nevermind this topic. Nobody seems to even look at the post right now and I am way too fed up with this crap to wait for longer. I will install 32bit ubuntu and try again, as that seems to be a better choice. I am sick and tired of commercial developers not supporting 64bit architecture, such as macromedia and all that w32codec mess. So I guess I will be better off not making use of my 64 bit cpu... crap. I hope that this will be easier at some point so I can go back... why the heck did I even buy the processor? :roll:

---

### Post by kuja on 2006-09-10
I'm almost entirely certain that your problem is not related to the 64-bit cpu. What I can tell you though is that it is likely a problem with the **highly experimental potentially unstable** compiz software. A less likely possibility is a problem with the graphics driver. I'm quite sure that XGL is not the problem... I've played with it (on its own, without compiz) and found it to be quite stable, perhaps more stable than Xorg.


As per other 64-bit problems, I'm sorry you feel that way, though they are easy to work around. You're not going to let one little thing stop you are you?

---

### Post by nopasaran on 2006-09-10
Yeah, I have it running now. I can tell that xgl is pretty stable. Must have been compiz. I followed the same tut and used the same repositories for 32bit now and it works like a charm. But I am ok with running 32bit linux now. I can at least get a decent and non complicated flash plugin now. Some things are just easier this way.

---

### Post by bittergourd on 2006-09-22
i have exactly the same problem. there is only one item whereas it was said to be a bunch of compiz settings.

aother problem i have with compiz is that i have to start all plugins in the startup script as 

gnome-window-decorator & compiz --replace gconf decoration fade minimize cube rotate zoom scale move resize place switcher trailfocus water blur &

otherwise no title bar, no virtual desktops etc.

i guess that line starts the plugins "by force", and the compiz settings manager is totally bypassed. i cant change parameters at all!

the weird thing is that actually the first time i installed xgl/compiz, the situation was a bit different. i don't remembered how i set it, but a) compiz started like normally b) there is NO compiz item in "gconf-editor" c)i can change settings in csm.

actually i think all of these weird stuff have something to do with my hardware. i have 9600pro, asus K8N (nf3 chipset), which gave a terribly hard time setting up correctly. i just found that for the ati driver to work, one has to DOWNGRADE bios to 1006 otherwise it wont work. what the xxxx? i have no idea how this issue relates to the gconf-editor/compiz thing, but i highly dout it...

---

