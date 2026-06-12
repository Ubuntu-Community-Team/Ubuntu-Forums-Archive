---
title: "heroes of might and magic 3 installation problems"
date: 2008-05-11
forum: Wine
---

### Post by bobzzz on 2008-05-11
hi im having problems installing heroes of might and magic 3. when i click on the setup.sh file it says Couldn't display "/media/cdrom0/setup.sh". not in a folder.i would really be happy if any one can help me im running the ubuntu hardy

---

### Post by itix on 2008-05-11
Uh... thats the wrong way to install a windows game in linux. You have to use the "emulator" called wine. Post this thread under the "Wine" section and they'll be able to help you.
Personally I don't use wine because I hate it.

If this is a linux specific game, there should be installing instructions in the game manual.

---

### Post by Perfect Storm on 2008-05-11
```
cd /media/cdrom0
sudo sh setup.sh
```

If it doesn't help, copy the setup file to your Desktop, then;

```
cd ~/Desktop
chmod +x setup.sh
sudo ./setup.sh
```

---

### Post by bobzzz on 2008-05-11
yes it is a linux game,and in the manual it says:Mount the Heroes III CD and change the current directory to where
it is mounted.  Type 'sh setup.sh' to run the install script.

e.g.  Log in as root:
	mount /mnt/cdrom
	cd /mnt/cdrom
	sh setup.sh

and i pasted the mount..... peice in the terminal and it says that the directory doesnt exist.im sorry but im completely new to linux distro`s and im trying my best.

---

### Post by drunkmatador on 2008-05-11
I'm confused.. does this game support linux, or are those instructions to get it running in wine? I love this game and own a copy but I'm pretty sure it's only for PC.

---

### Post by Perfect Storm on 2008-05-11
It's called something else. It's an old game. In the file browser, press <ctrl>+<L> and you can see the path.

---

### Post by Perfect Storm on 2008-05-11
> **drunkmatador said:**
> I'm confused.. does this game support linux, or are those instructions to get it running in wine? I love this game and own a copy but I'm pretty sure it's only for PC.

It's an old Loki game. Loki ported it years ago. But there linux installer works very poorly - so buying old loki games is a risk to take. Better buy newer games then instead.

---

### Post by bobzzz on 2008-05-11
A.I. in the terminal it shows:bobzzz@bobzzz-laptop:~$ cd ~/Desktop
bobzzz@bobzzz-laptop:~/Desktop$ chmod +x setup.sh
bobzzz@bobzzz-laptop:~/Desktop$ sudo ./setup.sh


what do i do now.if its not too much trouble.thank you for the other replies as well

---

### Post by Perfect Storm on 2008-05-11
Did something happen when you ran the last command? A installer window?

---

### Post by bobzzz on 2008-05-11
unfortunately not i pasted the command and then pressed enter and then it showed me:./setup.sh: 9: function: not found
x86

---

### Post by Perfect Storm on 2008-05-11
ok, try with **sudo sh setup.sh** instead

---

### Post by acoustibop on 2008-05-11
I was just discussing mounting Playstation CDs with someone, so I thought I'd try "sudo mount -t iso9660 /dev/<device> /mnt/<folder>" where /dev/<device> is the drive your CD is in (try /dev/cdrom or /dev/cdrom0) and /mnt/<folder> is a folder you create in /mnt for mounting CDs - you can call <folder> whatever you want.  Worked fine: I could browse the CD.

So if your game is a Linux game you would do:
"sudo mount -t iso9660 /dev/<device> /mnt/<folder>
cd /mnt/<folder>
sh setup.sh"
by my reckoning.

**Edit:** sorry, I missed the last several posts (got distracted while writing the post).  You seem to have got pretty much that far anyway. ;)

---

### Post by bobzzz on 2008-05-11
no it doesnt work.thank you very much for your trouble i have a windows copy that ill play through wine or cedega.or i can just stick to wesnoth
thanks again and have a nice day

---

### Post by bobzzz on 2008-05-11
i have found the solution to my problem after several hours on google through trial and error.

bobzzz@bobzzz-laptop:~$ cd /media/cdrom0
bobzzz@bobzzz-laptop:/media/cdrom0$ bash setup.sh
bobzzz@bobzzz-laptop:/media/cdrom0$ sudo bash setup.sh


that is what i did and it worked and now i can enjoy my game.

---

### Post by dox_drum on 2009-01-25
Thank you bobzzz!

Just one comment. Aa far as I understood, the second line of command is not needed.

---

### Post by jewelry_wang on 2009-09-15
> **bobzzz said:**
> i have found the solution to my problem after several hours on google through trial and error.

bobzzz@bobzzz-laptop:~$ cd /media/cdrom0
bobzzz@bobzzz-laptop:/media/cdrom0$ bash setup.sh
bobzzz@bobzzz-laptop:/media/cdrom0$ sudo bash setup.sh


that is what i did and it worked and now i can enjoy my game.
Thanks a lot bobzzz! As dox_drum said, we may have to use "sudo bash setup.sh" to install it.

---

