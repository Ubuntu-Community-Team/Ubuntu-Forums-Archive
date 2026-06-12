---
title: "Will the server be getting any GUI at all?"
date: 2008-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by jaime256 on 2008-03-03
Okay, before everyone starts flaming I have read a lot of the why you wouldn't want that and on and on. I had to ask, because I like to look at nice things and I just find the OS pretty good, so hey, there's nothing wrong with adding a bit of GUI. I installed the 64-bit server briefly to test it and tried adding the desktop stuff, but it didn't work.I read other post with other stuff, but wasn't able to get that going. I don't have that installed any more, but I was wondering about this part anyway. Thanks.

---

### Post by brent113 on 2008-03-03
The server has a GUI! It's just not packaged on the installer disk by default.  To install it type ```
sudo apt-get install ubuntu-desktop
```

---

### Post by Kilz on 2008-03-03
> **jaime256 said:**
> Okay, before everyone starts flaming I have read a lot of the why you wouldn't want that and on and on. I had to ask, because I like to look at nice things and I just find the OS pretty good, so hey, there's nothing wrong with adding a bit of GUI. I installed the 64-bit server briefly to test it and tried adding the desktop stuff, but it didn't work.I read other post with other stuff, but wasn't able to get that going. I don't have that installed any more, but I was wondering about this part anyway. Thanks.

Servers dont need a gui. People who suggest installing the Ubuntu desktop really dont understand why it isnt a good idea. It is a huge waste of resources for a server. A servers job is to serve data. Not edit documents with open office (installed with the ubuntu desktop) . Not to read email with Evolution (installed with the ubuntu desktop)  or browse the internet with Firefox (installed with the ubuntu desktop). Not to mention the ram the desktop, the hal and a dozen other damens that the deskop loads eats.
You look at desktop computers, you shouldnt be looking at a server, it should be serving data to other desktop computers. Some people dont even attach monitors to servers. They instead access the server with [webmin]("http://www.webmin.com/").
If you must have a gui then at least think about [a low memory]("https://help.ubuntu.com/community/Installation/LowMemorySystems") option like icewm or fluxbox. Start the gui with startx, and logout of it when you are not using it.

---

### Post by kaivalagi on 2008-03-04
If you really do want a windows manager on a server then I think you need to be installing a very minimal one. You really want to install from the bottom up, so you don't get bloat. And as Kilz says don't have it start by default, and shutdown X when you're done.

Have a look around for lightweight wm's, I suggest something like qwm, openbox, icewm etc

---

### Post by igknighted on 2008-03-04
The true "GUI" for a server is a web interface, such as Webmin or PHPMyAdmin (among others... it depends what servers you are running).  Apache servers out a page that you log in securely to that lets you control whatever it is that needs control (users/groups, web pages, etc.) through a pleasing GUI, without the xserver overhead.

If you install "ubuntu-desktop", or even fluxbox, you aren't going to have any GUI tools available to manage the server, so what's the point?  You could pull up firefox and log into webmin via localhost, but that is just as easily done from another computer without burdening the server.  Same with PHPMyAdmin and others.  Even for doing server work on a terminal such as gnome-terminal instead of the flat black background, why not sit at a desktop computer and use SSH to accomplish the same thing, again without wasting server resources to run an xserver.

I understand the frustration.  Managing a server using CLI commands can be tedious and difficult to new users.  But an xserver doesn't even begin to solve any problems, and it creates more.  A good web-based admin tool is the way to go, along with a friendlier installer (see opensuse/sles and fedora/rhel/centos) that can run a GUI to make sure that the proper servers get installed and the network configured properly.

---

### Post by johnnybirdman on 2008-03-04
> **jaime256 said:**
> Okay, before everyone starts flaming I have read a lot of the why you wouldn't want that and on and on. I had to ask, because I like to look at nice things and I just find the OS pretty good, so hey, there's nothing wrong with adding a bit of GUI. I installed the 64-bit server briefly to test it and tried adding the desktop stuff, but it didn't work.I read other post with other stuff, but wasn't able to get that going. I don't have that installed any more, but I was wondering about this part anyway. Thanks.

[http://www.webmin.com/](http://www.webmin.com/)
so simple and easy for use with servers. I have used with 32 and 64-bit.  can be up and running in less than 5 min.

---

### Post by jaime256 on 2008-03-05
Thanks for the info. I like trying out different things, So if there are other programs or options I like to hear them too. I have tried the webmin, and I am liking the option to set something smaller and just activate it when I'm on it. Maybe be I'll do headless server that way, but right now I just want to know what you guys have used and what other programs there are. Some I hadn't heard of so this is great, Keep them coming. Also, what's that program qwm? I couldn't find that anywhere. So far I got...

Ubuntu-Desktop
Webmin
PhpAdmin
qwm
Openbox
Icewm
Fluxbox

---

### Post by kaivalagi on 2008-03-05
I was going on memory, but it looks like qwm has been abandoned...

Take a look at [http://xwinman.org/index.php]("http://xwinman.org/index.php") for details on some of the less used more lightweight window managers out there. If you're running python on the server PyWM looks like something worth considering?

All I was trying to get at was that there are some extremely lightweight window managers which might cover off what you need on a server, and won't drain resources.

Happy hunting :)

---

