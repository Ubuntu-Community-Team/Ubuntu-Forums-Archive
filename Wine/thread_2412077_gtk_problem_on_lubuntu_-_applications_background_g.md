---
title: "gtk problem on lubuntu - applications background graphics are blurred or transparent"
date: 2019-02-07
forum: Wine
---

### Post by estatistics on 2019-02-07
[COLOR=#000000]Hello Ubuntuers, [/COLOR]

The following problem restricting me from running wine applications. 
Somewhere I read a similar case, and maybe it was caused by installing wine dev varsion, as I did. 

[COLOR=#000000]gtk problem on lubuntu --- I Include pics to understand better the problem.[/COLOR]
[[IMG]https://i.postimg.cc/rDmPZCFM/linux-gtk-bug.png[/IMG]]("https://postimg.cc/rDmPZCFM")
[[IMG]https://i.postimg.cc/v4NSJgc9/linux-gtk-bug2.png[/IMG]]("https://postimg.cc/v4NSJgc9")


[COLOR=#000000]a) When I run an application e.g. gedit, kdenlive, lximage-qt --screenshot etc. their graphics are "disturbed". [/COLOR]
[COLOR=#000000]b) However, when I run them with sudo command, they are looks "ok". [/COLOR]

[COLOR=#000000]This make some application to have great problem e.g. wine apps. [/COLOR]

[COLOR=#000000]I think it must be something on installation, ownership, i dont know. [/COLOR]

[COLOR=#000000]How Can I fix it? [/COLOR]


[COLOR=#000000]Update 1: [/COLOR]
[COLOR=#000000]By experimenting, the following messages appeared when i did sudo visudo [/COLOR][https://stackoverflow.com/questions/...ery-time-for-a]("https://stackoverflow.com/questions/45981317/why-do-i-get-warning-qstandardpaths-xdg-runtime-dir-not-set-every-time-for-a")
[COLOR=#2B91AF][FONT=inherit]Defaults[/FONT][/COLOR][COLOR=#303336][FONT=inherit] env_keep [/FONT][/COLOR][COLOR=#303336][FONT=inherit]+=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"XDG_RUNTIME_DIR"[/FONT][/COLOR][COLOR=#000000]Code:
elias@eliasc:~$ kdenlive
QApplication: invalid style override passed, ignoring it.
inotify_add_watch("/home/elias/.config/lxqt/lxqt.conf") failed: "No such file or directory"
kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/libexec/kf5/klauncher'
kdeinit5: Launched KLauncher, pid = 3314, result = 0
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit5: opened connection to :0.0
inotify_add_watch("/home/elias/.config/lxqt/lxqt.conf") failed: "No such file or directory"
kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so' from launcher.
kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so'
QXcbConnection: XCB error: 8 (BadMatch), sequence: 617, resource id: 52428823, major code: 155 (Unknown), minor code: 11
kdeinit5: PID 3317 terminated.
elias@eliasc:~$ sudo kdenlive
QStandardPaths: wrong ownership on runtime directory /run/user/1000, 1000 instead of 0
QStandardPaths: wrong ownership on runtime directory /run/user/1000, 1000 instead of 0
QXcbConnection: XCB error: 8 (BadMatch), sequence: 620, resource id: 52428823, major code: 155 (Unknown), minor code: 11
elias@eliasc:~$ sudo visudo
visudo: /etc/sudoers.tmp unchanged
elias@eliasc:~$[/COLOR]

[COLOR=#000000]Update 2: [/COLOR]

[COLOR=#1A1A1B]Info from here: [https://www.reddit.com/r/linuxquesti...wnership_when/]("https://www.reddit.com/r/linuxquestions/comments/7gs9xo/issue_with_runtime_directory_ownership_when/")

" export XDG_RUNTIME_DIR=/var/run/user/1000[/COLOR]
[COLOR=#1A1A1B]
I have learned that 1000 is the user ID and 0 is the root ID, so it seems that the error is basically saying that the directory is owned by my ser, but I am trying to run it as root, so its the wrong ownership?[/COLOR]
[COLOR=#1A1A1B]As I said, I'd like to fix the issue but am always trying to figure out what is actually happening. Any help would be appreciated. "[/COLOR]


[COLOR=#000000]Sincerely,[/COLOR]
[COLOR=#000000]Elias Tsolis[/COLOR]

[COLOR=#000000]p.s. No Excuse for Animal Abuse [/COLOR]
[COLOR=#000000]p.s. Fasting from any kind of abuse[/COLOR]

---

### Post by CatKiller on 2019-02-07
> **estatistics said:**
> [COLOR=#000000]However, when I run them with sudo command, they are looks "ok".[/COLOR]

Don't do that. Don't ever do that. And messing around with your sudoers file is a really bad idea.

Your issue is that you're using a theme that you don't seem to like. Change the theme.

---

### Post by estatistics on 2019-02-07
Hello Catkiller,
It is more serious my problem than "colors". 

Some application has "transparent" "backgrounds". Others have "phantom" backgrounds". And wine applications have serious problems. They are not running properly. I think the whole problem is one. I have reinforced reisnatllation gtk2, gtk3, ubuntu desktop, pythons, but nothing worked until now. 

I dont know what to do, I dont knwo how to debbug it! 

The only thing that succeeded is to run properly kdenlive. 

Wine apps dont run! :) 

[COLOR=#000000][COLOR=#000000]Sincerely,[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Elias Tsolis[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]p.s. No Excuse for Animal Abuse [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]p.s. Fasting from any kind of abuse[/COLOR][/COLOR]

---

