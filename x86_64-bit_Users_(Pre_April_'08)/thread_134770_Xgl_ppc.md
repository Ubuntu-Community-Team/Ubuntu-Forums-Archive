---
title: "Xgl ppc"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by T31 on 2006-02-22
I have being reading the post "xgl success stories" and I saw few ppc users posts, but what Im curious after reading some staff saying Xgl works better on propietary drivers and bla bla

Hey guys someone with a working Xgl desktop on mac hardware?

:-k :-D \\:D/

---

### Post by Ptero-4 on 2006-02-23
Can Xgl work on a 8mb ATI Rage mobility?

---

### Post by T31 on 2006-02-24
As far as I have seen there is people making it work on a Geforce 3 or even Geforce 2 some effects but I dont know how an ATI 8mb can do :-|

---

### Post by ssam on 2006-02-24
[http://en.opensuse.org/Using_Xgl_on_SUSE_Linux](http://en.opensuse.org/Using_Xgl_on_SUSE_Linux) lists which drivers work and which have problems.

on nvidia you need the propietry drivers (the nvidia opensource drivers are bad).

on older ATIs the opensource driver is very good, and work better than the propietry drivers for xgl.

i have got xgl running fairly well on a 1ghz powerbook with a ati radeon 9000 mobility. there are a few display corruption issues though, and it does not wake from sleep in a good mood.

---

### Post by spaceballl on 2006-02-24
ooooh good to hear! That means there is hope for XGL on my iBook w/ 9200!

---

### Post by callipeo on 2006-02-26
I have an iBook G4 with a radeon mobility 9200 and I must admit than Xgl performances are not very good. In particular, moving windows with dynamic contents (be it a video or simply an instance of htop) lead to noticeable slowness (not to mention to place them on the cube vertex...). It seems to work fine with "static" windows instead.

---

### Post by moijbt on 2006-03-02
Hi !
Does anybody know if there is a ppc driver for the Radeon 9550 in Dapper ? And, if yes, does it works with Xgl ?

---

### Post by eidex on 2006-03-02
Hi, i am trying to run XGL on a g4 1,2 GHZ iBook, I have posted my results here in the XGL PPC Dapper thread: [http://www.ubuntuforums.org/showthread.php?t=136015](http://www.ubuntuforums.org/showthread.php?t=136015)

Callipeo, you seem to have the same iBook revision, what did you do different?

---

### Post by callipeo on 2006-03-02
[QUOTE=eidex]Hi, i am trying to run XGL on a g4 1,2 GHZ iBook, I have posted my results here in the XGL PPC Dapper thread: [http://www.ubuntuforums.org/showthread.php?t=136015](http://www.ubuntuforums.org/showthread.php?t=136015)

Callipeo, you seem to have the same iBook revision, what did you do different?[/QUOTE]

Well, excluding the lack of window manager, I have similar problems. I tried different solutions, including manual launching Xgl on a different display, and I always got the basic functionality (including the window manager). In any case, the instructions of the first post in the thread you linked works for me. BTW maybe the reason for the slowness is related to [http://en.opensuse.org/Using_Xgl_on_SUSE_Linux#ATI.2FOpen_source_driver_.22radeon.22](http://en.opensuse.org/Using_Xgl_on_SUSE_Linux#ATI.2FOpen_source_driver_.22radeon.22)

---

### Post by Entity on 2006-03-15
On my 17" Powerbook G4 with radeon 9600 I get a white screen on GDM restart and I need to reboot cause I'm stocked there.

Any similar experiences?

---

### Post by Baggypants on 2006-03-17
Me Too, 

I'm assuming its due to the fairly new opensource R300 driver in Xorg which works great for some things and not for others, FooBilliard works fine, for example. Torcs you end up with 4 disembodied wheels flying in the air, very disconcerting. Also it crashes on particle based stuff.

As to the guy who said the propriety driver runs quicker than the open source one, he's right....... for x86,  I just put him down as some incompetant who didn't read the post fully. or believes x86 == theworld :-D

(the bcm43xx drivers get much the same treatment "Use Ndiswrapper! Use Ndiswrapper!" dolts, sorry I'm wandering off topic into a flame:mrgreen: )

---

### Post by plush on 2006-04-22
How can PPC people make this work???  There's no proprietary nVidia driver!  Someone help, I'd like to get this to work too... I have a GeForce 6800GT on my G5.

---

