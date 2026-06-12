---
title: "Starting win executables and security"
date: 2008-06-27
forum: Wine
---

### Post by skim23 on 2008-06-27
Hi *,

first thing, I don't really have any problems with wine so far, I can run the needed window applications (it's mostly WoW tho ;) ), so thanks to the devs on this one.

But I noticed that every application of the type win executable is started via wine, even from the terminal. How can I protect myself against, say, starting a manual.pdf.exe accidentally by double clicking it? I know, I shouldn't, but since I run Linux, I'd like to have the extra protection. Is there any setting I can change so that just launching an exe via terminal or double click would not work anymore and I am forced execute "wine program.exe" everytime?

My system: xubuntu 8.04 amd 64

Thanks in advance

---

### Post by pytheas22 on 2008-06-27
Maybe Xubuntu is different, but by default, Gnome won't start an .exe if you double-click on it.  You have to right-click and explicitly select "open with wine" for it to run.  Unfortunately I've never really used xfce so I don't know how you would tell it not to open something with wine when you double-click (why are you using Xubuntu if you have 64-bit processor and therefore presumably a relatively new machine?).

In the terminal, if you just type something like:
```

manual.pdf.exe
```

it's not going to do anything except complain that it doesn't recognize the command.  You would have to prefix the command with "wine" for wine to open it.  So you shouldn't worry about accidentally launching Windows executables from the terminal.

I guess if you're really worried, you could move wine out of your path, i.e. move it from /usr/bin to somewhere else.  Then the system won't be able to start wine unless you explicitly give it the whole path.

But I wouldn't worry about this too much anyway.  In principle wine could run Windows malware, but the vulnerabilities that an exploit expects to find on the system are unlikely to be there, because the wine code is not the same as Windows'.  Moreover, wine operates only with the privileges of the local user, so it's not going to touch the Linux system.  In a worst case, an apt-get remove --purge wine would clear out any problems.  But I've never heard of Windows malware ever damaging anything via wine anyway.

---

