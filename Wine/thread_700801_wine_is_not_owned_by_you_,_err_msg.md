---
title: "wine is not owned by you , err msg"
date: 2008-02-18
forum: Wine
---

### Post by ronio on 2008-02-18
I installed the latest WINE via the package manager.
I have a Windows game installed.  
I placed it at  /usr/share/apps/EASports/

However, when I try to execute the game, I get the following message:

wine: /home/ron/.wine is not owned by you

i searched the forum, however, i must be the only loser that can't even get wine to fire up :)

---

### Post by Ferrat on 2008-02-19
sounds like you started up wine with a sudo, this makes the .wine folder a root owned folder = no good

open a terminal 
type in 
```

sudo nautilus 

```

got to /home/ron

press Ctrl + H (this will show hidden files and folders)

find the folder .wine 

remove it 

close down the filebrowser

in the terminal now type 

```

winecfg

```

only that, nothing else and the wine cfg should start after building you a new .wine dir :)

---

### Post by Sukarn on 2008-02-19
You could do the above, or you could type this in the terminal -
```

sudo chown -R ron:ron ~/.wine

```
The above command will change the ownership of the .wine folder to the user "ron" and group "ron"

---

### Post by Alex14 on 2009-12-24
hi, im pretty new to ubuntu and wine and have the same problem with wine telling me that i do not own /home/alexander/.wine.
i tried both ways posted above, but none of them worked. when i tried the sudo chown -R alexander:alexander ~/.wine nothing happend at all. it wrote what i just typed in and that was it. please help me i have used hours on this problem!

---

### Post by Sathallrin on 2009-12-24
@Alex: can you post the output of
ls -al ~ | grep wine
That will show the current permissions of the .wine folder

---

### Post by Drastic2010 on 2010-05-21
Kind of an old topic i see, but i am having this issue now too.  Here is the output for 
ls -al ~ | grep wine

```
drwxr-xr-x  4 cjoyner cjoyner    4096 2010-05-21 14:30 .wine
drwxr-xr-x  3 cjoyner cjoyner    4096 2010-05-08 01:17 .winetrickscache
```

Thanks and hopefully can resolve this issue.

---

### Post by Sukarn on 2010-05-23
> **Drastic2010 said:**
> Kind of an old topic i see, but i am having this issue now too.  Here is the output for 
ls -al ~ | grep wine

```
drwxr-xr-x  4 cjoyner cjoyner    4096 2010-05-21 14:30 .wine
drwxr-xr-x  3 cjoyner cjoyner    4096 2010-05-08 01:17 .winetrickscache
```

Thanks and hopefully can resolve this issue.

Hey Drastic2010,

Just to make sure that the permissions are set correctly, I would ask you to run the command I mentioned above once on your own computer.

I am assuming that your username is cjoyner, so, based on that, this is the command you would have to type -

```
sudo chown -R cjoyner:cjoyner ~/.wine
```

Try running it once and then check whether that fixes it for you.

---

### Post by zelrikriando on 2011-03-29
I am having the same issue also, none of the above works, the only way to have access to .wine for me is to do it as su.

---

### Post by cwwilson721 on 2011-03-29
> **zelrikriando said:**
> I am having the same issue also, none of the above works, [COLOR="Red"]the only way to have access to .wine for me is to do it as su.[/COLOR]
I'll bet that 90% of the above issues were caused by the posters RUNNING WINE AT SOME POINT AS SU.

Don't do it.

[SIZE="6"][COLOR="Navy"]***_Never run wine as the super-user!_***[/COLOR][/SIZE]


You are as vulnerable as a typical Windows user. Security, file permissions, folder permissions, executing files w/root permissions, virus/malware (Yes, wine can run BAD JUJU stuff as SU, and since 99% of users NEVER remove "non-windows" drives in winecfg, that exposes your ENTIRE system to the woes of MS Windows virus/malware. Since you are running as su, EVERY FILE ON YOUR COMPUTER IS AT RISK.)

Don't do it.

[SIZE="6"]EVER[/SIZE]

---

### Post by matuskap on 2011-07-10
Well now i have the same problem and it started just after upgrade to 10.10. I guess im going to remove and install it again to avoid any problems... to be honest, there enough pure-wine crap to be fixed while trying to run games without having to deal with this kind of stuff.

---

