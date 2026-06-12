---
title: "doom 3 x64 ubuntu 8.10 ibex"
date: 2009-01-11
forum: x86 64-bit Users
---

### Post by sankster2001 on 2009-01-11
hey guys/girls, this is my first post and i am a noob when it comes to linux, but anyway when itry to install it gives me a error. see screenshot posted this is most annoying as my machine was built for gaming and i cant even do that. 
any help would be aprciated thanks Tom

---

### Post by insane_alien on 2009-01-11
seems you're missing a file thats supposed to be at ~/.setup6297 you can try just creating a blank file with that name and trying agian.

---

### Post by sankster2001 on 2009-01-11
nope that didnt work 
thanks

---

### Post by william_nbg on 2009-01-11
which version of doom3 are you trying to install?

what command are you typing into the terminal?

---

### Post by sankster2001 on 2009-01-11
trying to install DOOM III 1.3.1, build 1304 from [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/) but just keeps saying that error, i have tried typing sh ~/Desktop/doom3-linux-1.3.1.1304.x86.run, and setting the .run file to run when double clicked.
thanks

---

### Post by william_nbg on 2009-01-12
Sorry for the delay, I went out last night.

I asked because I just installed Doom 3, and for the first time on a 64-bit system. Fortunately, I didn't experience any problems. I have never seen the error that you have gotten, but a couple of ideas:

are you using "sudo"?

instead using the sh command try typing it like this:

sudo ./doom3-linux-1.3.1.1304.x86.run

replacing the "sh" with "./"

Second: in the permission, is the game file executable?

Hope it helps. The game is working great on my box.

---

### Post by sankster2001 on 2009-01-15
no worries mate hope ya had good night :), but any ways nope that didnt work it said:  
thomas@thomas-desktop:~$ sudo ./doom3-linux-1.3.1.1304.x86.run
sudo: /etc/sudoers is owned by uid 1000, should be 0

---

### Post by MGaddict2000 on 2009-08-29
I'm using Ubuntu 9.04 and Slackware Linux (obviously dual boot). I'm getting the exact same error. When I goto /root, the file is definatly not there in either distro. Is there a dependency I should probably have installed? In Ubuntu I am using sudo. But it seems oddI get the same exact error in both distros. I'm using the same NVIDIA drivers (manually installed) on both, could that be the problem? And it's not just Doom3, I get the same thing with Quake 4. Anybody know some other high end game I could try installing?

---

