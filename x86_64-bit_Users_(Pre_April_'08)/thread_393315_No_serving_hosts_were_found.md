---
title: "No serving hosts were found"
date: 2007-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by bradweiser on 2007-03-25
I tried installing the Nvidia drivers (NVIDIA-Linux-x86-1.0-9755-pkg1) and am now having some problems. I am running Ubuntu 6.10 on a Compaq Presario V6110CA.

My system boots, gets all the way through the basic load & initialization sequence (Nvidia splash screen displays too), tries to put up a user login screen, then puts up an error dialog with the message "No serving hosts were found." 

I've tried searching and I cannot find any information that explains how to correct this problem. 

Does anyone know how do I fix this? Thank you.

---

### Post by bradweiser on 2007-03-27
Okay, I've resolved the "No serving hosts were found" issue. 

To correct this issue I ran recovery mode and then edited /etc/gdm/gdm.custom.conf

I set
[xdmcp]
Enable=false

Then I set
[servers]
0=gdm

I then restarted the computer and ran Ubuntu as I normally would and voila! It worked!

So far it seems like the video drivers are working properly. I'm going to bed so I'll have to verify tomorrow.

There was a usefull thread from which I obtained some useful information.
[http://www.ubuntuforums.org/showthread.php?t=135304&highlight=No+serving+hosts+were+found]("http://www.ubuntuforums.org/showthread.php?t=135304&highlight=No+serving+hosts+were+found")

---

### Post by topsites on 2007-04-25
For Ubuntu Dapper [6.06], I found the above extremely helpful but let me add my knowledge as a remote admin helped, as follows:

Yes, absolutely when it boots watch for that 'hit Esc for boot options' or whatever that pops up at the bottom of the screen with a 1-0 second count-down timer and, well, hit Esc then pick the top-most recovery boot.

Once at the command prompt, do: cd /etc/gdm
Then, run a 'dir' and you should see:  gdm.conf AND gdm.custom-conf

So, ALWAYS back up system files!!!
cp gdm.conf gdm.confORIG
cp gdm.custom-conf gdm.custom-confORIG

In the original files, if you read through bs in gdm.conf it tells you that gdm.custom-conf overrides all, so only need to edit gdm.custom-conf

Now I used pico to edit because it wouldn't let me simply 'edit'
pico gdm.custom-conf

I guess you can use vi as well but I like pico
To exit and save:  Ctrl-X and Yes

I had to reboot, doing a gdm-restart caused another error, but it works now.

One more thing:  It helps to have an Ubuntu Boot OS CD, I hate using the Install CD to get into Ubuntu thou I suppose one could use that.

---

