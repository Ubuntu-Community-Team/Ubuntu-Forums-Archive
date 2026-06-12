---
title: "cannot execute sudo commands"
date: 2006-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by webbcm01 on 2006-05-14
im trying to reconfigure xorg using the line:

     sudo dpkg-reconfigure xserver-xorg

my screen looks like this:

root@ubuntu1:~# sudo dpkg-reconfigure xserver-xorg
sudo: unable to lookup ubuntu1 via gethostbyname()
root@ubuntu1:~# sudo apt-get install nvidia-kernal-common nvidia-glx
sudo: unable to lookup ubuntu1 via gethostbyname()

what is wrong i am very new to linux and would appreciate some help here

---

### Post by gslo on 2006-05-14
webbcm01
try using su instead of sudo.

---

### Post by ceverett on 2006-05-15
hey,you must be new to linux too.  Ubuntu doesn't assign a root password.
So you can't su unless you can sudo.

---

### Post by Sutekh on 2006-05-27
Have you made any changes to network configurations or other system configs? 

Can post #3 in this thread help you out?

[http://ubuntuforums.org/showthread.php?t=181102]("http://ubuntuforums.org/showthread.php?t=181102")

---

### Post by Drain on 2006-05-28
[QUOTE=webbcm01]
root@ubuntu1:~# sudo dpkg-reconfigure xserver-xorg
sudo: unable to lookup ubuntu1 via gethostbyname()
[/QUOTE]

Well, just looking at what you posted - I have two thoughts: First, it appears that you're already root. (username is "root", and the prompt is a "#" instead of a "$").  So do you really need to use sudo at that point?

Second, that error message might tell you something - Googling around led me to find that a number of people have had a similar error message after they changed their hostname, so you might want to check the file at /etc/hosts to see what it looks like.  I'm guessing the first line should look like this:
```

127.0.0.1       localhost.localdomain   localhost       hostname
```

(where "hostname" in your case should be "ubuntu1").

---

