---
title: "Hamachi Install Problem?"
date: 2008-01-10
forum: Wine
---

### Post by stevothewise on 2008-01-10
So I've recently set up Starcraft in Wine, works perfectly, and I thought that I'd get Hamachi so I can still play online (B.Net doesn't work in SC). 

So I dl it and run through the steps of "make install" and "tuncfg". Then i try to finish the configuration by running ./hamachi-init. Doesn't do anything as in generates no output at all. ./hamachi start wouldn't work either. 

Is there a specific directory or way I am supposed to do this?

---

### Post by mikedep333 on 2008-01-11
I haven't tried out hamachi on linux, but perhaps you need to use sudo.

---

### Post by stevothewise on 2008-01-12
Tried using sudo, same thing happens.

---

### Post by AquaFox90 on 2008-01-19
Same here

---

### Post by noremac on 2008-01-20
I have been trying to install it today as well, and am getting the same problems.

---

### Post by nutts4life on 2008-01-28
Hi guys,

I'm getting exactly the same issue. I used the steps in this post:

[http://ubuntuforums.org/showthread.php?t=135036](http://ubuntuforums.org/showthread.php?t=135036)

I'm using 7.10 ubuntu minimal install, with xfce built on top. The make went fine, with no errors.

But when i run hamachi-init nothing happens.

hamachi-init is a actually a link to the hamachi executable.

I'm really keen to get this running.

any ideas?

---

### Post by a10waveracer on 2008-01-29
I was having the same problem and managed to fix it.  This is what I had to do:

[URL="http://logmeinwiki.com/wiki/Hamachi:Install_on_Linux#If_commands_have_no_output"]http://logmeinwiki.com/wiki/Hamachi:Install_on_Linux#If_commands_have_no_output
[/URL]

Follow those instructions of installing the software and then unpacking.  Once I did that to the hamachi executable (with sudo, btw) I was able to successfully get an output. I hope it works for you too!

---

### Post by nutts4life on 2008-02-01
Brilliant, this worked great.

I had to run again:

sudo make install
sudo tuncfg

then 
upx -d ./hamachi (in the /usr/bin directory).

That worked a treat!

O

---

