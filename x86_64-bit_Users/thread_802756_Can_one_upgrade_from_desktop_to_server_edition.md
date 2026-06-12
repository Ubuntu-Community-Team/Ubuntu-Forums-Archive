---
title: "Can one upgrade from desktop to server edition?"
date: 2008-05-21
forum: x86 64-bit Users
---

### Post by VitalBodies on 2008-05-21
Can one upgrade from Ubuntu 64-bit desktop to 64-bit server edition? 
Or does one have to start over with a clean install? 

I was going to add XAMPP and thought I might be bettor off using the server edition.

---

### Post by Kilz on 2008-05-21
> **VitalBodies said:**
> Can one upgrade from Ubuntu 64-bit desktop to 64-bit server edition? 
Or does one have to start over with a clean install? 

I was going to add XAMPP and thought I might be bettor off using the server edition.

Im sure you could make a sever edition from the desktop one. First I would open synaptic and install the linux-image package for the server, reboot into the server kernel and then uninstall the linux-image desktop package, as well as any installed desktop kernels.
Remove the desktop and all the gnome packages. [Here is a page]("https://help.ubuntu.com/community/PureKDE") that shows how to do it to replace it with KDE, just dont install KDE. The Gutsy package list will probably work. Then install your server packages. Be aware that a server install has no GUI.
You might want to install a lightweight desktop [like icewm]("https://help.ubuntu.com/community/IceWM") with the rox filer and gtkedit and use the startx command to start it only when you need it. Thats what I did.

---

### Post by VitalBodies on 2008-05-21
> **Kilz said:**
> Im sure you could make a sever edition from the desktop one. First I would open synaptic and install the linux-image package for the server, reboot into the server kernel and then uninstall the linux-image desktop package, as well as any installed desktop kernels.
Remove the desktop and all the gnome packages. [Here is a page]("https://help.ubuntu.com/community/PureKDE") that shows how to do it to replace it with KDE, just dont install KDE. The Gutsy package list will probably work. Then install your server packages. Be aware that a server install has no GUI.
You might want to install a lightweight desktop [like icewm]("https://help.ubuntu.com/community/IceWM") with the rox filer and gtkedit and use the startx command to start it only when you need it. Thats what I did.

Thank you so much for taking the time to answer. Looking over your answer I begin to wonder if I need the server edition or just web server type applications like Apache, PHP, MySQL etc added to my DE. I was going to add XAMPP but wanted something where the updates come from the Ubuntu community. I like to use LAMP but am not to savvy on maintaining/updating it all. 

Would one be best to use the Server Edition (SE) and add the desktop they like one you suggested or Gnome or KDE or stay in Desktop Edition (DE) and add server stuff. I personally will be creating 3d graphics (Blender) and web documents (XML, XHTML, SVG etc). I will have additional computer for network rendering 3d like a small render farm. Essentially my main computer is my desktop for all my computing so to speak.

---

### Post by jimv on 2008-05-22
There's not a whole lot of difference between the server and desktop versions of Ubuntu.  The server is just the desktop without the GUI.  You can install all of the 'server' packages on the desktop, and all of the 'desktop' packages on the server.  It doesn't matter which you start with.

---

### Post by VitalBodies on 2008-05-22
> **jimv said:**
> There's not a whole lot of difference between the server and desktop versions of Ubuntu.  The server is just the desktop without the GUI.  You can install all of the 'server' packages on the desktop, and all of the 'desktop' packages on the server.  It doesn't matter which you start with.

So how would one go about doing that? In add/remove what would you choose or does it not work that way?

---

### Post by cariboo on 2008-05-23
Check out his Link:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")

To see what is involved. Ignore the install from CD instructions and have a look at the rest.

Jim

---

### Post by Kilz on 2008-05-23
> **VitalBodies said:**
> So how would one go about doing that? In add/remove what would you choose or does it not work that way?

One word of caution, the reason the server edition doesnt have a desktop is the amount of resources the Gnome, KDE and Xfce (the 3 main desktops for Ubuntu) use. If this server is going to be under a load, you may want to think about doing the server over, or at the least use xubuntu as a base if you find you dont want to install icewm to a server install. Xfce eats the least of the 3. If this is going to be a true server, you will not need a fancy desktop with effects and such gobbling up ram and other resources as they will not be used as its serving files.

---

### Post by wigglydiggly on 2008-05-23
> **jimv said:**
> There's not a whole lot of difference between the server and desktop versions of Ubuntu.  The server is just the desktop without the GUI.  You can install all of the 'server' packages on the desktop, and all of the 'desktop' packages on the server.  It doesn't matter which you start with.
I always thought the server edition used different kernals, ones that didn't focus on multimedia features built into CPUs instead focused on read/write functions.

I'm probably wrong in my thinking, just thought I'd ask.

---

### Post by EndPerform on 2008-05-23
> **VitalBodies said:**
> Can one upgrade from Ubuntu 64-bit desktop to 64-bit server edition? 
Or does one have to start over with a clean install? 

I was going to add XAMPP and thought I might be bettor off using the server edition.

There are a lot of good ideas in this thread.  I'll tell you what I did on my machine.  I started with the Desktop addition and added PHP, mysql and Apache.  If you're doing something where it's going to be under a small load, this should be fine.  If you're looking to turn your machine into a dedicated server, perhaps a fresh install with something more lightweight (Fluxbox, XFCE, etc as mentioned before) would work.  I haven't had a problem so far.

---

### Post by VitalBodies on 2008-05-23
The server I need will have no real load at all. I use a server to build web sites and web page for testing/preview. Thus I will create a page or page fragment, load the page, edit for a while reload to see the results. I am using mostly SSI but I am considering moving towards PHP. 

If you want an easy (for installing) solution consider XAMPP. This is a great and easy user friendly way to load/install Apache, PHP, MySQL, Filezilla, Mercury mail and the like. 
But...
You have to maintain this your self to some degree meaning the Ubuntu community does not maintain this so there are not automatic updates. 
Much easier than load all that one program at a time.

My situation is that I use this stuff (Apache, PHP, MySQL) so little I never really learn it. It is like a hard drive, I just need to use it and not think about it much so I am looking for EASY so I can focus on art and being creative. I just need my page to load off line so I can see it.

---

