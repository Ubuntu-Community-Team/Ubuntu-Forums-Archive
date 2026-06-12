---
title: "Mozilla build of Firefox won't launch on 64-bit Hardy"
date: 2009-07-19
forum: x86 64-bit Users
---

### Post by running_rabbit07 on 2009-07-19
Is there any way to upgrade FF3.0 to FF3.5 for 8.04 via GUI.

I have searched a few threads already and can not find a way to install 3.5 without CLI. The last time I tried with CLI, I had to reinstall my OS. 

I have a hard time understanding why it will not be in repositories for the LTS until 2011.

---

### Post by wabbalee on 2009-07-19
ff3.5? mine is 3.0.11 and as far as I know the latest version. any particular reason you want to be running this? seems like a beta, and if you want to run beta software you should learn to master the dreaded CLI as most of this software is not packaged yet, otherwise just stick to what's in the repo's.

---

### Post by aysiu on 2009-07-20
Here. I've made a video for you on how to do it via the GUI:
[http://www.youtube.com/watch?v=GW1MVXVReys](http://www.youtube.com/watch?v=GW1MVXVReys)

It took me quite a while to make, but I hope you find it useful. If you don't, perhaps someone else will.

---

### Post by Sef on 2009-07-20
>  I have a hard time understanding why it will not be in repositories for the LTS until 2011.

Once a version is released, then only security updates are issued.   3.5 will be available in Karmic Koala, 10.09.  Also you can update by [PPA]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").   It is easy to do.

---

### Post by running_rabbit07 on 2009-07-20
> **aysiu said:**
> Here. I've made a video for you on how to do it via the GUI:
[http://www.youtube.com/watch?v=GW1MVXVReys](http://www.youtube.com/watch?v=GW1MVXVReys)

It took me quite a while to make, but I hope you find it useful. If you don't, perhaps someone else will.

That video worked sweet, thanks for making it.

I do have a problem now, I tried to restart to fix it but it didn't work. 

The problem is after the install, that showed no errors, the launch icon doesn't work nor does clicking links in thunderbird to get FF to open.

Does anybody know a fix for this?

Thanx

---

### Post by aysiu on 2009-07-20
> **running_rabbit07 said:**
> That video worked sweet, thanks for making it.

I do have a problem now, I tried to restart to fix it but it didn't work. 

The problem is after the install, that showed no errors, the launch icon doesn't work nor does clicking links in thunderbird to get FF to open.

Does anybody know a fix for this?

Thanx
Well, those are two separate problems. Let's try to tackle them one at a time, first with the Firefox one.

First of all, what is the command the launcher is using to launch Firefox? Right-click on the launcher and select *Properties*.

Also, just to make sure it did install properly can you paste these commands into the terminal and post the output back here? ```
which firefox
ls -l /usr/bin/firefox
ls -l /usr/bin/firefox.ubuntu
```

---

### Post by running_rabbit07 on 2009-07-20
> **aysiu said:**
> Well, those are two separate problems. Let's try to tackle them one at a time, first with the Firefox one.

First of all, what is the command the launcher is using to launch Firefox? Right-click on the launcher and select *Properties*.

Also, just to make sure it did install properly can you paste these commands into the terminal and post the output back here? ```
which firefox
ls -l /usr/bin/firefox
ls -l /usr/bin/firefox.ubuntu
```

In the properties the command is "firefox %u

Here's the screenshot of those commands.

Thanx for the super quick response.

---

### Post by wabbalee on 2009-07-20
> Also you can update by PPA. It is easy to do.

@Sef
thanks for the tip.

---

### Post by aysiu on 2009-07-20
> **running_rabbit07 said:**
> In the properties the command is "firefox %u

Here's the screenshot of those commands.

Thanx for the super quick response.
Everything looks good. In theory ```
firefox %u
``` should work fine. Can you try, though, changing the launcher command to straight-up ```
firefox
``` and seeing if that makes a difference?

---

### Post by running_rabbit07 on 2009-07-20
> **aysiu said:**
> Everything looks good. In theory ```
firefox %u
``` should work fine. Can you try, though, changing the launcher command to straight-up ```
firefox
``` and seeing if that makes a difference?

It still doesn't load.

Both before and after changing the command, it starts loading then disappears. I don't know if that helps the diagnosis.

I looked in Synaptic and it shows 3.0 is still installed and it doesn't shows 3.5.

---

### Post by aysiu on 2009-07-20
That's strange.

It's normal for it not to show up in Synaptic, since we did not use the package manager to install it.

What about if you launch it from the terminal? Just use the command ```
firefox
``` and see if, after the window disappears if the terminal spits out any error messages at you.

By the way, are you using any kind of special Ubuntu? PowerPC? 64-bit?

---

### Post by running_rabbit07 on 2009-07-20
> **aysiu said:**
> That's strange.

It's normal for it not to show up in Synaptic, since we did not use the package manager to install it.

What about if you launch it from the terminal? Just use the command ```
firefox
``` and see if, after the window disappears if the terminal spits out any error messages at you.

By the way, are you using any kind of special Ubuntu? PowerPC? 64-bit?


It is AMD64.
Here's the screenshot. There was an error.

---

### Post by aysiu on 2009-07-20
> **running_rabbit07 said:**
> It is AMD64.
Here's the screenshot. There was an error.
So does ```
sudo apt-get install --reinstall libdbus-glib-1-2 && firefox &
``` fix it?

---

### Post by raymondh on 2009-07-20
cool video Aysiu.  Fast processing as well.

---

### Post by running_rabbit07 on 2009-07-20
> **aysiu said:**
> So does ```
sudo apt-get install --reinstall libdbus-glib-1-2 && firefox &
``` fix it?


I think it is waiting for more commands, didn't do anything.

---

### Post by slakkie on 2009-07-20
Not really via the gui but:

[http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

Download the .deb, install it, then run the script which got installed (check with dpkg -L ubuntuzilla) and you have FF 3.5, same script can remove FF as well. Works well.

---

### Post by aysiu on 2009-07-20
> **running_rabbit07 said:**
> I think it is waiting for more commands, didn't do anything. Since there are no error messages, I think it thinks Firefox launched successfully. How long have you waited for Firefox to actually appear?

> **slakkie said:**
> Not really via the gui but:

[http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

Download the .deb, install it, then run the script which got installed (check with dpkg -L ubuntuzilla) and you have FF 3.5, same script can remove FF as well. Works well. Not really helpful in this case. I was heavily involved in the early development of UbuntuZilla, and it really just automates the process by which running_rabbit07 has already installed Firefox.

---

### Post by running_rabbit07 on 2009-07-20
For at least a minute.

The first time I entered the command I thought it needed a password and when I typed it I got the same thing as this screenshot (just with my password visible instead of the -?.) That is why I think it is waiting on more input.

---

### Post by aysiu on 2009-07-20
I'm a bit stumped here.

Any 64-bit Hardy users out there who can test this out and help running_rabbit07?

Unfortunately, as I run either i386 or lpia, and I'm on Jaunty (with only a Hardy live CD), and there aren't any other helpful error messages, I'm at a bit of a loss here.

---

### Post by running_rabbit07 on 2009-07-20
> **aysiu said:**
> I'm a bit stumped here.

Any 64-bit Hardy users out there who can test this out and help running_rabbit07?

Unfortunately, as I run either i386 or lpia, and I'm on Jaunty (with only a Hardy live CD), and there aren't any other helpful error messages, I'm at a bit of a loss here.

Thanks for the help. You have more than helpful in trying to figure this out. Worse come to worse I'll upgrade to JJ to get it to run. Again thanx for the help.

---

### Post by aysiu on 2009-07-20
I'm going to edit the title of your thread and move it to the 64-bit subforum, and hopefully that'll draw in the right kind of support folks.

---

### Post by running_rabbit07 on 2009-07-20
> **aysiu said:**
> I'm going to edit the title of your thread and move it to the 64-bit subforum, and hopefully that'll draw in the right kind of support folks.

Sweet, Thanks!

---

### Post by zaddik01 on 2009-07-20
> **Sef said:**
> Once a version is released, then only security updates are issued.   3.5 will be available in Karmic Koala, 10.09.  Also you can update by [PPA]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").   It is easy to do.

I have a question about the security updates. I built 3.5 myself, which is easy to do, but I am curious about security updates? I also couldn't get it to install using sudo checkinstall, so I installed it straight up. Any suggestions?

Thanks!

---

### Post by running_rabbit07 on 2009-07-20
I went ahead and installed 9.04 and loaded Shireteko. Works fine.

---

### Post by running_rabbit07 on 2009-08-14
Installed Karmic Alpha 4. (9.10 is not yet released- use at your own risk)

---

