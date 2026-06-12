---
title: "Cant edit xorg.conf file."
date: 2005-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by sman88 on 2005-10-19
Guys I need help quick, I cant edit the xorg.conf file and I have to to setup twinview on my laptop (I think, If im wong let me know!) and I have to have it working by tomarow because I have a presentation to give for school, 250pts! I really need help FAST!    PLEASE!!!!!!

---

### Post by claydoh on 2005-10-19
You need to use sudo to edit it with write privileges. Open a terminal, and type in

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by dbott67 on 2005-10-19
```
 gksudo gedit /etc/X11/xorg.conf
```

-Dave

---

### Post by dbott67 on 2005-10-19
[QUOTE=claydoh]You need to use sudo to edit it with write privileges. Open a terminal, and type in

```
sudo gedit /etc/X11/xorg.conf
```[/QUOTE]

Jinx... you owe me a Coke! :)

---

### Post by claydoh on 2005-10-19
heh, will you take a Diet Cherry Vanilla Dr. Pepper?
:p

---

### Post by sman88 on 2005-10-20
I dont have write privlages, and I cant login as root so how to I give myself write privliages, unless someone can tell me how to log in as root.

---

### Post by rjwood on 2005-10-20
[quote=sman88]I dont have write privlages, and I cant login as root so how to I give myself write privliages, unless someone can tell me how to log in as root.[/quote]
using sudo gives you root privlages temporarally.  sudo does not work??

---

### Post by dbott67 on 2005-10-20
[QUOTE=sman88]I dont have write privlages, and I cant login as root so how to I give myself write privliages, unless someone can tell me how to log in as root.[/QUOTE]

In Ubuntu, the root account does not have a password, so you can't login using this account (it's by design).  The first account created during installation becomes a member of the 'admin' group and can gain 'root' privileges by typing in 'sudo' (or 'gksudo' for the graphical version) in front of the command.  So by typing the following command in a terminal window:
```
gksudo gedit /etc/X11/xorg.conf
``` 
you're telling the OS to 'super-user' do the command.  In this case, it's use the application 'gedit' to open the file 'xorg.conf'.

You'll be prompted to enter YOUR password.  If this doesn't work, you may not be part of the 'admin' group.

So, the questions I would have for you are this:
1. Did you install Ubuntu or did someone else?
2. If you did it, what was the first account that you created during installation?  This account can use 'sudo'; any secondary accounts that are created do not have the ability to run sudo (unless explicity assigned to the 'admin' group).
3. If it was someone else, either you need to use the first account or have them add your user account to the 'admin' group.

-Dave

---

### Post by dbott67 on 2005-10-20
The other thing I just thought of is to check ownership & permissions of the xorg.conf file.

1. Using Nautilus, browse to the /etc/X11 directory.
2. Right-click the xorg.conf file & select PROPERTIES.
3. Click on the PERMISSIONS tab.
4. The owner & group should both be root.
5. The permissions should be 644 (number view).

If you have something different, let us know.

-Dave

---

### Post by dbott67 on 2005-10-20
[QUOTE=claydoh]heh, will you take a Diet Cherry Vanilla Dr. Pepper?
:p[/QUOTE]

Sure.  Cheers *clink*.  Thanks for the cold one! :)

-Dave

---

### Post by claydoh on 2005-10-20
[quote=claydoh]You need to use sudo to edit it with write privileges. Open a terminal, and type in

```
sudo gedit /etc/X11/xorg.conf
```[/quote]

Stupid me! I am sorry, I definitely should have specified what 'sudo' is :(

---

### Post by sman88 on 2005-10-20
Well I did the sudo thing and it worked, also the properties of the file are set to 644 or whatever you said. But when I edited it and did a reboot, It came up with a blue screen and said x server was not setup correctly and to do a restart when it is. Luckly I had my 250 point project on a cd, so I did a reinstall (didnt know what else to do) and did my project off of a 15.4 in widescreen display, nobody could see, but I did get the full points because most people had never herd of linux before (thats what the project was on) and it intrieged them so that was kool. But my monitor out still doesnt work, it works but its all scrambled and is wayy screwed up, so what do I do to get my vga out on my laptop to work. BTW its a compaq r3000z with a nvidia geforce 4 420 go.

Thanks all for your post and being descriptive on what different things are, Im still learning. THANK YOU!

---

