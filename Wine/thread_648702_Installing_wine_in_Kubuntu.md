---
title: "Installing wine in Kubuntu"
date: 2007-12-23
forum: Wine
---

### Post by -gabe-noob- on 2007-12-23
How can I do this, I tried following the same steps I used for ubuntu but it didnt work because of me having to run the command dpkg --configure -a to install it, it said I  needed superuser privileges to do this, how can I get the superuser privileges

---

### Post by jualin on 2007-12-23
to get superuser privileges type 
"su" and then run the command

---

### Post by jualin on 2007-12-23
you could also install wine from Adept Manager in Kubuntu without using the konsole.

---

### Post by -gabe-noob- on 2007-12-23
Thanks, but I'm having problems with adept too because "another process is using the packaging system database"

---

### Post by -gabe-noob- on 2007-12-23
and when I do su and type in my password it says su: Authentication failure
Sorry.

---

### Post by jualin on 2007-12-23
ok try killing all the adept processes using CTRL+ALT+ESC. If that does not work reboot your computer and try running adept

---

### Post by -gabe-noob- on 2007-12-23
neither of what you sugested for adept worked... :( :( :(  and I cant get superuser to work because it keeps onsaying authentication failed

---

### Post by jualin on 2007-12-23
ok "authentication failed" means that you are putting the wrong password. Did you install Ubuntu recently?. If you did you need to change the root password sometimes so run
> sudo passwd and enter your new password. Sometimes the command is > sudo passwd root. If the password change was successful you should be able to login as superuser. Let me know if this helps.

---

### Post by -gabe-noob- on 2007-12-23
it works and I'm now able to get in as supeuser but when I try to install wine it gets stuck at here, and I still have no luck with ade pt 

0% [connecting to wine.budgetdedicated.com...................  

and it stays like that for a while then times out

edit forgot to update :P lets see if it works

update is stuck at this 
99% [Connecting to wine.budgetdedicated.com (81.171.111.184)]

---

### Post by jualin on 2007-12-23
how about installing synaptic? >  sudo apt-get install synaptic that is another package manager, you could install wine from there.

---

### Post by -gabe-noob- on 2007-12-23
yea I was thinking about getting syntapc (or however you spell it) cause I'm more familiar with it but i couldnt get it from adept so I didnt know what to do

---

### Post by jualin on 2007-12-23
you could also try killing all the adept processes and try running adept again. > killall adept

---

### Post by jualin on 2007-12-23
try > sudo apt-get install synaptic to install synaptic. My personal opinion is that synaptic is better than adept.

---

### Post by -gabe-noob- on 2007-12-23
ahh god now synaptic is taking FOREVER to download wine, its not even moving

this is what I get after a while 

W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.51~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.51~winehq0~ubuntu~7.10-1_i386.deb)
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out



Edit: on a totaly unrealated note do you know any bridge builder type games that I can get from synaptic thats already in the repos?

---

### Post by jualin on 2007-12-23
This website has some information of how to install wine [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) this should work in Kubuntu too. Give it a try. I hope it works

---

### Post by -gabe-noob- on 2007-12-23
yea I've already started trying that, thanks for all your help man

---

### Post by jualin on 2007-12-24
My pleasure bro, I hope you get it to work. That's the bad thing about linux, sometimes you have to try some things for a while until they finally work. The good thing about using Ubuntu or Kubuntu is that the forum community is wonderful, the response is almost instant. That's why is my favorite distro. How long have u been using linux?

---

### Post by TeaSwigger on 2007-12-24
I use WINE in Kubuntu and haven't had an issue installing it.

Ah which repository are you using for WINE? Perhaps remove it from your sources.list and try the WINE from the ubuntu repos first. I can only speak from my own experiences here, but I later updated to using WINE's repositories over the ubuntu repos version and had no problem. Note ubuntu's version put shortcuts in my menu for anything I installed in WINE and the WINE repos version doesn't. Not a serious matter though since it is easy to "roll your own" shortcuts.

Less likely from what I gather, but to pass along experience from a recent "could not" ;) is a firewall or router or moblock/peerguardian possibly interfering with the connection?

---

### Post by -gabe-noob- on 2007-12-24
The week before 7.10 came out, just got fed up with vista and installed ubuntu, I've been using ubuntu since then and I'm just tying kubuntu now

---

### Post by -gabe-noob- on 2007-12-24
also another totaly unrelated qustion, how can I get dvds to work with Kaffine it keeps on telling me they are crypted, note I didn't even get the dvd plugins for totem in normal ubuntu

---

### Post by -gabe-noob- on 2007-12-24
hmm yea, I'm sorta kinda just getting internet from my grandmas neighbor, sorta "stealing it" I'm a baddd man a badd bad man, CALL IN THE E POLICE!

---

### Post by cogadh on 2007-12-24
I don't want to take this back to the beginning, but some of the steps you have been advised to take could have been avoided and some of the information you have been given is inaccurate.
You just needed to use "sudo" to run the dpkg command:
```
sudo dpkg --configure -a
``` 
You didn't need to create a root password (in fact it is usually recommended that you don't) and if you wanted to run with superuser permissions you can just run "sudo su".

The packages from the Wine repositories are identical to the package that is in Ubuntu's repository, except for the version (i.e. the WineHQ package will create the menu shortcuts, just like the Ubuntu package). In fact, both package sets are maintained by the same person.

As for the problem you are having getting the Wine package, since you are "borrowing" someone else's internet connection, I assume you are using wireless. Is it possible that you just don't have a good solid connection?

---

