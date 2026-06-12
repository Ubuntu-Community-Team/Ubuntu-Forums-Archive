---
title: "Fluxbox Screw-up"
date: 2006-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Frank65 on 2006-04-06
Hello,

I have a problem which I hope one of you wonder people can help me with.

A few days ago I downloaded Fluxbox from fluxbox.sourceforge.net. I used the Synaptic Packe Mgr. to extract it and give it a place to stay. After reading a few of the txt. files or Readme files, I couldn't find instructions on how to start up Fluxbox.

So I came to this forum in search of a thread and I found one entitled "General - fluxbox how-to... plus tips & tricks". I discovered a post by a user called ***otake-tux*** posted on Jan. 13, '06. I followed starting at step 4 (because the Fluxbox file was already extracted).

At step 8, things must have gone haywire mostly due to the fact that I didn't know what to expect after issuing the commands. That's where the whole procedure stalled.

I must have turned the machine off or logged out and restarted and I was presented immediately after username and p/w with yellow exclamation point and the following:

[I]Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Etc. ...

[Checkbox] View details (~/.xsession-errors file)

/etc/gdm/PreSession/Default: Registering...
/etc/gdm/PreSession/Default: running /usr/bin/X11/sessreg -a ... etc.
/etc/gdm/Xsession: Beginning session setup...[/I]

I got into Terminal and found the files and placed "#'s" at the beginning of each line I entered before. But that didn't seem to help.

I know I screwed something up. Can anyone help me fix this at least to the point where the old Ubuntu was? 

Thanks for your patience with me.

Frank65

---

### Post by dermotti on 2006-04-06
FYI, Fluxbox is in the ubuntu repositories

**sudo apt-get install fluxbox** to install

---

### Post by DJ Scribblinni on 2006-04-06
Just a quick question regaurding your situation, are you also saying you cannot get into Gnome?  If the login manager isn't messed up you should still be able to select the Gnome as a Window Manager from the Actions list.  From there you will be able to change the files that need to be worked on, which sounds like the ~/.fluxbox/init and/or the ~/.fluxbox/startup files.  You could also try (at the login screen) pressing Ctl+Alt+Backspace, from there you'll be able to login into a command line interface...


Yes the fluxbox is in the repositories, but it is the old version.... The better version is the v0.9.15...
[http://fluxbox.sourceforge.net/]("http://fluxbox.sourceforge.net/")

---

### Post by pgmario on 2006-04-07
[quote=Frank65]Hello,

I have a problem which I hope one of you wonder people can help me with.

A few days ago I downloaded Fluxbox from fluxbox.sourceforge.net. I used the Synaptic Packe Mgr. to extract it and give it a place to stay. After reading a few of the txt. files or Readme files, I couldn't find instructions on how to start up Fluxbox.

So I came to this forum in search of a thread and I found one entitled "General - fluxbox how-to... plus tips & tricks". I discovered a post by a user called ***otake-tux*** posted on Jan. 13, '06. I followed starting at step 4 (because the Fluxbox file was already extracted).

At step 8, things must have gone haywire mostly due to the fact that I didn't know what to expect after issuing the commands. That's where the whole procedure stalled.

I must have turned the machine off or logged out and restarted and I was presented immediately after username and p/w with yellow exclamation point and the following:

[I]Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Etc. ...

[Checkbox] View details (~/.xsession-errors file)

/etc/gdm/PreSession/Default: Registering...
/etc/gdm/PreSession/Default: running /usr/bin/X11/sessreg -a ... etc.
/etc/gdm/Xsession: Beginning session setup...[/I]

I got into Terminal and found the files and placed "#'s" at the beginning of each line I entered before. But that didn't seem to help.

I know I screwed something up. Can anyone help me fix this at least to the point where the old Ubuntu was? 

Thanks for your patience with me.

Frank65[/quote]I've had a similar problem (not fluxbox-related, though). In GDM, select the terminal mode. In the terminal type: ```
sudo chmod 700 .ICEauthority
``` and then ```
exit
```. 
You will be presented with GDM again. Try to log in. I don't know if this works for you, but it helped here when my session was terminated before it had really started.

---

### Post by Frank65 on 2006-04-07
Ok, here's the latest status:

The instructions I followed said to create a .xsession file in my home directory with exec /usr/local/bin/fluxbox. When I  list the directories of /usr/local/bin there is no entry for a .xsession. If , from there, I cd/fluxbox, I'm told fluxbox: Not a directory.

After I nano ~/.xsession, I placed a # in front of the exec command I previously entered.

Then, nano ~/.fluxbox/startup. I placed a # in front of my entry exec /usr/local/bin/fluxbox -log ~/.fluxbox/log.

My original entry attempt at editing /usr/share/xsessions was unsuccessful.

Sudo chmod...etc. didn't yield any visible results and the problem still remains.

I'm thinking that the instructions I followed pertained to an older, less refined version of Fluxbox. I am perfectly willing, at this somewhat infantile stage of my learning Linux and Ubuntu, to do an entire reinstall from the original CD and start over.

I am hanging on your every word. 

Thanks again for the help.

Frank65

---

### Post by jdp on 2006-04-07
One thing to note is that files/directories that start with a period do not show in a regular **ls** command.  You have to use **ls -a** to show them.  They will show if you are using a root shell, however.

---

### Post by Frank65 on 2006-04-08
In my zeal to get back on the learning curve with Ubuntu and Linux in general, I have decided to reinstall Ubuntu from scratch.

So as of right now, I'm back to square one with a smile and renewed enthusiasm with a new installation on my old iMac.

Thanks for all your help.

Let's put this Fluxbox thing to rest and get on with the experience.

Frank65

---

