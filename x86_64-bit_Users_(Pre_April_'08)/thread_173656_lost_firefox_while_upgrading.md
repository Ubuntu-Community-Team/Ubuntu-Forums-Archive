---
title: "lost firefox while upgrading?"
date: 2006-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by imacQ on 2006-05-10
"no such file or directory," is what it says when i try to get online. 

i tried to use ssams build of firefox (see post) [http://www.ubuntuforums.org/showthread.php?t=128045&highlight=firefox](http://www.ubuntuforums.org/showthread.php?t=128045&highlight=firefox) 

used [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) to guide me along as suggested, but there's something i've screwed up, or not done? anyway i figured what the hey... go ahead and upgrade to dapper and then maybe i'll have firefox back. NOT! have tried reinstalling it without success. still get same "no such file or directory." i hope someone can tell me what to try? i guess i could reinstall ubuntu and start over, but oh my... lions and tigers and bears :confused:

---

### Post by cyracks on 2006-05-10
After upgrading to dapper did you try to install it with synaptic or from source.

---

### Post by imacQ on 2006-05-10
tried to install via synaptic

---

### Post by cyracks on 2006-05-10
in console/terminal write 

$whereis firefox
$cd /usr/bin/
$ls -l|grep firefox

and send the output

---

### Post by imacQ on 2006-05-10
firefox: /usr/bin/firefox.ubuntu /etc/firefox usr/lib/firefox usr/bin/X11/firefox.ubuntu /usr/share/man/man1/firefox.1gz  

what?

---

### Post by imacQ on 2006-05-10
lrwxrwrwx 1 root root 22 2006-05-08 20:46 firefox.ubutu -> ../liv/firefox/firefox

lrwxrwrwx 1 root root 20 2006-05-08 12:33 mozilla-firefox -> /opt/firefox/firefox

lrwxrwrwx 1 root root 22 2006-05-08 20:46 mozilla-firefox.ubuntu -> ../lib/firefox/firefox

i think that's what it says maybe a typo cause typing from other computer. thanks for your help.

---

### Post by cyracks on 2006-05-10
[QUOTE=imacQ]
what?
[/QUOTE]

Don't know what exactly you don't understand ?

This should open firefox, just open terminal and copy and paste line by line, if not send error
```

/usr/bin/firefox
/usr/lib/firefox/firefox

```

To check you realy have firefox installed type
```

dpkg -l|grep firefox

```

To see where firefox is linked
```

ls -l /usr/bin/|grep firefox

```

For example on my computer where I also had firefox 1.5 installed under breezy **ls -l /usr/bin/|grep firefox** gives me:
lrwxrwxrwx 1 root   root         22 2006-05-07 23:37 firefox -> ../lib/firefox/firefox
lrwxrwxrwx 1 root   root         22 2006-05-10 22:42 firefox.ubuntu -> ../lib/firefox/firefox
lrwxrwxrwx 1 root   root         20 2006-03-01 16:04 mozilla-firefox -> /opt/firefox/firefox
lrwxrwxrwx 1 root   root         22 2006-05-10 22:42 mozilla-firefox.ubuntu -> ../lib/firefox/firefox

---

### Post by cyracks on 2006-05-10
[QUOTE=imacQ]
lrwxrwrwx 1 root root 22 2006-05-08 20:46 firefox.ubutu -> ../liv/firefox/firefox
[/QUOTE]

If you misspelled and ../**liv**/firefox/firefox means ../**lib**/firefox/firefox then write in console this:
```

firefox.ubuntu

```

if works then do
```

sudo ln -s /usr/lib/firefox/firefox /usr/bin/firefox

```

and everything should work as it was before :)

---

### Post by imacQ on 2006-05-10
okay! firefox open when i put in /usr/lib/firefox/firefox. THANK YOU :-D . 

i'm here now on my imac. still says "Could not launch application

Details: Failed to execute child process "file:///firefox" (No such file or directory)" when  i try to open from icon. can i fix that? i have my bookmarks and history from old version sitting on my desktop. can i just move/copy them over to other folder?

---

### Post by cyracks on 2006-05-11
[QUOTE=imacQ]
i'm here now on my imac. still says "Could not launch application
[/QUOTE]

That is another computer or the same, but you want to fix the desktop icon ? If the same, do this...
```

sudo ln -s /usr/lib/firefox/firefox /usr/bin/firefox

```
then right click on the desktop icon, select properties->applicaton and just write firefox in the command field.


Don't know which files needs to be copyed to restor old profile, you can just open the old firefox export bookmarks and than import in new firefox. To do this.
[QUOTE=imacQ]
lrwxrwxrwx 1 root root 20 2006-03-01 16:04 mozilla-firefox -> /opt/firefox/firefox
[/QUOTE]
above is location of old firefox, to open it write
```

/opt/firefox/firefox

```
or
```

mozilla-firefox

```

---

