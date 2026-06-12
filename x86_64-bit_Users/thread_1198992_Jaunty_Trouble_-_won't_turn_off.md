---
title: "Jaunty Trouble - won't turn off"
date: 2009-06-28
forum: x86 64-bit Users
---

### Post by Dr Noam on 2009-06-28
Hi, I've had a new problem since I upgraded my wubi-downloaded 64-bit ubuntu to Jaunty Jackalope. Sometimes it doesn't shut down properly - the shut down puts the computer in a strange sleeping mode, with the DOS-like black screen and the ^@ prompt in the corner. I can only revive it by ctrl-alt-del to restart, then I have to turn it off again. Any suggestions? 

I thought of reinstalling Jaunty, not sure how to do that without completely uninstalling and reinstalling ubuntu.

Thanks!

---

### Post by mariuszsynowczyk on 2009-07-26
Open terminal and write:

sudo update-rc.d -f sendsigs remove && sudo update-rc.d sendsigs start 80 0 6 .

---

### Post by John Jason Jordan on 2009-07-26
> **mariuszsynowczyk said:**
> Open terminal and write:

sudo update-rc.d -f sendsigs remove && sudo update-rc.d sendsigs start 80 0 6 .

Can you explain what those commands do?

---

### Post by Raffles10 on 2009-07-26
> **mariuszsynowczyk said:**
> Open terminal and write:

sudo update-rc.d -f sendsigs remove && sudo update-rc.d sendsigs start 80 0 6 .

It's never a good idea to post a string of commands without an explanation, only a fool would run it.

Especially with root privileges... [-X

---

### Post by Raffles10 on 2009-07-26
> **Dr Noam said:**
> Hi, I've had a new problem since I upgraded my wubi-downloaded 64-bit ubuntu to Jaunty Jackalope. Sometimes it doesn't shut down properly - the shut down puts the computer in a strange sleeping mode, with the DOS-like black screen and the ^@ prompt in the corner. I can only revive it by ctrl-alt-del to restart, then I have to turn it off again. Any suggestions? 

I thought of reinstalling Jaunty, not sure how to do that without completely uninstalling and reinstalling ubuntu.

Thanks!

I've had shutdown problems with the 'Fast User Switch Applet' using it just loads the login screen...maybe unrelated to your problem but I've found that using poweroff does the job:

```
sudo poweroff
```

for more information:

```
man poweroff
```

---

### Post by bagle on 2009-07-26
well.......
this could have been caused by a bad download.
maby a md5 could work (if wubi has md5sums:confused:)

for now try this
```
sudo shutdown 00:00
```
shutdown simply powers down the computer.
```
sudo shutdown -r 00:00 
```
 this one restarts the computer.
```
man shutdown
```
tells you about the command shut down.

mabey when you click the shut down button the wrong commmand is issued or the shutdown scripts are messed up.:twisted:

---

### Post by John Jason Jordan on 2009-07-26
I have used poweroff in the past, but not lately. I'll try shutdown as well to see if anything interesting happens.

My problem is related, but not exactly the same as Dr Noam's. (He couldn't be Noam Chomsky, could he? Nah, Chomsky lives in Massachusetts.)

I have been using Ubuntu x86_64 since May, 2005, always dist-upgrading. Using two different laptops I have frequently had problems with shutdown, but never as serious as after the Jaunty upgrade.

Since the Jaunty upgrade it appears to completely shut down (screen is blank), but the wireless and bluetooth lights are still lit up - my clue that it didn't completely shut down. At that point I just hold the power button down until all the lights go out.

A couple of weeks ago while at the university I did this. Then I went to class, which lasted two and a half hours. When class was over I put my books into my backpack and noticed that the computer was hot. I opened the lid. There were no lights lit up. I tried to boot it, but the battery was completely dead. It had been on the mains previously, so the battery would have been completely charged up at the beginning of class.

Since that event I have had two other incidents where it appears to be completely shut down and all the lights are out, but something is still running. I now must physically remove the battery when I shut it down just to make sure that it is really shut down.

The computer is a Thinkpad T61. Jaunty is completely up to date.

I never had anything like this with Intrepid or Hardy. Does anyone have any idea what might be going on? Any suggestions are welcome!

---

### Post by mariuszsynowczyk on 2009-07-27
The main reason for this is because of a in the update-rc.d script:
Quote 'man update-rc.d':

"..Obviously, therefore, the default stop sequence number should be 80.  
Defaulting to 20, as update-rc.d does, is an old bug .."

It defaults setting the simlinks to 20. As a result, the sendsigs init-script tries to kill all remaining processes while some network filesystems (nfs, cifs, smb) are not yet umounted and/or the networking is not yet stoped etc..

Those symlinks (/etc/rc0.d/S20sendsigs and /etc/rc6.d/S20sendsigs) must be simply renamed to put them on '80', resulting in /etc/rc0.d/S80sendsigs and /etc/rc6.d/S80sendsigs.
This should fix this (it did for me reproducable):

Copy&paste this code in your terminal (all in one line):
sudo update-rc.d -f sendsigs remove && sudo update-rc.d sendsigs start 80 0 6 .

(The last . (dot) is part of the code!)

---

### Post by John Jason Jordan on 2009-07-28
> **mariuszsynowczyk said:**
> The main reason for this is because of a in the update-rc.d script:
Quote 'man update-rc.d':

"..Obviously, therefore, the default stop sequence number should be 80.  
Defaulting to 20, as update-rc.d does, is an old bug .."

It defaults setting the simlinks to 20. As a result, the sendsigs init-script tries to kill all remaining processes while some network filesystems (nfs, cifs, smb) are not yet umounted and/or the networking is not yet stoped etc..

Those symlinks (/etc/rc0.d/S20sendsigs and /etc/rc6.d/S20sendsigs) must be simply renamed to put them on '80', resulting in /etc/rc0.d/S80sendsigs and /etc/rc6.d/S80sendsigs.
This should fix this (it did for me reproducable):

Copy&paste this code in your terminal (all in one line):
sudo update-rc.d -f sendsigs remove && sudo update-rc.d sendsigs start 80 0 6 .

(The last . (dot) is part of the code!)

OK, I ran the code as above. It appeared to run correctly, changing the 20 to 80. But when I shut down I got the same behavior as before. That is, the GUI disappears, but the wireless and bluetooth lights are still on. Linux is not completely shut down. I have to hold the power button down to shut it down completely.

---

### Post by Obnoticus on 2009-07-30
I'm having the same problem too - I believe it's related to having an Intel wireless card.  For some reason the wireless card would not shut off and this in turns hangs the entire system upon shutdown.

I think there are other threads that mention this problem... I haven't been able to find them again though

---

### Post by John Jason Jordan on 2009-07-31
> **John Jason Jordan said:**
> OK, I ran the code as above. It appeared to run correctly, changing the 20 to 80. But when I shut down I got the same behavior as before. That is, the GUI disappears, but the wireless and bluetooth lights are still on. Linux is not completely shut down. I have to hold the power button down to shut it down completely.

I wish I had never run that code. Before I could not get Jaunty to shut down completely. Now not only does it not shut down completely the same as before, but I am getting random lockups. Running that code is the only difference, nothing else has changed.

I desperately need to undo that command. Unfortunately, I have no idea what it actually does or how to rewrite it to undo what it did. This is the command:

sudo update-rc.d -f sendsigs remove && sudo update-rc.d sendsigs start 80 0 6 .

Would it undo the effects of the command to change "80" to "20" and run it again?

---

