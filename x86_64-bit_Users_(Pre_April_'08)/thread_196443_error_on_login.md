---
title: "error on login"
date: 2006-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hg80 on 2006-06-14
i tried to install quake 4 on my 64bit platform and also tried to install Nvidia-glx and Nvidia settings and upon a restart when i log in i get an error telling me the session lasted 10 seconds and to try failsafe mode, so i have and still i dont know where the problem lies
I have installed libSDL needed for quake under 64bit and i complained about Nvidia-glx so i installed that and upon restarting i got the error any help as im new linux 
Hg

---

### Post by dabang on 2006-06-14
That's curious, the same error appeared on 5.10. Maybe this will help you:

[http://www.ubuntuforums.org/showthread.php?p=644492#post644492](http://www.ubuntuforums.org/showthread.php?p=644492#post644492)

(Look for my post in this thread.)

---

### Post by Hg80 on 2006-06-17
thanks but didnt work so i re-installed which wasnt a huge problem as the install was only a day old

---

### Post by John Jason Jordan on 2006-06-18
[QUOTE=Hg80]thanks but didnt work so i re-installed which wasnt a huge problem as the install was only a day old[/QUOTE]
The problem you experienced is very common. Next time it happens it may be after you have invested a lot of time in your system, so you won't want to reinstall. Luckily, the problem is really easy to fix. Print out the following and keep it handy.

The problem is a file called .ICEauthority. (Note the dot in front of it -- that makes it invisible, so if you need to see it you need to turn on Show Invisible Files.) For some reason the .ICEauthority file gets corrupted and gives that "your session lasted less than ten seconds" error message. But every time you log in a new .ICEauthority file is automatically created anew. So all you have to do is delete it. However, you can't delete it until you get logged in, right? Wrong. You can delete it, you just have to do so from the command line. So you do this, except where I have jjj (my username) you put your username:

	Exit X (Ctrl-Alt-F1)
	.ICEauthority is in /home/jjj, so first make sure you are in that folder
        Then just do “rm .ICEauthority”
	A new one will be recreated upon logging in, so it won’t hurt to delete it
	To go back to X do Ctrl-Alt-F7
	Log in as usual

I keep these instructions in a document I call my "CheatSheet" which is a plain text document that I can open with Gedit. I also have a paper copy in my backpack.

---

### Post by Hg80 on 2006-06-18
Thanks again

---

### Post by Hg80 on 2006-06-18
[QUOTE=Hg80]Thanks again[/QUOTE]

Well it just happened again to me, and i done the above before i logged in in X i pressed Ctrl-alt-f1 and then logged in went and deleted the file and still it wont allow me to login under x so some one have any ideas as im back to using windows till this is sorted

---

### Post by John Jason Jordan on 2006-06-19
[QUOTE=Hg80]Well it just happened again to me, and i done the above before i logged in in X i pressed Ctrl-alt-f1 and then logged in went and deleted the file and still it wont allow me to login under x so some one have any ideas as im back to using windows till this is sorted[/QUOTE]
Sorry to be so long responding. Decided to upgrade to Dapper. BIG HASSLE!! It has taken me the past 24 hours to get it running!

Regarding your problem, are you sure you removed .ICEauthority? Reboot Ubuntu, when it gets to the login window, do you still have the "your session lasted less than 10 seconds" error message? If so, go back to the shell (Ctrl-Alt-F1) and do a "ls" command to see what is there. You could also try "slocate .ICEauthority" to see if it is hidden someplace else. Also, I think you have to use sudo to delete it.

Try again and then post back. If the above doesn't work, I'm out of ideas, but maybe someone else will have another idea.

---

### Post by Hg80 on 2006-06-20
i have posted the error code here, this may help you
[http://ubuntuforums.org/showthread.php?t=199950](http://ubuntuforums.org/showthread.php?t=199950)

---

