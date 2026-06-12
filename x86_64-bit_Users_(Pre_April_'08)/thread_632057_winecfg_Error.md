---
title: "winecfg Error"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jabb3r on 2007-12-05
Just someting else that seems to work for everyone else but not me.  64bit *shakes head*

So my story so far. I'm trying to get secondlife workking. NO the linux alpha won't run, YES I've got all I need installed even the ELFIO stuff.

So I think ok, lost that battle but how about wine/ hmm sounds like a plan. So I get all I need via synaptic and it all installs wonderfully. So I think oh I'm getting somewhere so I run  sudo winecfg and now get thin.

I h8 windows but I don't get why I'm having so many probs doing what everyone else seems to be able to do. I'm more than annoyed.

Anyhoo my error...

jabb3r@saturn:~$ sudo winecfg
wine: creating configuration directory '/home/jabb3r/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/jabb3r/.wine'.
jabb3r@saturn:~$ wineserver: could not save registry branch to /home/jabb3r/.wine-vsEWoh/system.reg : No such file or directory
wineserver: could not save registry branch to /home/jabb3r/.wine-vsEWoh/user.reg : No such file or directory


Segmentation will be the death of me.

---

### Post by Jabb3r on 2007-12-06
Finally worked it out. Borked install of Ubunu. Re burned reinstalled. Even SL client works now. :)

---

### Post by roger99 on 2007-12-06
I get a very similar error when trying to run winecfg

```
beavis@beavis-laptop:~$ winecfg
wine: creating configuration directory '/home/beavis/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/beavis/.wine'.
beavis@beavis-laptop:~$ wineserver: could not save registry branch to /home/beavis/.wine-D5cVtl/system.reg : No such file or directory
wineserver: could not save registry branch to /home/beavis/.wine-D5cVtl/user.reg : No such file or directory

```

Everything else seems to work correctly so i don't think that a borked install disc is my problem.  Anybody got any ideas?

---

### Post by Rhubarb on 2007-12-06
Firstly, never run "sudo winecfg".
You should run winecfg without admin rights.
```
winecfg
```

Secondly, it's a good idea to use the latest version of wine (use for gutsy gibbon 7.10):
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```
Have a look here if you're using an older version of ubuntu:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Thirdly, if winecfg isn't working, delete ~/.wine
Then run winecfg, then try installing your windows games / apps.

---

### Post by roger99 on 2007-12-06
> **Rhubarb said:**
> Firstly, never run "sudo winecfg".
You should run winecfg without admin rights.
```
winecfg
```

Secondly, it's a good idea to use the latest version of wine (use for gutsy gibbon 7.10):
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```
Have a look here if you're using an older version of ubuntu:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Thirdly, if winecfg isn't working, delete ~/.wine
Then run winecfg, then try installing your windows games / apps.

Err, thats helpful then.....  I never have or never would run winecfg with root priviliges.  Wine is up to date using the repo from WineHQ.  And i have no .wine directory, as the error i posted states, winecfg cannot create it.

---

### Post by Rhubarb on 2007-12-06
I'm not sure why wine isn't working for you there roger99.  Seems quite odd to me.
I know you wheren't running wine with admin privileges roger99.
If you look at Jabb3r's post, you'll see that he did call for wine with admin privileges - which is a definite no no to do.

---

