---
title: "Kubuntu AMD 64 and XGL - Can it work?"
date: 2006-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Princey on 2006-06-19
I've been reading around and seeing screen shots of XGL. Lots of references point to the graphics cards, success stories, problems etc. However, even according to [this thread ]("https://wiki.ubuntu.com/CompositeManager/Xgl") mention is made specifically to Ubuntu and to two types of ATI Radeon cards, namely the "Mobility Radeon 9700 SE" and "Radeon X300" as the supported hardware under ATI. 

I mention ATI as I have an ATI X600 Graphics card running on my AMD 64 X2 3800+ machine. The question is, is it possible at all to install and run XGL on my machine?

---

### Post by Kilz on 2006-06-19
[QUOTE=Princey]I've been reading around and seeing screen shots of XGL. Lots of references point to the graphics cards, success stories, problems etc. However, even according to [this thread ]("https://wiki.ubuntu.com/CompositeManager/Xgl") mention is made specifically to Ubuntu and to two types of ATI Radeon cards, namely the "Mobility Radeon 9700 SE" and "Radeon X300" as the supported hardware under ATI. 

I mention ATI as I have an ATI X600 Graphics card running on my AMD 64 X2 3800+ machine. The question is, is it possible at all to install and run XGL on my machine?[/QUOTE]
Gentoo has a [list of hardware]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL") they have gotten Xgl to run on. The ATI x600 is listed as being able to run Xgl, but there were problems with an older driver. I dont think the main prossessor makes any diffrence, there are 64 bit packages available.
Id say give it a try, but be prepared for it not to work. Even if it dose , you may change your mind. I had it running on an x200 and it was ok, but after awhile it was distracting. I also didnt like the 1 window border theme that all Xgl setups have to use, and most opengl programs dont work right with it enabled.

---

### Post by Princey on 2006-06-19
[QUOTE=Kilz]Gentoo has a [list of hardware]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL") they have gotten Xgl to run on. The ATI x600 is listed as being able to run Xgl, but there were problems with an older driver. I dont think the main prossessor makes any diffrence, there are 64 bit packages available.
Id say give it a try, but be prepared for it not to work. Even if it dose , you may change your mind. I had it running on an x200 and it was ok, but after awhile it was distracting. I also didnt like the 1 window border theme that all Xgl setups have to use, and most opengl programs dont work right with it enabled.[/QUOTE]

Thanks Kilz, I'll give it a try tomorrow. If I don't like it, I can always remove it. Just want to see what it looks and feels like.

---

### Post by Kilz on 2006-06-19
[QUOTE=Princey]Thanks Kilz, I'll give it a try tomorrow. If I don't like it, I can always remove it. Just want to see what it looks and feels like.[/QUOTE]
Thats why I tried it myself, just to see what it was like. To sum up my experence, it was gnome with wobbly windows. Though the cube workspace changer was kind of cool.

---

### Post by Princey on 2006-06-20
[QUOTE=Kilz]Thats why I tried it myself, just to see what it was like. To sum up my experence, it was gnome with wobbly windows. Though the cube workspace changer was kind of cool.[/QUOTE]

I'll be sure to post my experiences when I give it a go later. Let's see if it will be KDE and wobbly windows or something entirely different.8-)

---

### Post by Princey on 2006-06-20
Update:

Not sure if I can say I had a successful install. Went through the howto step by step without error. However, when it comes to logging out of my regular session to test the xgl session, I just get a blank desktop...no icons, no menu, nothing. Only thing I can do is press CTRL + ALT + BACKSPACE to log into my regular session. Didn't go on to the compiz section as I'm not sure what would happen seeing the testing stage yielded a blank desktop.

Truth be told, if I type in ```
glxgears
``` I now see the 3D gears spinning. Am I missing something or what?

---

### Post by Kilz on 2006-06-20
[QUOTE=Princey]Update:

Not sure if I can say I had a successful install. Went through the howto step by step without error. However, when it comes to logging out of my regular session to test the xgl session, I just get a blank desktop...no icons, no menu, nothing. Only thing I can do is press CTRL + ALT + BACKSPACE to log into my regular session. Didn't go on to the compiz section as I'm not sure what would happen seeing the testing stage yielded a blank desktop.

Truth be told, if I type in ```
glxgears
``` I now see the 3D gears spinning. Am I missing something or what?[/QUOTE]
Well it looks like you have acceleration setup, if you see the gears. maybe you need to do something for kde to use it.

---

### Post by rutger83 on 2006-07-01
Same thing here. Just to note: I have a dual boot also to the i386 version of dapper on this system. There compiz/xgl work fine! :-?

---

### Post by Princey on 2006-07-02
[QUOTE=Kilz]Well it looks like you have acceleration setup, if you see the gears. maybe you need to do something for kde to use it.[/QUOTE]


I gave up for a few days then went back at it. Maybe I'm wrong but all posts I've read so far indicate that I must have XGL running properly before compiz can be installed. I still can't get it to run save well, I have 3D acceleration. I'm wondering if anyone using Kubuntu has had any bit of success running it could offer some bit of advice. As I stated earlier, installing it didn't give me any error messages. Installed fine and even after successful reboots, I still can't log into the XGL session. I'm currently using the ati drivers. Anyone out there got theirs running on Kubuntu?

---

### Post by Princey on 2006-08-11
OK. After leaving compiz/xgl for a while, I finally got back at it for another try after seeing much ado about it on GL-TV. I followed the howto from the [compiz forums]("http://www.compiz.net/viewtopic.php?id=205") and all tests so far come back positive. However, there are a few shortcomings. Because it uses gdm to load compiz/xgl I get an error message about a theme missing an xml component. If I click ok, cancel the login screen, I get a normal login and I log in with no problems. I tried installing xwinwrap and got package couldn't be found. I have all my repos enabled. Does anyone know how can I get it installed, i.e. which repository carries that file?

---

### Post by Mooie on 2006-08-11
It might just be a gnome theme that you need, so if you dont have it installed you might want to install the ubuntu-desktop package in synaptic, this would also let you boot into gnome if you wanted too.  I'm not quite sure it would help, but unless you dont want gnome on your box its worth a try...   unless sombody doesnt think it would work :???:

---

### Post by Princey on 2006-08-12
> **Mooie said:**
> It might just be a gnome theme that you need, so if you dont have it installed you might want to install the ubuntu-desktop package in synaptic, this would also let you boot into gnome if you wanted too.  I'm not quite sure it would help, but unless you dont want gnome on your box its worth a try...   unless sombody doesnt think it would work :???:

I think it is. However, it's not so much of an issue. I don't want to install gnome. If I wanted, I'd just have installed ubuntu instead of kubuntu. The actual message reads > Can't load Human theme
/usr/share/gdm/themes/Human/Human.xml can't be found

I think I'll try reinstalling gdm to see what happens.

---

### Post by infinitepi on 2006-08-13
i also am having trouble installing xwinwrap on my amd 64, getting a package not found... i was thinking maybe the the file was moved?

---

### Post by Princey on 2006-08-14
> **infinitepi said:**
> i also am having trouble installing xwinwrap on my amd 64, getting a package not found... i was thinking maybe the the file was moved?

I still haven't got mine working or found how to install it. I'm currently searching via google to see what I come up with. I'll keep you posted. Please let me know if you found anything as well.

---

