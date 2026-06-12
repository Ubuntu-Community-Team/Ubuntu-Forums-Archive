---
title: "Terminal problem, pls help"
date: 2008-09-12
forum: x86 64-bit Users
---

### Post by skozzy on 2008-09-12
I have been using Ubuntu x86 desktop for ages, tonight I reinstalled the 64bit AMD desktop and find I can't get a program running I had before.

I was using HandBrakeCLI from a terminal window to convert some dvd's to avi's, the path where I have HandBrakeCLI saved is /home/skozzy/Desktop/

On the 32bit disktop I could just type /home/skozzy/Desktop/HandBrakeCLI --help to display the help for it. But if I do the same on this 64bit OS I always get a reply saying "Command no Found"

What I am doing wrong or is there something different to do in this 64bit version.

The file permitions are correct I believe.

Here is the result from LS -L

> skozzy@skozzy-desktop:~$ ls -l /home/skozzy/Desktop
total 6524
-rwxr-xr-x 1 skozzy skozzy 6667911 2008-02-20 04:51 HandBrakeCLI


So, should I just type /home/skozzy/Desktop/HandBrakeCLI to run it ?

---

### Post by jerome1232 on 2008-09-12
Well I am running x86_64 Hardy, I just downloaded the i386 binary from their site [http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

Extracted it and ran and it appears to work just fine, I don't have anything to test it on though. The first command is just to show I'm on 64 bit

```
jeremy@lifebane:~$ uname -m
x86_64   
jeremy@lifebane:~$ mv Desktop/HandBrake-0.9.2_i386.tar.gz ~/
jeremy@lifebane:~$ ls
Desktop    Examples                     Music     Public     torrents
Documents  HandBrake-0.9.2_i386.tar.gz  Pictures  Templates  Videos
jeremy@lifebane:~$ mkdir handbrake
jeremy@lifebane:~$ tar xzf HandBrake-0.9.2_i386.tar.gz -C handbrake/
jeremy@lifebane:~$ cd handbrake/
jeremy@lifebane:~/handbrake$ ls
HandBrakeCLI
jeremy@lifebane:~/handbrake$ ./HandBrakeCLI 
Missing input device. Run ./HandBrakeCLI --help for syntax.
jeremy@lifebane:~/handbrake$ ./HandBrakeCLI --help
Syntax: HandBrakeCLI [options] -i <device> -o <file>

.... and lots of help text after that
```

---

### Post by skozzy on 2008-09-12
Im running a bunch of OS updates at the moment, I will see if that changes anything.

I can see the files with I list the folder, but I just can't run it. It's got me beat for now.

> skozzy@skozzy-desktop:~$ ls -l /home/skozzy/Desktop
total 6524
-rwxr-xr-x 1 skozzy skozzy 6667911 2008-02-20 04:51 HandBrakeCLI
skozzy@skozzy-desktop:~$ 
skozzy@skozzy-desktop:~$ 
skozzy@skozzy-desktop:~$ /home/skozzy/Desktop/HandBrakeCLI --help
bash: /home/skozzy/Desktop/HandBrakeCLI: No such file or directory
skozzy@skozzy-desktop:~$ 
skozzy@skozzy-desktop:~$ 
skozzy@skozzy-desktop:~$ 



---

### Post by jerome1232 on 2008-09-12
nifty I keep looking at it for a spelling mistake but just can't see one, try it like this just to try it

```
touch ~/Desktop/HandBrakeCLI
~/Desktop/HandBrakeCLI --help
```

Maybe try simply re-downloading extracting it, and running the new executable.

---

### Post by skozzy on 2008-09-12
No luck, all the updates (320mb of them) finished installing and I rebooted, just to make sure, result is :

> skozzy@skozzy-desktop:~$ touch ~/Desktop/HandBrakeCLI
skozzy@skozzy-desktop:~$ ~/Desktop/HandBrakeCLI --help
bash: /home/skozzy/Desktop/HandBrakeCLI: No such file or directory
skozzy@skozzy-desktop:~$ 



---

### Post by skozzy on 2008-09-12
I have a copy in 2 places now, /home/skozzy and /home/skozzy/Desktop and both say it cant be found.. this is nuts :confused:

---

### Post by jerome1232 on 2008-09-12
Try typing ~/Des now hit tab, then hit tab again.

I'm assuming you have two copies because you downloaded the binary from their website and that one won't work now?

---

### Post by skozzy on 2008-09-12
I typed that and got pages and pages of commands.

---

### Post by skozzy on 2008-09-12
I bailed out of the 64bit OS and installed the 32bit one on another drive so I can keep going with my rips. But I do still have the 64bit install to try tackle the problem when I get more help on the issue from anyone.

---

### Post by Yellow Pasque on 2008-09-12
What does this command return?
```
file ~/Desktop/HandBrakeCLI
```

---

### Post by jormabe1 on 2008-09-12
support good article.where wholesale and retail cheaper wedding dresses?i recomend a wedding dress factory to everybody,jorma wedding dresses factory is professional wedding gowns factory in china. Have more 240 wholesalers in the world, Have able to offer wedding dress, [bridesmaid dresses](http://www.jormabridal.com/gown.html), [bridal gowns](http://www.jormabridal.com/wedding_dress.html), [prom dresses](http://www.jormabridal.com/Prom_dress.html), mother of bride dresses and [flower girl dresses](http://www.jormabridal.com/flower_girl.html) for the bridal industry.No extra cost for [plus size wedding dresses](http://www.jormabridal.com/plus_size.html)if you think our informaiton not good, please cancel it.thanks for your support.

---

### Post by skozzy on 2008-09-14
The result I got was this :

> skozzy@skozzy-desktop:~$ file /home/skozzy/Desktop/HandBrakeCLI
/home/skozzy/Desktop/HandBrakeCLI: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), not stripped


---

### Post by Yellow Pasque on 2008-09-14
It might be better to build from source (a 64-bit version should rip noticeably faster since we're talking video de/encoding here). I'm building it in the background as I type. I'll let you know how it turns out. I may try and make a .deb out of it if I can too.

EDIT: It's done and it works well.
```
dan@harvest:~/HandBrake$ file HandBrakeCLI 
HandBrakeCLI: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), not stripped
```

Also, if you want the file to be executable in the terminal, you'll have to use ./ or copy the HandBrakeCLI file to /usr/bin

---

### Post by skozzy on 2008-09-15
Well I have tried all morning to compile the source, tried every way I saw in the HandBrake forums, none worked for me, always something missing.

So, I will purhaps leave this as unsolved and move back to the 32bit OS.

I would like to thank you all for the help.

---

