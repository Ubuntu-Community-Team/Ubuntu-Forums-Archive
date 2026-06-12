---
title: "Install Adobe Flash 64 bits"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by neonl on 2007-11-04
Hi

I'm having a problem which is that when I try to execute the Adobe Flash instalation script on Terminal I get this: ```
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
```
It's the first time I'm running the x64 version of Ubuntu...

BTW if you are so kind pls give me a hand to install Adobe Reader too.

Thank you so very much!

---

### Post by Cappy on 2007-11-04
Use
```
sudo apt-get install flashplugin-nonfree
```

Try searching next time by entering into this x86 64-bit subforum and then searching on "flash" in the top right hand corner, for instance.

---

### Post by JAwuku on 2007-11-04
Even easier if you have 64-bits, you can just type ```
 sudo apt-get install flashplugin-nonfree
```

and it will automatically install ndiswrapper and download the Adobe Flash player.

---

### Post by Yellow Pasque on 2007-11-04
You can use the version available in the repo as both posts above describe. If this fails for some reason, you can use nspluginwrapper to force the libflashplayer to work with a 64-bit browser (details available upon request).

---

### Post by John.Michael.Kane on 2007-11-04
For codec/flash see this sticky thread install [Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

For acroread under gutsy 64.

Run:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Followed by
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Then.
```
sudo aptitude install acroread acroread-plugins acroread-escript
```

---

### Post by neonl on 2007-11-05
Ok, thank you all! :)

---

### Post by ksg089 on 2007-11-10
I tried using the sudo command that was suggested above and my terminal generated the following:

ken@ken-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
ken@ken-laptop:~$ 


I am very new to Linux and I just want to install Flash Player so that YouTube works in Firefox. What went wrong?

---

### Post by Kilz on 2007-11-10
> **ksg089 said:**
> I tried using the sudo command that was suggested above and my terminal generated the following:

ken@ken-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
ken@ken-laptop:~$ 


I am very new to Linux and I just want to install Flash Player so that YouTube works in Firefox. What went wrong?

The package is only available for Gutsy Gibbon in 64bit, are you running Gutsy?

---

### Post by bonka on 2007-11-10
i found it easier installing through firefox

find a site which has flash and install it through there

---

### Post by John.Michael.Kane on 2007-11-10
> **ksg089 said:**
> I tried using the sudo command that was suggested above and my terminal generated the following:

ken@ken-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
ken@ken-laptop:~$ 


I am very new to Linux and I just want to install Flash Player so that YouTube works in Firefox. What went wrong?
What version of Ubuntu are you using?

---

### Post by ksg089 on 2007-11-10
Yes, I'm running Gutsy Gibbon.

Bonka, what do you mean by installing through Firefox?

> **Kilz said:**
> The package is only available for Gutsy Gibbon in 64bit, are you running Gutsy?

---

### Post by rsambuca on 2007-11-10
You just have to activate your repositories first.  Go to the top menu bar and select "System -> Administration -> Software Sources".  On the first tab, make sure the universe and multiverse tabs are checked, and then close the Window.  Reload the repos when you are prompted.  You can then run that command and you will be fine.

---

### Post by ksg089 on 2007-11-10
Ok, I changed the settings in Software Sources and it did a little updating when I closed it. I have no idea what you mean when you say 'Reload the repos', I'm new to Linux and am trying to get used to the lingo.

I ran the code again and Terminal now gave me this:
ken@ken-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1) but 0.9.91.4-0ubuntu3~upure64 is to be installed
  nspluginwrapper: Depends: lib32gcc1 (>= 1:4.1.2) but it is not installable
                   Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not installable
                   Depends: ia32-libs but it is not going to be installed
                   Depends: ia32-libs-sdl
                   Depends: ia32-libs-gtk
                   Depends: lib32asound2 but it is not installable
                   Depends: gsfonts-x11 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


> **rsambuca said:**
> You just have to activate your repositories first.  Go to the top menu bar and select "System -> Administration -> Software Sources".  On the first tab, make sure the universe and multiverse tabs are checked, and then close the Window.  Reload the repos when you are prompted.  You can then run that command and you will be fine.

---

### Post by bonka on 2007-11-10
> **ksg089 said:**
> Yes, I'm running Gutsy Gibbon.

Bonka, what do you mean by installing through Firefox?

What I mean is that, let's say you go to a site through firefox which uses flash, it will come up with a message stating that it is missing a plugin. It then will ask you to either install the adobe version or another one, forget what that one is. I had trouble installing through the package manager and through terminal. This worked like a charm. Plus it installs all the plugins for Firefox to use flash.

---

### Post by rsambuca on 2007-11-10
> **ksg089 said:**
> Ok, I changed the settings in Software Sources and it did a little updating when I closed it. I have no idea what you mean when you say 'Reload the repos', I'm new to Linux and am trying to get used to the lingo.

I ran the code again and Terminal now gave me this:
ken@ken-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1) but 0.9.91.4-0ubuntu3~upure64 is to be installed
  nspluginwrapper: Depends: lib32gcc1 (>= 1:4.1.2) but it is not installable
                   Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not installable
                   Depends: ia32-libs but it is not going to be installed
                   Depends: ia32-libs-sdl
                   Depends: ia32-libs-gtk
                   Depends: lib32asound2 but it is not installable
                   Depends: gsfonts-x11 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

OK, something is a little messed up, but we should be able to fix it.  Open a terminal and enter```
sudo apt-get -f install
```Then read what it says.  If it says everything is OK, try installing again.

---

### Post by ksg089 on 2007-11-10
Here's what came up in the console this time around:

ken@ken-laptop:~$ sudo apt-get -f install
[sudo] password for ken:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ken@ken-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1) but it is not going to be installed
E: Broken packages


> **rsambuca said:**
> OK, something is a little messed up, but we should be able to fix it.  Open a terminal and enter```
sudo apt-get -f install
```Then read what it says.  If it says everything is OK, try installing again.

---

### Post by John.Michael.Kane on 2007-11-10
First run this command  to make sure it you remove everything that's problematic not configured.
```
sudo aptitude -f remove
```

Next you can try to configure all packages that are unconfigured.
Run:
```
sudo dpkg --configure -a
```

Then:
```
sudo aptitude remove -f nspluginwrapper
```

Next try reinstalling nspluginwrapper first.
```
sudo aptitude install nspluginwrapper
```

Follwed by
```
sudo aptitude install flashplugin-nonfree
```

rsambuca may have more to add,however. try the above method to see if it gets you going.

---

### Post by Kilz on 2007-11-10
> **ksg089 said:**
> Ok, I changed the settings in Software Sources and it did a little updating when I closed it. I have no idea what you mean when you say 'Reload the repos', I'm new to Linux and am trying to get used to the lingo.

I ran the code again and Terminal now gave me this:
ken@ken-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1) but 0.9.91.4-0ubuntu3~upure64 is to be installed
  nspluginwrapper: Depends: lib32gcc1 (>= 1:4.1.2) but it is not installable
                   Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not installable
                   Depends: ia32-libs but it is not going to be installed
[B]                   Depends: ia32-libs-sdl
                   Depends: ia32-libs-gtk[/B]
                   Depends: lib32asound2 but it is not installable
                   Depends: gsfonts-x11 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

 ia32-libs-sdl and ia32-libs-gtk do not exist in Gutsy. They were incorporated into ia32-libs. Something is wrong if the nspluginwrapper deb requires them and you are running Gutsy.

---

### Post by rsambuca on 2007-11-11
**ksg089** - Post the output of this:```
cat /etc/apt/sources.list
```

---

### Post by Corbelius on 2007-11-11
> **ksg089 said:**
> I tried using the sudo command that was suggested above and my terminal generated the following:

ken@ken-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
ken@ken-laptop:~$ 


I am very new to Linux and I just want to install Flash Player so that YouTube works in Firefox. What went wrong?

Enable universe e multiverse repositories.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> **ksg089 said:**
> Ok, I changed the settings in Software Sources and it did a little updating when I closed it. I have no idea what you mean when you say 'Reload the repos', I'm new to Linux and am trying to get used to the lingo.

I ran the code again and Terminal now gave me this:
ken@ken-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1) but 0.9.91.4-0ubuntu3~upure64 is to be installed
  nspluginwrapper: Depends: lib32gcc1 (>= 1:4.1.2) but it is not installable
                   Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not installable
                   Depends: ia32-libs but it is not going to be installed
                   Depends: ia32-libs-sdl
                   Depends: ia32-libs-gtk
                   Depends: lib32asound2 but it is not installable
                   Depends: gsfonts-x11 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

This my nspluginwrapper package from feisty, the dependencies are different, disable feisty repo and install nspluginwrapper from gutsy official repo.

---

### Post by snakep on 2007-11-19
Okay, so I am having a similar problem with flash in firefox.  I originally installed the flash player through the synaptic package manager.  When I go there, it shows that flash player is installed, and the nspluginwrapper as well.  In fact, I know that nspluginwrapper is installed, because I can run:

```
Aragorn:~> nspluginwrapper -l
/usr/lib/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5

```

But it still won't work in Firefox.  I tried 
```

nspluginwrapper -u /usr/lib/firefox/plugins/flashplugin-alternative.so

```

but that doesn't seem to have helped either.

Any ideas?

P.S.  I'm running gutsy.  Also, 

```
Aragorn:~> ls /usr/lib/firefox/plugins/
flashplugin-alternative.so  libtotem-mully-plugin.so
libtotem-basic-plugin.so    libtotem-mully-plugin.xpt
libtotem-basic-plugin.xpt   libtotem-narrowspace-plugin.so
libtotem-gmp-plugin.so      libtotem-narrowspace-plugin.xp

```

Thanks for the help.

---

### Post by 1veedo on 2008-03-28
Same thing here.  about:plugins shows that flash (version 9) is installed but I go to youtube and none of the videos work.

I fixed it like this,> **John.Michael.Kane said:**
> First run this command  to make sure it you remove everything that's problematic not configured.
```
sudo aptitude -f remove
```

Next you can try to configure all packages that are unconfigured.
Run:
```
sudo dpkg --configure -a
```

Then:
```
sudo aptitude remove -f nspluginwrapper
```

Next try reinstalling nspluginwrapper first.
```
sudo aptitude install nspluginwrapper
```

Follwed by
```
sudo aptitude install flashplugin-nonfree
```

rsambuca may have more to add,however. try the above method to see if it gets you going.

---

