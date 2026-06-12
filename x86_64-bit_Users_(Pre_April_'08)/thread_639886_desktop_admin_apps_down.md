---
title: "desktop admin apps down"
date: 2007-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrsudo on 2007-12-13
i have recently installed ubuntu on my athlon x2 64 and have had problems in both kde and gnome.  i am sure each iso is the x86 64 version.  many times i go to start an application and the taskbar will just read "admin application starting"  but nothing will start.  my terminal is working but many commands just end up hanging with no ouput.  do you think it may be hardware issue.

---

### Post by Thelasko on 2007-12-17
I have never seen anything quite like you are talking about.  However, I had a mis-configured video driver once that made my screen become unreadable when the "admin application starting" dialog box appeared.  What kind of video card do you have?  Have you tried running the program in the terminal?  In the terminal type "sudo gedit" using Gnome or "sudo kate" in KDE.  Does the program freeze then?

---

### Post by mrsudo on 2007-12-17
i have a geforce 6150 LE.  do you think it may be a missing or misconfigured driver?  
its really hard to update my system seeing as i still havent gotten my wifi working and cant use a wired connection.  

i can use text editors like kate and gedit when i first boot although after running a few applications, one will end up not starting and then very few commands in the terminal will respond, even sudo kate.  it command hangs and i can no longer input anything in the terminal (konsole).

---

### Post by Thelasko on 2007-12-18
The reason I was asking if you can run "sudo kate" is to see if your computer is freezing when it asks for a password.

When a command hangs you can kill it with the "killall" followed by the process name. For example:
> killall kate

To your question about video drivers.  Yes, if you haven't taken your machine onto the internet to install the NVidia drivers it might be a problem.  NVidia drivers are not open source but instead supplied by NVidia.  Therefore, they are not included on the installation cd.  You must use the "restricted drivers manager" to get the NVidia driver.

I don't have an NVidia card so I don't have any experience with this.  Sorry, but that's all I know.

---

### Post by mrsudo on 2007-12-19
ive tried downloading the nvidia driver and installing.  no difference!  
one example of the prompt freezing that i can give is:

iwlist scanning

eth0  interface does not support scanning

then there should be a wlan0  . . . . .  but it just stays blank as apposed to when i first boot up and there are no problems it shows a few wifi networks under wlan0 with the same command

---

### Post by Thelasko on 2007-12-21
This looks beyond my abilities.  Especially since this is wifi related.  The only suggestion I have is using the command: ```
iwlist wifi0 scan
```
my guess is that iwlist checks it's interfaces starting with eth0 and then stops running on the error message.  If that's the case then the above command will tell it to only check wifi0.

Have you read the [HOW TO?]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

Anybody else have some suggestions?

---

