---
title: "[SOLVED] Firefox wont start"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by wortxyzzy on 2008-05-19
I have looked extensively on Google, and throughout the forums and cant seem to find a fix for my problem. Many people have similar problems, but non of the fixes seem to help, so here goes.

My firefox wont start from the icon, just says starting then a few seconds later it stops and disappears out of the taskbar. No error pop up.

From the terminal, the command "firefox"  results in "Illegal instruction".
"firefox -g"  gives the same results.  

I have tried deleting or renaming my .mozilla folder.  Doesn't help.
I have logged in as a different user.  Still doesn't work.

I'm running the updated version out of the repository, so 3.0 b5  I'm pretty sure.   I'm not completely sure at what i did that stopped it from working, may have been an update, or a computer restart.

I have uninstalled it and reinstalled it, no change.

I'm on Hardy Heron x86 64

and "strace firefox" has to much for me to cut it all and put it in here, i don't even know how to go all the way back, but i think the last part is what is important:


......
access("/home/ely/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}", F_OK) = 0
open("/home/ely/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}", O_RDONLY|O_NONBLOCK|O_DIRECTORY|0x80000) = 27
fstat(27, {st_mode=S_IFDIR|0755, st_size=48, ...}) = 0
getdents(27, /* 2 entries */, 4096)     = 48
getdents(27, /* 0 entries */, 4096)     = 0
close(27)                               = 0
access("/usr/share/mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}", F_OK) = 0
open("/usr/share/mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}", O_RDONLY|O_NONBLOCK|O_DIRECTORY|0x80000) = 27
fstat(27, {st_mode=S_IFDIR|0755, st_size=48, ...}) = 0
getdents(27, /* 2 entries */, 4096)     = 48
getdents(27, /* 0 entries */, 4096)     = 0
close(27)                               = 0
access("/usr/lib/mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}", F_OK) = 0
open("/usr/lib/mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}", O_RDONLY|O_NONBLOCK|O_DIRECTORY|0x80000) = 27
fstat(27, {st_mode=S_IFDIR|0755, st_size=48, ...}) = 0
getdents(27, /* 2 entries */, 4096)     = 48
getdents(27, /* 0 entries */, 4096)     = 0
close(27)                               = 0
open("/usr/lib/firefox-3.0b5/chrome/browser.jar", O_RDONLY) = 27
lseek(27, 0, SEEK_END)                  = 1776527
lseek(27, 1775503, SEEK_SET)            = 1775503
read(27, "istory-panel.xulPK\1\2\27\3\n\0\0\0\0\0009\233m8"..., 1024) = 1024
lseek(27, 1765814, SEEK_SET)            = 1765814
read(27, "PK\1\2\27\3\n\0\0\0\0\0\24\2\2021\35\16K\225\35\327\0\0"..., 4096) = 4096
read(27, "\20\0\0,\0\0\0\0\0\0\0\0\0\0\0\244\201\n\310\r\0conten"..., 4023) = 4023
read(27, "places/places.xmlPK\1\2\27\3\n\0\0\0\0\0:\22U"..., 4080) = 2594
read(27, "", 4018)                      = 0
open("/usr/lib/firefox-3.0b5/chrome/browser.jar", O_RDONLY) = 28
lseek(28, 605603, SEEK_SET)             = 605603
read(28, "PK\3\4\n\0\0\0\0\0\322 78\352\211\210\346\202%\0\0\202"..., 30) = 30
lseek(28, 605660, SEEK_SET)             = 605660
read(28, "//@line 39 \"/build/buildd/firefo"..., 9602) = 9602
close(28)                               = 0
access("/home/ely/.mozilla/firefox/s6u393oc.default/places.sqlite", F_OK) = 0
open("/home/ely/.mozilla/firefox/s6u393oc.default/places.sqlite", O_RDWR|O_CREAT, 0644) = 28
fcntl(28, F_GETFD)                      = 0
fcntl(28, F_SETFD, FD_CLOEXEC)          = 0
fstat(28, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
lseek(28, 0, SEEK_SET)                  = 0
read(28, "", 100)                       = 0
fcntl(28, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(28, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(28, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/ely/.mozilla/firefox/s6u393oc.default/places.sqlite-journal", F_OK) = 0
fcntl(28, F_GETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741825, len=1, pid=18446744073163522165}) = 0
fstat(28, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
unlink("/home/ely/.mozilla/firefox/s6u393oc.default/places.sqlite-journal") = 0
fcntl(28, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
fcntl(28, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(28, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(28, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/ely/.mozilla/firefox/s6u393oc.default/places.sqlite-journal", F_OK) = -1 ENOENT (No such file or directory)
fstat(28, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
fcntl(28, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
fcntl(28, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(28, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(28, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/ely/.mozilla/firefox/s6u393oc.default/places.sqlite-journal", F_OK) = -1 ENOENT (No such file or directory)
fstat(28, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
fcntl(28, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=1073741825, len=1}) = 0
open("/home/ely/.mozilla/firefox/s6u393oc.default/places.sqlite-journal", O_RDWR|O_CREAT|O_EXCL, 0644) = 29
open("/home/ely/.mozilla/firefox/s6u393oc.default", O_RDONLY) = 30
fcntl(30, F_GETFD)                      = 0
fcntl(30, F_SETFD, FD_CLOEXEC)          = 0
fcntl(29, F_GETFD)                      = 0
fcntl(29, F_SETFD, FD_CLOEXEC)          = 0
fstat(29, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
open("/dev/urandom", O_RDONLY)          = 31
read(31, "\237\230\205\35293\306\335\201#g\267\t\377n)Z\363}\330"..., 256) = 256
close(31)                               = 0
lseek(29, 0, SEEK_SET)                  = 0
write(29, "\331\325\5\371 \241c\327\0\0\0\0\221&\300\2\0\0\0\0\0\0"..., 24) = 24
lseek(29, 4095, SEEK_SET)               = 4095
write(29, "\0", 1)                      = 1
--- SIGILL (Illegal instruction) @ 0 (0) ---
unlink("/home/ely/.mozilla/firefox/s6u393oc.default/lock") = 0
rt_sigaction(SIGILL, {SIG_DFL}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [ILL], NULL, 8) = 0
tgkill(7288, 7288, SIGILL)              = 0
--- SIGILL (Illegal instruction) @ 0 (0) ---
+++ killed by SIGILL +++
Process 7288 detached
ely@ely-ubuntu:~$ 

Im really sorry if this is a duplicate, if it is just point me in the right direction, and if not I'd really appreciate any advice.   

Thx in advance,
William

---

### Post by bikeboy on 2008-05-19
Don't know if it will help, but have you tried *firefox -ProfileManager* then make a new profile? Or -safe-mode ?

It will at least help you determine if it's a profile/extension problem causing Firefox to not start.

---

### Post by wortxyzzy on 2008-05-19
Thanks for the response,
with  "firefox -ProfileManager"   i created a new profile called test,
and it wouldn't start either.  "Illegal instruction"
"-safe-mode"  same thing "Illegal instruction"

Anyone have any other suggestions?

---

### Post by bikeboy on 2008-05-19
Okay, at least that rules out some things. I missed that you'd tried a different profile already btw.

It's not something that I do regularly on Linux, but a purge and reinstall might help.

```
sudo apt-get --purge remove firefox && sudo apt-get install firefox
```

---

### Post by wortxyzzy on 2008-05-19
did the purge without errors, and the installation went smooth, but still have the same problem.

ely@ely-ubuntu:~$ sudo apt-get --purge remove firefox && sudo apt-get install firefox
[sudo] password for ely: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper classpath-gtkpeer classpath-common cacao libgcj-common classpath
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firefox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 123kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 114122 files and directories currently installed.)
Removing firefox ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper classpath-gtkpeer classpath-common cacao libgcj-common classpath
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/64.8kB of archives.
After this operation, 123kB of additional disk space will be used.
Selecting previously deselected package firefox.
(Reading database ... 114120 files and directories currently installed.)
Unpacking firefox (from .../firefox_3.0~b5+nobinonly-0ubuntu3_all.deb) ...
Setting up firefox (3.0~b5+nobinonly-0ubuntu3) ...
ely@ely-ubuntu:~$ firefox
Illegal instruction
ely@ely-ubuntu:~$ firefox -safe-mode
Illegal instruction
ely@ely-ubuntu:~$ firefox %u
Illegal instruction

---

### Post by wortxyzzy on 2008-05-19
oh just saw the  apt-get autoremove   it didnt change anything either

---

### Post by bikeboy on 2008-05-19
Hmm, it's now beyond any of the tricks I'm aware of. Hope somebody else can provide more insight.

---

### Post by felker2 on 2008-05-20
What happens when you run firefox from within another Linux account?

What happens if you de-install firefox via apt-get, and then install firefox from getfirefox.com? 

BTW: as you're posting in the 64-bit forum: could the problem be 64- versus 32-bit related?

---

### Post by wortxyzzy on 2008-05-20
Attempting to run it from a different user account, has the same results. Wont start -- Illegal instruction  

As for uninstalling and reinstalling from firefox's site,  The main thing i like about this distro is being able to keep all of my software up-to-date automatically. I would rather not install outside of the manager. I tend to find myself doing a complete reinstall soon after i deviate from the norms.  which despite how far they have come, it is no walk in the park to get ubuntu back to how i like it.

And the 64 bit thing.  I'm kinda new to the posting thing, usually i can quickly find the answer just by searching around. So i didn't really know were would be best to put the problem. Since i am running 64bit i thought this was as good a place as any.  I don't think it is necessarily 64bit specific though, or more people would be having this problem, not just the corrupt .mozilla folder.  

Thanks for your suggestions, keep um coming

---

### Post by pixel :-) on 2008-05-21
You purged firefox, but firefox is just a metapakage,if you noticed your dear computer removed only 123kb when you purged.use firefox-3.0 instaid

Do a mem check at boot up.Did you have any issues in general? like crashes.

remove all firefox plugins.

try full path /usr/bin/firefox
              /usr/bin/firefox-3.0

maybe one of the dependencies is corrupted/buged.Say (some examples) xulrunner or libmozjs or libxul0d or libxul-common.I still have xulrunner version ubuntu3 for example,try downgrading this last one to my version and reinstall the others.

Upgrade fully,maybe some newer stuff is in colision with older things.

install firefox 2? It's in the repository.
name "firefox-2".Firefox 3 is officially in beta.

---

### Post by wortxyzzy on 2008-05-21
Wow, thanks for the post.  Such a strange thing, libxul0d and libxul-common were both not installed.  So after installing them, my fox is back up and running.

---

