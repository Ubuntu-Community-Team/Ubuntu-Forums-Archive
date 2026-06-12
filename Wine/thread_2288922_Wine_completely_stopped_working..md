---
title: "Wine completely stopped working."
date: 2015-07-30
forum: Wine
---

### Post by brunomandaloriano on 2015-07-30
Hi, The problem is happening at a PC running Ubuntu 12.04.5 64bit, wine simply stopped working, No updates, nothing.
It was Wine 1.4 I updated to 1.6 without success, deleted the windows folder but it's a global problem it happens with all user of the system. sometimes it pops some messages about wineserver crashing.  No output is given when I run most of the wine components:
```

1:~$ wine /opt/photo3/kids.exe 
:~$ wine /opt/photo3/kids.exe 
:~$ winetricks 
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string
------------------------------------------------------
:~$ wineconsole 
:~$ winecfg 
:~$ wineserver 
:~$ winepath 
err:process:start_wineboot failed to start wineboot, err 1359
:~$ wineboot

```

---

### Post by kc1di on 2015-07-30
Hello brunomandaloriano,   

Try this from a terminal.```
sudo apt-get purge wine
```
Then ```
sudo apt-get install wine
```

see if it will work now.

---

### Post by Simon_Tomoko on 2015-07-30
First you are certain the program you want to run is located in; /opt/photo3/kids.exe ?

[INDENT]The reason I ask is, most Windows programs are stored in $HOME/.wine/drive_c/
I would move/copy it to $HOME/.wine/drive_c/photo3/kids.exe
[/INDENT]

Second from those prompts I would purge the wine and reinstall 1.7.44-amd64, you can find it [here]("https://www.playonlinux.com/wine/binaries/linux-amd64/").

Third read [my tutorial]("http://ubuntuforums.org/showthread.php?t=2288305") about my non-evasive procedure to install WINE.

Let me know how it goes.

---

### Post by Paulo_Bergo on 2015-07-31
Hi.
My Wine stoped too, since the updates of jul, 28 (Xubuntu 14).
I've tried to reinstall but it didn't fix it.
I noticed the same problem on Lubuntu 15.04 after updating and installing Lubuntu and updating at the same time.
Reinstall didn't fix...
I'll try to reinstall 1.7.44...
Thanks!

---

### Post by Paulo_Bergo on 2015-07-31
Hi.
After successfully installation of 1.7.44 the problem continues.

Typing

[email]bergo@P01157220:~/.wine[/email]/drive_c/Program Files (x86)/EditPlus 3$ 
wine editplus.exe

doesn't open the program and

dmesg

Leads to this result

[71956.984429] wineserver[25842]: segfault at 71af2d0 ip 00000000071af2d0 sp 000000002598b8c0 error 14 in ld-2.19.so[7ff8071ae000+23000]

and

wineserver -p

Leads to crash: "sorry, wine64-preloader stopped working..."

---

### Post by Paulo_Bergo on 2015-07-31
Hi

New update!

Applied... restart... and voilá! Wine working find again!

Solved!

---

### Post by Simon_Tomoko on 2015-08-01
Good to hear.  I think your wine might have been still active in memory? That is just a guess. I have some programs that have barked at me.  I look through open processes and see that WINE didn't close down 100%. So I end up killing the process or doing a restart.

---

### Post by brunomandaloriano on 2015-08-05
> **kc1di said:**
> Hello brunomandaloriano,   
Try this from a terminal.```
sudo apt-get purge wine
```
Then ```
sudo apt-get install wine
```
see if it will work now.

Thanks, that was the first thing i tried, without success


> **Simon_Tomoko said:**
> First you are certain the program you want to run is located in; /opt/photo3/kids.exe ?[INDENT]The reason I ask is, most Windows programs are stored in $HOME/.wine/drive_c/
I would move/copy it to $HOME/.wine/drive_c/photo3/kids.exe
[/INDENT]
Second from those prompts I would purge the wine and reinstall 1.7.44-amd64, you can find it [here]("https://www.playonlinux.com/wine/binaries/linux-amd64/").
Third read [my tutorial]("http://ubuntuforums.org/showthread.php?t=2288305") about my non-evasive procedure to install WINE.
Let me know how it goes. 

Thanks. First: Yes, it is an specific application that I use at my company, I had to make some adaptations and cretated an script to install it under Ubunttu, I decided to keep the executables at this folder. Second: Tried That without success.

> **Paulo_Bergo said:**
> Hi
New update!
Applied... restart... and voilá! Wine working find again!
Solved!

Yeah, that worked for me to, I have others PC running Ubuntu 12.04 and it didn't happen to them, the only difference is that they are 32bit.

> **Simon_Tomoko said:**
> Good to hear.  I think your wine might have  been still active in memory? That is just a guess. I have some programs  that have barked at me.  I look through open processes and see that  WINE didn't close down 100%. So I end up killing the process or doing a  restart.


I do not think so, I restart the PC a lot when I had the problem it seems that it was an problematic update but I can not be more specific since I did not investigate it more.

---

### Post by monkeybrain20122 on 2015-08-05
Probably the latest kernel update was the culprit [https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1479040](https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1479040)

If this is the issue booting into the previous kernel should work.

---

