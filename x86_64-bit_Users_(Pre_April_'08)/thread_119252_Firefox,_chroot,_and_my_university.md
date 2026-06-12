---
title: "Firefox, chroot, and my university"
date: 2006-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-01-19
Over the past week or so I have been trying to get Firefox working properly in my Ubuntu-64 Breezy laptop. In addition, I needed to get Adobe Reader 7.0 going, and I wanted to get RealPlayer installed as well. Eventually I gave up and installed chroot, following a link to installation instructions outside of ubuntu.org.

Once I had chroot running I managed to install RealPlayer and Acrobat Reader 7.0 with Synaptic32. They both work great as standalone apps, but I couldn't get either one linked to Firefox.

Then I decided to do what [handy] did in another post I saw, that is, install 32-bit Firefox in chroot. I did so, and amazingly, RealPlayer now works in Firefox32. Haven't gotten Adobe Reader working yet, but one step at a time.

I have been happily enjoying my 32-bit Firefox. But today I needed to spend all day at the university (pdx.edu) and I needed my computer with me. Once I got there I found that I was not able to log into the university network. This always worked fine before, but it was dead today.

Eventually I found that the problem was in 32-bit Firefox. I still have the old (64-bit?) version of Firefox installed, so I launched it and -- lo and behold -- everyting was connectig to the university wifi network fine. After contacting the university IT people I determined that the 32-bit Firefox was finding the university wifi and was connecting to it, but something was blocking any transfer of data. And I have no special firewalls installed on this laptop, other than what the default installation of Ubuntu gave me.

So my question is, does anyone have any idea why regular Firefox that was installed by default in Breezy-64 can connect to my university wifi, but 32-bit Ubuntu does not allow traffic to pass? Any clues at all?

---

### Post by awi on 2006-01-26
Maybe there is a different routing table on your chroot environment, to find out ->  from a shell type
```
$ route -vn

```
 inside chroot and from your normal 64-bits shell

Try to telnet to some web server from within chrooted shell, like this:
```
$ telnet yourwebserver.edu 80
GET / HTTP/1.0

```
after the GET line, you must type ENTER twice.
And see if that get you some output, if it does not, or while you are trying to get some web site with your firefox(32), execute this:
```
$ netstat -tn
```

and look for entries in state SYN_SENT (especially the one for your webserver IP number), that might indicate that there is a firewall blocking the connection.
If there is a connection in state ESTABLISHED, then you might have a ghost or we need to call The Exorcist. :)

---

### Post by John Jason Jordan on 2006-01-26
[QUOTE=awi]If there is a connection in state ESTABLISHED, then you might have a ghost or we need to call The Exorcist. :)[/QUOTE]
Heh.

Thanks for the suggestions. I did finally figure out what was wrong, and I have a sort of solution, but it needs further fixing.

Someone at a local LUG suggested connecting to wifi somewhere (I have just ethernet to cable at home, no wifi), and then trying to ping an IP address instead of pinging a name. So I did that and lo and behold! It worked! Conclusion, it was a DNS issue.

Turns out there is a /etc/resolv.conf file and there is also a /chroot/breezy/32bits/etc/resolv.conf. When connecting to a wifi in the 64-bit mode it automatically changed the lines in /etc/resolv.conf, but the 64-bit world was unaware of the existence of the chroot world, so nothing was changing the nameservers in /chroot/breezy/32bits/etc/resolv.conf.

My solution so far is:

1) Connect to the new connection with 64-bit Firefox or whatever
2) Do "sudo ln -f /etc/resolv.conf /chroot/breezy/32bits/resolv.conf"
3) Open 32-bit Firefox and away I go, no problems.

This works, but what remains to be done is to automate the solution somehow. I have an OO.o Writer file I call "hacks.odt" where I save stuff like the ln line above, together with instructions to remind me how to do it. Still, it is a PITA to have to go through the above just to get my 32-bit world to see the nameservers. What I need to do is figure out some way for this to happen automatically. In other words, I need a script that runs before 32-bit Firefox launches that does the link line above. Note that having the correct nameserves in the chroot resolv.conf file is necessary only to Firefox installed in chroot. All other internet apps are in the 64-bit world. So the script needs to run only when 32-bit Firefox is launched.

I know nothing of writing scripts, nor am I sure my logic above is correct.

I did also think of making the script run on booting, but that won't work. Booting does not change the nameservers in /etc/resolv.conf. That happens only when a new connection is made, e.g., a wifi connection is made and again when I return home and the cable connection is made. Every time I connect someplace new the /etc/resolv.conf file gets changed. That needs to be propagated to the chroot copy of the file before launching 32-bit Firefox.

Am I right? Any suggestions for how to do it?

---

### Post by slavik on 2006-01-26
create a shell script on the desktop and name it 'Connect to college WiFi.sh' ?

something that launches firefox64, then kills it, then does the DNS copy thing and pops up a message (is this possible with shell scripts?) or just ends ...

---

### Post by John Jason Jordan on 2006-01-26
[QUOTE=slavik]create a shell script on the desktop and name it 'Connect to college WiFi.sh' ?

something that launches firefox64, then kills it, then does the DNS copy thing and pops up a message (is this possible with shell scripts?) or just ends ...[/QUOTE]
After thinking about it some more I think you are on track, but launching 64-bit Firefox is not the right thing to do. At my university, after booting, I launch Firefox-64 and I am still not connected. I have to try to go someplace (e.g., a bookmark). A few moments later a tab opens with a NoCat login in the upper left corner. Then I enter my student id and pass and hit enter. Only then am I connected.

However, if I am in a free wireless coffee house, there is no login.

I think the wifi DNS entries for the university wifi are discovered by the System > Administration > Networking dialog box. I'm not sure about that, however. The script (assuming I can figure out how to write one) would have to find the nameservers for whatever wifi spot I am trying to connect to. Maybe I need to go manually to System > Administration > Networking and choose the wifi site I want to connect to before doing the hard link. Sometimes there are multiple wifi options, depending on where I am, e.g., if I am at the Starbucks across the street from the student union, I'll see both theirs and the university's wifi.

I wonder if all I need is just a button on the Gnome panel that does the link thing. Wherever I am I just go first to System > Administration > Networking and choose what I want to connect to, wait until the hourglass stops, and then hit the button for the link script. At that point 32-bit Firefox in chroot should see the nameservers, right?

I really don't understand much about how this stuff works.

---

### Post by slavik on 2006-01-27
did you try to sit there just after booting up without doing anything?

maybe the login comes up on it's own after a while?

---

### Post by John Jason Jordan on 2006-01-27
[QUOTE=slavik]did you try to sit there just after booting up without doing anything? maybe the login comes up on it's own after a while?[/QUOTE]
No, many times I have booted up at the university and just worked for hours before needing the internet. The login never comes up unless I try to go somewhere with Firefox.

I'm just going to have to wait until I go there again to test some of these things. I bet the DNS thing is found as soon as I go into System > Administration > Networking and choose which wifi to connect to. But I won't be able to test that until I go back there on Monday.

---

### Post by awi on 2006-01-27
[QUOTE=John Jason Jordan]
2) Do "sudo ln -f /etc/resolv.conf /chroot/breezy/32bits/resolv.conf"
[/QUOTE]
Why don't use only a symbolic link? with "-s"? That way you would not need to recreate the link every time your /etc/resolv.conf changes.
You have two options editing this file:

```
/etc/dhcp3/dhclient.conf
```
there will be a line like this:

```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
```

1) you can remove 

```
 domain-name, domain-name-servers
```
from that list and have your own /etc/resolv.conf, having two (or *n*) entries for nameserver, with the IP number you usually get from your both providers, this numbers rarely change.
Or 
2) You can add lines like this on the 
```
/etc/dhcp3/dhclient.conf
```

```
supersede domain-name "university.edu home.com";
prepend domain-name-servers 1.2.3.4, 2.3.4.5;

```

that will always have your /etc/resolv.conf the way you need it.

Just curious, did you read this thread?

[http://ubuntuforums.org/showthread.php?t=90106&highlight=firefox32](http://ubuntuforums.org/showthread.php?t=90106&highlight=firefox32)

There is a howto firefox32 without chroot, and will avoid your current problem. :)
I use firefox32 like that.

---

### Post by John Jason Jordan on 2006-01-27
> **awi]Why don't use only a symbolic link? with "-s"? That way you would not need to recreate the link every time your /etc/resolv.conf changes.
You have two options editing this file:[/QUOTE]
I was told by gurus at the local LUG that chroot would barf on a symbolic link said:**
> Just curious, did you read this thread?

[http://ubuntuforums.org/showthread.php?t=90106&highlight=firefox32](http://ubuntuforums.org/showthread.php?t=90106&highlight=firefox32)

There is a howto firefox32 without chroot, and will avoid your current problem. :)
I use firefox32 like that.
Yes, I did read that thread, and before going the chroot route. But I also needed Adobe Reader 7.0, which refused to install until I created chroot. And I also couldn't get RealPlayer to work until I installed it in chroot. I don't mind the chroot environment. And it was a lot easier for a n00bie like me than the instructions on the site you mentioned above.

---

### Post by awi on 2006-01-27
[QUOTE=John Jason Jordan]I was told by gurus at the local LUG that chroot would barf on a symbolic link; that it had to be a hard link. At that I have to use -f in the link command.
[/QUOTE]
Yes, my mistake, the file system changes when you chroot.
Perhaps the [COLOR="DarkOliveGreen"]--bind[/COLOR] option from mount can help you, is used in chrooted enviroments, especially in ftp daemons.

```
# mount --bind /some/dir_or_file /other/dir_or_file
```

---

### Post by John Jason Jordan on 2006-01-27
[QUOTE=awi]Yes, my mistake, the file system changes when you chroot.
Perhaps the [COLOR="DarkOliveGreen"]--bind[/COLOR] option from mount can help you, is used in chrooted enviroments, especially in ftp daemons.
```
# mount --bind /some/dir_or_file /other/dir_or_file
```[/QUOTE]
Hmmm. I need to read up more on bind. I tried "man bind" but there is no manual. Later I discovered that it seems it is an option for the mount command, which I guess is why there is no man page for it. 
But that brings up something else that may be part of the issue. When booting there are a lot of lines scrolling by before X starts. After installing chroot I found six new ones, all of which [fail]:
```
/home on /chroot/breezy/32bits/home type none (rw,bind)
/tmp on /chroot/breezy/32bits/tmp type none (rw,bind)
/dev on /chroot/breezy/32bits/dev type none (rw,bind)
/proc on /chroot/breezy/32bits/proc type none (rw,bind)
/media/cdrom0 on /chroot/breezy/32bits/media/cdrom0 type none (rw,bind)
/usr/share/fonts on /chroot/breezy/32bits/usr/share/fonts type none (rw,bind) 
                                     [FAIL] (in red)
```
The [OK] and [FAIL] occur after each line in the boot process, except the above four have nothing at the end of the line, just a [FAIL] after all four lines. I take that to mean that there is one [FAIL] message for all four lines.
Since all four of them end in "bind," maybe this means that they were supposed to bind to something and didn't. No wait ... this is 64-bit booting, and it was trying to bind the chroot folders and couldn't because it couldn't see inside chroot?
From my dim understanding of bind, it seems to me that all I need is a hard link that is permanent. I.e., any time /etc/resolv.conf changes the change happens instantly and automatically in /chroot/breezy/32bits/resolv.conf as well.

---

