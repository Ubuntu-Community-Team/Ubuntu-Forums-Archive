---
title: "log in errors"
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by grizzly451 on 2005-11-22
Hello Everyone,

I am new to using linux.

I have done something so when I try to log in as any account except the root account i get an error that the home directory for that account doesn't exist.  And that most likely nothing will work unless I use a failsafe login using the /root as my base directory.

I can create new accounts without any problems, but when I try to log in as them I get that error everytime.  I have tried creating several different accounts without any success.

Since i have heard that it is not a good idea to continously log in as the root account I was hoping that someone knew of a way to fix this.

If need be I can reformat again.

Thanks for you time

---

### Post by ssam on 2005-11-22
how are you creating the new accounts?

do you have /home on a seperate partition?

do you know of anything you may have done to cause this?

---

### Post by grizzly451 on 2005-11-22
What I was trying to say was that I can only log in as root.  When I am logged in as root I can create new user accounts, but after I create the new account, log out as root, and then try to log in as the new account I get the home directory doesn't exist error.  It also does that with the user account I was using before this started happening.

I was basically looking around the user accounts menu, trying to get used to the new layouts and such, I was trying to figure out how to make it so my user account could delete a document on the desktop without logging in as the root.

Thanks for the quick reply

---

### Post by Graham_Thomson on 2005-11-22
If you go into /home do the relevant home folders actually exist for the accounts you created?

---

### Post by grizzly451 on 2005-11-22
Yes when I go to the /home directory I can see the folders for each account that I create.

---

### Post by Graham_Thomson on 2005-11-22
If you ls -l who's listed as 'owner.group' for the folders?

---

### Post by ssam on 2005-11-22
do they have the correct permissions?

can you post the output of

```
ls -al /home
```

---

### Post by grizzly451 on 2005-11-22
total 16
drwxr--r--   4 root root 4096 2005-11-22 08:55 .
drwxr-xr-x  22 root root 4096 1903-12-31 23:31 ..
drwx------   3 griz griz 4096 2005-11-22 08:42 griz
drwxr-xr-x   2 1001 root 4096 2005-11-22 08:55 test



That is what I get.

---

### Post by grizzly451 on 2005-11-22
when I do: ls -l

total 24
drwxr-xr-x  3 griz 1000 4096 2005-11-18 17:38 Automatix
-rw-r--r--  1 root root  176 2005-11-21 14:07 automatix.log
-rw-r--r--  1 root root  175 1903-12-31 23:32 dbootstrap_settings
drwxr-xr-x  2 root root 4096 2005-11-21 13:19 Desktop
-rw-r--r--  1 root root 5471 2005-11-21 14:05 frozen.htm

---

### Post by Graham_Thomson on 2005-11-22
I had meant you to run 'ls -l' within the home folder, sorry that wasn't very clear. The output from the 'ls -al /home' shows pretty much the same thing though.

It looks like both the ownership and permissions are wrong for the home folders of both the 'griz' and 'test' accounts.

if you 'cd /home' then 'chown test.test -R test' that should get the test account up and running.

---

### Post by grizzly451 on 2005-11-22
ok, i did: ls -l   from the /home
total 8
drwx------  3 griz griz 4096 2005-11-22 08:42 griz
drwxr-xr-x  2 1001 root 4096 2005-11-22 08:55 test

the test account actually doesn't exist anymore i deleted that one.

but i did the 'chown griz.griz -r griz' with that account and it still does the same thing

---

### Post by Graham_Thomson on 2005-11-22
That's pretty strange. I'll have to go have a think and get back to you - I really would have expected that to be working. Sorry I can't be more help at the moment.

---

### Post by ssam on 2005-11-22
ok, i have an idea.

log out

press ctrl+alt+f1 to get a terminal

log into the command line as your nomal user

```
sudo /etc/init.d/gdm stop
```
to stop x.

```
startx
```

see if that works, or gives a more useful error message

---

### Post by grizzly451 on 2005-11-22
ok, i logged in as my normal user

it did say something about 'no directory, logging in with HOME=/'

did the sudo /etc/init.d/gdm stop

and it ran through a bunch of things like it was starting up and got to 'Starting periodic command scheduler...' and is sitting there

should i just reboot it or let it sit there for a while?

---

### Post by ssam on 2005-11-22
hmm. thats a bit odd

yeah restart and try again.

also maybe you could give the output of

```
cat /etc/passwd | grep griz
```

maybe the home folder is messed up in there.

---

### Post by grizzly451 on 2005-11-22
ok, i left that screen (ctrl+alt f8) and went to the (ctrl+alt+f1) screen and entered sudo startx and that booted it back into the gui interface.  Then I tried to logout, and that booted me over to the terminal screen.

At the terminal screen i can see what it did after i typed the 'sudo startx' and one of the things it has it a

X: warning; process set to priority -1 instead of requested priority 0

then it has some lines about the version its loading, etc. and then it lists some files it is skipping

/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o
same....................................../libGLcore.a:m_debug_norm.o
same....................................../libGLcore.a:m_debug_xform.o
same......................./libfb.a:fbmmx.o

saying No symbols found

then it lists warnings about font renderer for some fonts being already registered at priority 0

finally it says

AUDIT: the date and time X: client 6 rejected from local host

now it is sitting at the prompt

i rebooted from there

---

### Post by grizzly451 on 2005-11-22
My department at work is calling it quits for Thanksgiving break at noon today, so that pretty much means I will be offline until Monday the 28th, if anyone has any ideas on this please post and I will try it when I get back on Monday.

Like I said I can always reformat it if I need to, if most of you think that would be the best thing for me to do I have no problem doing it.  

I was told not to stay logged in as root so I wouldn't mess up the system by changing some setting or file.  But I seem to have to no problem doing that outside of root as a normal user. haha

I pretty much expected these kind of problems at first since I just started using linux on a mac.  Helps me learn a lot if nothing else though.


Thanks for you help in advance.

---

