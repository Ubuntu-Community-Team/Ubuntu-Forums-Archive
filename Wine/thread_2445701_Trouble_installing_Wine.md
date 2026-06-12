---
title: "Trouble installing Wine"
date: 2020-06-18
forum: Wine
---

### Post by nginmu on 2020-06-18
64bit Lubuntu 19.10 currently, but quite close to buying a new HDD and installing 20.04 so if there's a likelihood of a resolution just by upgrading, maybe not worth spending too much trouble over..

I was hoping to use Crucial's website to checkout my RAM.

Their scanner involves downloading an executable and running it on your system to determine your memory papameters.

They only provide a Windows executable as far as I can see.

So I thought, okay, I'll try Wine.

I found it in the Muon package manager under 'wine', and went ahead and marked it for installation and applied changes.

Couldn't see a shortcut in the system menu, so I tried going into a terminal

```

me@me-pc:~$ wine
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32"
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
me@me-pc:~$ sudo apt-get install wine32
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine32 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libwine

E: Package 'wine32' has no installation candidate
me@me-pc:~$ wine32
wine32: command not found
me@me-pc:~$ wine64
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
me@me-pc:~$ ls
crucial.exe  Desktop  Documents  Downloads  Music  notepad.exe  Pictures  Public  Templates  thunderbird  Videos
me@me-pc:~$ wine64 crucial.exe
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32"
wine: Bad EXE format for Z:\home\me\crucial.exe.
me@me-pc:~$ wine64 notepad.exe
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32"
wine: Bad EXE format for Z:\home\me\notepad.exe.
me@me-pc:~$ man -k wine64
wine64-stable (1)    - run Windows programs on Unix
me@me-pc:~$ man wine64
me@me-pc:~$ 

```

not quite sure where I'm going wrong.. tried a copy of windows xp's 'notepad.exe' besides the crucial.exe scanner but that seemed to fail as well..

Grateful for any suggestions, tia

---

### Post by ActionParsnip on 2020-06-18
[https://packages.ubuntu.com/eoan/wine](https://packages.ubuntu.com/eoan/wine)

It's in the universe repository. Make sure you have that enabled. Make sure you check the WINE AppDb for compatibility
[https://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](https://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

---

### Post by nginmu on 2020-06-18
Thanks, I ran

```

sudo add-apt-repository main
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install wine32

```

.. and that got Wine working fine.

notepad.exe pulled out from Windows XP works fine.

crucial.exe gives me this..

```

me@me-pc:~$ wine crucial.exe
0009:err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
0009:err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
wine: Unhandled privileged instruction at address 0x46145c (thread 002e), starting debugger...
(long wait................)
me@me-pc:~$ 

```

so I guess whatever way Crucial have programmed their scanner, it just isn't supported by Wine.

---

### Post by ActionParsnip on 2020-06-18
What does the application do, please?

---

### Post by nginmu on 2020-06-18
It's available at [https://www.crucial.com/](https://www.crucial.com/) - it's a utility for scanning your system and reporting it's RAM suitability parameters to assist memory purchasing decisions. I'll find another way to do that; it just had the effect of diverting me into setting up Wine. Wine itself works ok now, it runs notepad.exe just fine.

---

### Post by CelticWarrior on 2020-06-18
> **ActionParsnip said:**
> What does the application do, please?

[https://www.crucial.com/store/systemscanner](https://www.crucial.com/store/systemscanner)

Quite obvious why it doesn't work.

---

### Post by ActionParsnip on 2020-06-18
If you run:
```

sudo lshw | less

```
It should show you the system specs and you can buy RAM based on that. If the system has a make and model then use that.

---

### Post by CelticWarrior on 2020-06-18
And you can check the online database at their website with the brand/model.

---

### Post by QIII on 2020-06-18
Moved to the Wine sub-forum for a better fit.

---

### Post by nginmu on 2020-06-18
Thanks folks. Sorry if it's a dim question but I'll bite, why doesn't it work?

---

### Post by CelticWarrior on 2020-06-18
Such software needs low level access to the hardware/firmware (BIOS or UEFI firmware in this case). Nothing of that sort can be used with Wine, it needs Windows installed in bare metal.

Although very different from virtualization, Wine sort of works in a pseudo-virtual environment where Windows software memory calls are translated to their Unix/Linux equivalents . In simple terms, software requiring such level of hardware access or interaction is "lost in translation".

---

### Post by nginmu on 2020-06-18
Ahh ok.. well at least I got Wine working for those MS executables it does have a chance with. Thanks.

---

