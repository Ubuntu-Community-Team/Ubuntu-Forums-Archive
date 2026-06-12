---
title: "No space/Not owned Wine error"
date: 2013-05-16
forum: Wine
---

### Post by tomaspkr on 2013-05-16
I have wine 1.5.29. Ubuntu version 13.04.

When i try to instal a game with wine it says that there is no free space on the disk. However I have more than 400GB. 
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       455G   11G  422G   3% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G   12K  1.9G   1% /dev
tmpfs           382M  884K  381M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G   80K  1.9G   1% /run/shm
none            100M   64K  100M   1% /run/user

ANY directory I choose I get there is no free space error, even though I can download anything. So there is something wrong with Wine. Moreover, if I type: sudo wine aa.exe, I get: /home/username/.wine is not owned by you. Is this the problem? I have a fresh instal of Ubuntu and a fresh, clean disk. No Windows installed with Ubuntu. I am the only user on the computer.

---

### Post by tomaspkr on 2013-05-17
Bump. Anyone?

---

### Post by CatKiller on 2013-05-17
Don't run Wine as root.

If you don't have write permissions on your ~/.wine folder then your Windows application will not be able to create its files and will think you're out of disk space.

Correct your ownership and permissions problems and stop running random things as root.

---

### Post by tomaspkr on 2013-05-17
What does running random things as root? I don't use the terminal to run them. I do it through GUI. That means running it through root? And I seem to have the permision to write. Maybe you could write a command needed for this? Because i tried looking for it on other threads but couldn't find it.

---

### Post by CatKiller on 2013-05-18
> **tomaspkr said:**
> What does running random things as root? I don't use the terminal to run them. I do it through GUI.

This
> **tomaspkr said:**
> if I type: sudo wine aa.exe, I get: /home/username/.wine is not owned by you.

is running Wine as root. Don't do that.

 [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The error message could be because your ~/.wine directory isn't owned by root, which should be true, or it might mean that by running things as root it's no longer owned by your user.

Or the application might not work in Wine.

---

### Post by tomaspkr on 2013-05-19
> **CatKiller said:**
> This


is running Wine as root. Don't do that.

 [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The error message could be because your ~/.wine directory isn't owned by root, which should be true, or it might mean that by running things as root it's no longer owned by your user.

Or the application might not work in Wine.

Sorry, but I did uninstall wine completely and ran it without using root (through the terminal). It still says I don't have enough free space. My C: disk has 300GB of space. I used the guides on winewiki to install it. I also found the section there about the free space issue. I tried to set the application to run on Windows 98, as the guide suggested, but that didn't work. I am sure this game should work, because people had installed it in the past. Would installing Windows and the moving the game to linux directory help, because as far as I remember, the game could just be copied and it would work just fine. Or would that cause some issues for wine? Also, my Ubuntu is not installed using wubi. It is a proper install.

---

### Post by CatKiller on 2013-05-19
> **tomaspkr said:**
> Sorry, but I did uninstall wine completely and ran it without using root (through the terminal). 

That won't do anything to your ~/.wine folder, I'm afraid.

> It still says I don't have enough free space. My C: disk has 300GB of space. I used the guides on winewiki to install it. I also found the section there about the free space issue. I tried to set the application to run on Windows 98, as the guide suggested, but that didn't work. I am sure this game should work, because people had installed it in the past.

Without knowing what the game is, or which guide you followed, it's impossible to comment. If it's a known problem with this game then it probably isn't a permissions problem. This is the kind of information that would have been useful in your first post.

Your post also isn't clear on how exactly it didn't work.

> Would installing Windows and the moving the game to linux directory help, because as far as I remember, the game could just be copied and it would work just fine. Or would that cause some issues for wine? Also, my Ubuntu is not installed using wubi. It is a proper install.

Maybe. Sometimes that works and sometimes it doesn't. It's not a case of causing issues for Wine, it's just that game publishers tend to go out of their way to make that kind of thing not work.

---

### Post by tomaspkr on 2013-05-20
My game is Lineage 2 c5. I tried installing a bigger app and it had no problems. Something is wrong with this game. I know people played it on Linux so it should be possible to fix it. By the way, thank you for your time.

---

### Post by CatKiller on 2013-05-20
Are you using 64-bit Wine? I've found a very old forum post that suggested 32-bit Wine as a workaround for this problem with this game. It's not one that I have any experience with.

---

### Post by tomaspkr on 2013-05-20
I used the 1.1.6 version of wine, as the game was tested using it, and  it worked. Thanks for pointing that other wine versions should work.  (tried to use 32-bit, but don't know whether I succeeded in doing that,  since the installer didn't work). I used playonlinux to use the older  wine version.

---

### Post by CatKiller on 2013-05-21
It'll be something like ```
 sudo apt-get install wine-1.4:i386
``` but I must admit that I don't really understand multi-arch.

---

