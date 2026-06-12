---
title: "No binfmt-support"
date: 2008-03-13
forum: Wine
---

### Post by sharkbite1414 on 2008-03-13
I download wine from a windows PC and transfered it to my Ubuntu PC but when I tried to install it i got this error,

Error: Dependency is not satisfiable: binfmt-support

I need to get binfmt-support. If I need to download anything it has to be done on a Windows XP PC as I do not have internet.

Please help, thanks.

---

### Post by compiledkernel on 2008-03-13
sudo apt-get install binfmt-support

---

### Post by pizzipie on 2008-04-26
I am very low intermediate Ubuntu 7.10 user. Just installed 7.10 in fact. That is why I need to install wine again..

Well I also got the "missing binfmt-support" message.
I tried [apt-cache search binfmt-support] with no results.
Then naturally, [apt-get install] doesn't work either.


I then searched for 'binfmt-support' on the internet and got a Ubuntu Forum which tried to explain what it is. I downloaded it and now have no clue what to do. Trying to install wine just gives the same message. I gunzipped the file and used tar to extract the files. Now I'm totally lost!!! 

Any help in this installation would be greatly appreciated.

R

---

### Post by cogadh on 2008-04-26
You are going to find that trying to install Wine without internet access is going to be a huge pain. If you get the binfmt-support .deb package and install it before you install Wine, it might work, but I believe you will just find that there are dependencies that binfmt-support requires which cannot be met. If you have the ability to connect the machine to the internet, even temporarily, it will make things much easier.

---

### Post by pizzipie on 2008-04-26
Thanks Cogadh,

I can connect to the internet but what then? I tried downloading the newest wine selection for feisty and now the error message says the dependency libaudio2 can't be met. It didn't mention binfmt-support, however. I did not have any problem with feisty installing wine or, in fact, using wine.

I am baffled! Newer versions can't run wine now!!! What is going on??

Thanks, again for your help.

R

---

### Post by puifais on 2008-04-27
So I installed the binfmt-support on my Ubuntu Hardy Heron and then ran into a similar problem where it says "Error:  Dependency is not satisfiable:  libldap2."  So I tried installing libldap2 but apparently this thing isn't available.  Terminal said slapd libldap-2.4-2 replaced it and the package libldap2 has no installation candidate.  I don't have internet, still, so now what?

---

### Post by puifais on 2008-04-27
I did something that looked very promising then crapped out at 26% :(

so I did 

sudo apt-get install binfmt-support

This solved the binfmt-support dependency, but it came up with libldap2 dependency error instead.  At this point, just ignore this message.  I went back to terminal and type

sudo apt-get install wine

Then it worked hard trying to install the program until 26% was completed then gave me this message:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe wine 0.9.59-0ubuntu4           
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.92.3). - connect (101 Network is unreachable) [IP: 91.189.92.3 80]
Fetched 79.2kB in 6min50s (193B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu4_i386.deb)  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.92.3). - connect (101 Network is unreachable) [IP: 91.189.92.3 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I feel like I'm really really close to making this work.

---

### Post by cogadh on 2008-04-28
> **pizzipie said:**
> Thanks Cogadh,

I can connect to the internet but what then? I tried downloading the newest wine selection for feisty and now the error message says the dependency libaudio2 can't be met. It didn't mention binfmt-support, however. I did not have any problem with feisty installing wine or, in fact, using wine.

I am baffled! Newer versions can't run wine now!!! What is going on??

Thanks, again for your help.

R
You don't have to manually download the packages separately, once you are connected to the internet, you just need to use apt-get. It will download and automatically install all of the appropriate packages and dependencies for you. However, since you have attempted to install multiple packages manually, you might need to clean things up first. Run this to get rid of anything you might have leftover:
```
sudo apt-get remove --purge wine binfmt-support
```
Once that is complete, run this to install Wine correctly:
```
sudo apt-get install wine
```

As for why Wine is a bit more difficult to install now, in the past, previous versions of Ubuntu did not include the additional built-in support for Wine and Windows executables that it has had since Gutsy. Even though it does make it more difficult to install Wine manually, it is better for using Wine effectively: the .exe format is automatically associated with Wine; Wine is added to the Applications menu, with shortcuts to uninstall software, configure Wine, browse the fake Windows directory and any applications you have installed with Wine... it is generally a much more user-friendly Wine experience now.

> **puifais said:**
> I did something that looked very promising then crapped out at 26% :(

so I did 

sudo apt-get install binfmt-support

This solved the binfmt-support dependency, but it came up with libldap2 dependency error instead.  At this point, just ignore this message.  I went back to terminal and type

sudo apt-get install wine

Then it worked hard trying to install the program until 26% was completed then gave me this message:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe wine 0.9.59-0ubuntu4           
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.92.3). - connect (101 Network is unreachable) [IP: 91.189.92.3 80]
Fetched 79.2kB in 6min50s (193B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu4_i386.deb)  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.92.3). - connect (101 Network is unreachable) [IP: 91.189.92.3 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I feel like I'm really really close to making this work.

You just have a bad connection to the repository servers. You should probably switch to a more local mirror server. Open the Add/Remove programs utility, click on Edit Software Sources, in the "Download from" drop-down list, select "Other" and then click the "Find Best Server" button. That will reset your repository to the best connection it can find among all the mirrors and you should be able to complete the download/install.

---

### Post by K-Ragorn on 2008-09-14
I too have been through some trouble installing wine, but I found the solution by first installing the binfmt-support package which I found[ here]("http://www.filewatcher.com/m/binfmt-support_1.1.5_all.deb.16064.0.0.html"). (top of the list)
After this Wine installation went on flawlessly.
Hope it works for you all too :)

---

### Post by FactTech on 2009-02-21
FYI for anyone else encountering this issue -- The binfmt-support package is part of the community-maintained software repositories (i.e. "universe"). If Synaptic is complaining that it can't satisfy this dependency, it is most likely because you have not enabled this repository.

Go to System, Administration, Software Sources, and make sure the box for "Community-maintained Open Source Software (universe)" is checked. You will then need to reload the repository data -- which should happen automatically as you close out of the Software Sources program.

---

