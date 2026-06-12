---
title: "can't logon - password doesnt work"
date: 2009-08-29
forum: x86 64-bit Users
---

### Post by mkham on 2009-08-29
8.04 HH AMD64 on Acer Aspire 5003Wlmi, 1 gig RAM, Turion ML-32 1.8g Mh
dual boot with XP; Ubuntu on last 5gig

I haven't been able to logon to Ubuntu from 1 1/2 months ago or so. Won't take password- just says wrong. I last used it a month or so before, when I did a number of regular updates.

Now can't find ANY threads related to this problem. Before tried changing a line in the bootup "kernal ...." and added "init=/bin/bash", it didn't work, but I don't see that edit anymore. Not totally sure how that was supposed to work- reboot into passwordless ability? 

After you edit that line + reboot, I have something else about 
"mount / -o rw remount" ENTER  "passwd" ENTER, new password twice, "mount / -o ro,remount" ENTER Ctrl-ALt-Del Haven't tried that.

I've tried older version + no go, booted into (have Kernal 26) recovery mode and entered shell mode to change the password, but that says "give root password for maintenance". Was there something in the updates that could have broken the logon? It seems before the problem the default entry was upper case (without any caplock), now it is lower case.  

Saw something before about creating new user- how does one do that, and could that fix this? I'm fairly sharp but not a Linux programmer, so please be specific or give me links, cause it seems the search function on these forums isn't working.

---

### Post by cariboo on 2009-08-29
Have you tried booting in recovery mode? Once you are at the menu select drop to root prompt. At the prompt type:

```
passwd <user>
```

Where <user> is your user name. You should be asked to enter a password twice. Once you have entered the new password type:

```
exit
```

Then at the menu select Resume, this should take you back to your desktop.

---

### Post by mkham on 2009-08-29
yes, recovery wanted root password also.

So did that init=/bin/bash line addition to KERNAL and give me terminal root prompt

Tried to change password. First time printed letters, after only dark printing but took input

When entered new password it jumped to confirm password after first letter and again on confirming it. If I did 1 letter password got
AUTHENETICATION TOKEN LOCK BUSY

How do I fix this. LINUX isn't supposed to have such grevious basic problems

---

