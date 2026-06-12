---
title: "[SOLVED] Uninstalling Wine - Problems"
date: 2008-05-20
forum: Wine
---

### Post by ggsherma on 2008-05-20
How do you uninstall Wine?

I wanted to re-download wine and it says I already have it installed. I tried the command in the terminal window, no-go. I somehow deleted the wine folder in a terminal window by typing rm something (can't remember the name) -- but when I try and download it it says I still have it installed.

Is there a way to completely get rid of everything that .wine made?

Thanks.

---

### Post by prshah on 2008-05-20
> **ggsherma said:**
> How do you uninstall Wine?
Thanks.

Remove wine:```
sudo apt-get autoremove --purge wine
rm -rf ~/.wine
```

Note no sudo for the rm command.

Reinstall wine without removing:```
sudo apt-get install --reinstall wine
```

---

### Post by pedro_orange on 2008-05-20
```
uninstaller
```

Will give you a tool that can be used to delete apps that have been installed under WINE.

---

### Post by ggsherma on 2008-05-20
I did the two commands and when I try to access the .wine directory it tells me it does not exists.

```
geoff@geoff-laptop:~$ sudo apt-get autoremove --purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wine*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 55.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110972 files and directories currently installed.)
Removing wine ...
Purging configuration files for wine ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
geoff@geoff-laptop:~$ rm -rf ~/.wine
geoff@geoff-laptop:~$ sudo apt-get install --resinstall wine
E: Command line option --resinstall is not understood
geoff@geoff-laptop:~$ sudo apt-get install --reinstall wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8309kB of archives.
After this operation, 55.8MB of additional disk space will be used.
Selecting previously deselected package wine.
(Reading database ... 110353 files and directories currently installed.)
Unpacking wine (from .../wine_1.0~rc1~winehq0~ubuntu~8.04-1_i386.deb) ...
Setting up wine (1.0~rc1~winehq0~ubuntu~8.04-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
geoff@geoff-laptop:~$ cd .wine
bash: cd: .wine: No such file or directory
geoff@geoff-laptop:~$ ls
Desktop    Examples   Music            Pictures   Videos
Documents  kiba       patch2.txt       Public     winetricks
dx         mfc42.dll  patch_allow.txt  Templates
geoff@geoff-laptop:~$ 


```

---

### Post by mc4man on 2008-05-20
try running winecfg from terminal

---

### Post by hellomoto on 2008-05-20
when I removed WINE i used synaptic package manager. It will show any software you have and will remove configuration files. 


Just open it up and search for WINE.

:)

---

### Post by ggsherma on 2008-05-20
> **mc4man said:**
> try running winecfg from terminal

that worked. Thanks :)

---

### Post by hellomoto on 2008-05-20
ggsherma if this problem is fixxed please dont forget to mark this thread as solved. :)

---

### Post by ggsherma on 2008-05-20
Thanks! Marked as Solved as of 1:28 PM Eastern May 20th, 2008.

---

