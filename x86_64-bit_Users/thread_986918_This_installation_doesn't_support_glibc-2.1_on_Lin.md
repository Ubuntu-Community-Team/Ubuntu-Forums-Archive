---
title: "This installation doesn't support glibc-2.1 on Linux / x86_64"
date: 2008-11-19
forum: x86 64-bit Users
---

### Post by Elliander on 2008-11-19
I am trying to run 32-bit games on Ubuntu 8.10 on an AMD 64-bit. (I chose the 64-bit install because I was under the impression it would include 32-bit code)

After a minor period of trouble with permissions, I managed to get it worked out enough for me to follow the guide here:

[http://cedegawiki.sweetleafstudios.com/wiki/Ubuntu]("http://cedegawiki.sweetleafstudios.com/wiki/Ubuntu")

Under:

> Building a clean 32bit chroot with debbootstrap on AMD64

However, after I followed all of the steps, exactly as listed, I still get this message:

> This installation doesn't support glibc-2.1 on Linux / x86_64 

This is troubling, because the only programs I ever use are 32-bit.

I am totally new to Unix-based systems. I have no idea what I have to do to get this to work. Did I pick the wrong version of Ubuntu? Or is it my hardware? Does Ubuntu, unlike Windows, prevent me from running 32-bit applications on 64-bit hardware?

I want to make the switch from windows but Ubuntu is looking more and more complicated all the time, despite the obvious stability. If it wasn't so stable I would have given up by now.

I know there were other threads made in the past on trying to get 32-bit applications running on an AMD 64-bit, but the previous ones are closed threads and don't provide me any information on how to get this to work right, aside from what I already tried.

---

### Post by Elliander on 2008-11-19
I just tried adding every lib32 I could find under the Synaptic Package Manager, hoping they might include the files needed to make this work, but got the same thing.

> 
elliander@elliander-ubuntu:~$ sudo /home/elliander/Desktop/Creatures3/creatures3.run
Password:
Verifying archive integrity... All good.
Uncompressing Creatures: Internet Edition................................................................................
This installation doesn't support glibc-2.1 on Linux / x86_64

Please contact Creature Labs Technical Support at [http://support.creaturelabs.com](http://support.creaturelabs.com)


---

### Post by Elliander on 2008-11-19
aha. I figured out how to do it. After installing the lib32 files this is the command to use before the run path of a 32-bit game:

> 
sudo linux32 

example:

> elliander@elliander-ubuntu:~$ sudo linux 32 /home/elliander/Desktop/Creatures3/dockingstation.run


and one program then installed fine but now in another program I am getting:

> dirname: missing operand


---

### Post by Yellow Pasque on 2008-11-19
Please mark thread as solved. Also, see this if you ever need 32-bit libraries that aren't available in lib32 packages: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

