---
title: "Can't boot ubuntu-GDM could not write to your...."
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubuntubrian on 2006-04-07
I had been working in Naultilus as root and later upon restarting got:
"GDM could not write to your authorization file.  This could mean your
> out of disk space [I'm only using 5.2G out of 30G] or that your
> directory could not be opened for writing.  In any case, it is not
> possible to login.  Please contact your systems administrator." 
I have read all that is on this forum as well as other lists and I know it is not a full disk issue as I have 10GB on the Ubuntu partition alone. I have change ownership of .ICEauthority and /tmp from OSX as I have the Ubuntu volume mounted with Ext2FS. No problem there. The issues that I see on other lists to resolve the error seem specific to non-ppc installations. I can run a rescue disk or boot into rescue mode (I assume)but not failsafe terminal or failsafe gnome. I don't know what to do after I have a rescue mode going.
any help?

---

### Post by ubuntubrian on 2006-04-07
I found this, is it relevant?
When the GDM started the /home/username dir could not be used by username.

Solution was to
sudo chown -R 0755 username:username /home/username
sudo chown -R 0755 username:username /home/username/extraspace1
sudo chown -R 0755 username:username /home/username/extraspace2
sudo chown -R 0755 username:username /home/username/extraspace3

GDM could then start and write .files

When username is created with /home/username dir then
if dir username exists
chown /home/username and all mounts under it to be correct ownership.

---

### Post by Mustard on 2006-04-07
I suspect that your .Xauthority and .ICEauthority files have been corrupted and are now owned by root.  You said you looked at one of these, but have you looked at both? Try this in terminal..

```
ls -al .*authority
```

See if these files are owned by root.

The output of this command in my terminal is this...

```
mustard@slave:~$ ls -al .*authority
-rw-------  1 mustard mustard 5135 2006-04-08 09:17 .ICEauthority
-rw-------  1 mustard mustard  165 2006-04-08 09:17 .Xauthority

```

I believe you can just remove them entirely (if they are owned by root) and new files will be created when you log in.

What you have posted above, looks like it would work, but it seems like hitting the problem with a sledgehammer.  It's certianly a generalised solution, but I wonder whether everything in the $HOME directory is necessarily supposed to be owned by the user.  There could be special cases where this is not the best solution (not that I know of any special cases though).  I would be cautious in using it, it what I am trying to say really.

---

### Post by ubuntubrian on 2006-04-07
Thanks for the reply. While trying to devine a solution on my own and info from lists I got another message when trying to log in:
"Home directory has incorrect permissions and is being ignored. File should be owned by user and have 644 permissions."

silly me-I changed the owner ship to me (no difference) and that made no difference so I changed permissions to 644 from 755. That got another error at log in that:
"your home directory is listed as /home/me but it does not apper to exist. I have changed the permissions back to 755 and changed ownership of .Xauthority to me from root. I'll try again to log in and see what I get. I'll let you know. Thank you again and thatnks for the caution.

---

### Post by ubuntubrian on 2006-04-08
Well. things have not improved at all. I made the changes and now get a message "your home/.dmrc file has incorrect permissions..... file should be owned by user and have 644 permissions."
I changed the permissions and made me the owner but no help. When I click OK I get the same "GDM could not write...."
I am at a loss-which is easy for me! I can access all my files  from OS X but I would like to get my email from evolution in Ubuntu. 
Any ideas how to correct this problem? I really think it is an issue of permissions and not disk space.
Thanks

---

### Post by ubuntubrian on 2006-04-08
I should add that what I mean by "no help" is that I get the same message re: home/.dmrc" permissions also.

---

### Post by Mustard on 2006-04-08
[QUOTE=ubuntubrian]I should add that what I mean by "no help" is that I get the same message re: home/.dmrc" permissions also.[/QUOTE]

This is what my .dmrc shows up as..

```
mustard@slave:~$ ls -al .dmrc
-rw-------  1 mustard mustard 24 2006-04-02 20:13 .dmrc

```

It has rw set for user only. If thats relevant.

This is the permissions for my actual /home/mustard folder..

```
drwxr-xr-x  134 mustard mustard  8192 2006-04-08 13:58 mustard

```

Can you show your ls -al output to compare?

---

### Post by ubuntubrian on 2006-04-08
Thanks again for helping Mustard!
Here's what I've got:
-rw-r--r--    1 brianoke 1000           24 Apr  1 06:27 .dmrc

drwxr-xr-x   90 brianoke 1000         4096 Apr  7 20:23 brianokeefe

This does not seem right although the error when logging in was that the permissions for .dmrc should be 644 and according to my handbook this is 644. Yours, however is not. Also, what are these 1000's? They're all over my directories:

UNTITLED/home/brianokeefe] brianoke% ls -al
total 335148
drwxr-xr-x   90 brianoke 1000         4096 Apr  7 20:23 .
drwxr-xr-x    3 brianoke wheel        4096 Oct 15 17:41 ..
drwx------    2 1000     1000         4096 Sep 23  2005 .3ddesktop
drwx------    2 1000     1000         4096 Sep 11  2005 .AbiSuite
-rw-r--r--    1 root     1000         6148 Oct 18 14:04 .DS_Store
-rw-------    1 brianoke 1000            0 Apr  7 12:20 .ICEauthority
-rw-------    1 root     wheel        1199 Sep 22  2005 .ICEauthority.bak
drwx------    2 1000     1000         4096 Apr  7 07:23 .Trash
-rw-------    1 brianoke 1000            0 Apr  7 15:58 .Xauthority
drwxr-xr-x    2 1000     1000         4096 Feb  4 17:51 .albumShaper
-rw-r--r--    1 1000     1000          140 Dec 16 10:26 .appletviewer
drwx------    2 root     wheel        4096 Aug 30  2005 .aptitude
-rw-r--r--    1 1000     1000           24 Apr  6 07:17 .aspell.en.prepl
-rw-r--r--    1 1000     1000           58 Apr  6 07:17 .aspell.en.pws
drwxr-xr-x    2 1000     1000         4096 Apr  7 09:39 .avidemux
-rw-------    1 1000     1000        14499 Apr  7 12:00 .bash_history
-rw-r--r--    1 1000     1000          414 Aug 25  2005 .bash_profile
-rw-r--r--    1 1000     1000         2044 Aug 25  2005 .bashrc
drwxr-xr-x    7 1000     1000         4096 Feb 25 19:48 .beagle
drwxr-xr-x    2 1000     1000         4096 Dec 26 18:37 .cddbslave
drwx------    4 1000     1000         4096 Nov  9 16:05 .config
-rw-------    1 1000     1000           67 Nov  9 15:52 .directory
-rw-r--r--    1 brianoke 1000           24 Apr  1 06:27 .dmrc
-rw-r--r--    1 1000     1000        21472 Oct 17 10:27 .dvdriprc
 for example.

I used Apple's disk utility and see that my Linux partition is completely full and I should have checked that before-I just couldn't believe it. I'll try to copy some files to a cd and then try logging in but now that I've totally screwed up permissions!
I checked the Linux disk for directory sizes and after my home directory, root, usr and var are  the largest.
I will backup some directories and delete some files and see where that gets me. I could change permissions of .dmrc to what you have and seeif that helps.

---

### Post by ubuntubrian on 2006-04-08
I have copied all my photo and music files to a USB HD and deleted those directories entirely. I changed permissions of home/.dmrc to :
-rw-------

Now I can only hope!!
It seems to that my root/>trash directory is packed. How do I safely empty it?
thanks

---

### Post by Mustard on 2006-04-08
I assume since its in the trash that its not needed, so I guess you could cd into that folder and use the rm command to delete the files.

```
sudo -i
#get a root prompt in terminal
```

```
cd /root/.trash
#change directory to /root/.trash
```

```
ls -al
#list the contents of this directory to see how
#many files you have in there
```

```

rm /root/.trash/*

#Probably the safest option (above) is to explicitly state 
#the directory you want to delete stuff from
#You could use this one below if you ar
#USE CAUTION HERE, the rm is command permanently deletes files
#there is no way to restore them, so don't make a mistake and delete 
#the wrong stuff

```

If you get a 'argument is too long' error when using the rm command, you are going to have to try deleting them a bit at a time (using different wildcard arguments) until you get rid of a large chunk of the files, then you can try the * wildcard again to finish off the process.

---

### Post by ubuntubrian on 2006-04-08
Thanks for the advice and commands. I have been able to log in as root into Ubuntu but not as myself. Here's a history of what I have done so far. Obviously changing the permissions in the first place was a bad mistake and I really needed to empty the trash! anyway, the saga of getting to login as root:
After removing about 4 GB of stuff I tried to log in but got the same error message

"Your home/.dmrc file has incorrect permissions and is being ignored. File should be owned by user and have 644 permissions."
I couldn't log in but kept getting returned to the login screen so I logged in as failsafe terminal and changed permissions on the .dmrc file as you have them in your post. then I tried to startx but got:

"xauth: timeout in lockiing authority file/home/brianokeefe/.server.6879
xauth: /tmp/.gdm66wd2cnot writable, changes will be ignored
xauth: error in locking authority file/tmp/.gd....
x: user not authorized to run x server, aborting
xlib: connection to".0.0"refused by server
xlib" no protocol specified giving up
xinit: unable to connectto x2server"

So I tried "sudo start x":
and got the same xauth: errors plus:

"fatal server error:
server is already active for display 0
if this server is no longer running, remove/tmp/.X0-lock"

so I removed /tmp/.X0-lock and sudo start x worked and I logged in as root and have access to all files. No internet capability though even though network is up and running. I'm not surprised as it took a lot to get networking to function initially.
 So I removed .Xauthority and created new .Xauthority and changedchanged permissions to brianokeefe.
startx  still won't work with error:

"timeout in locking
home/brianokeefe/.serverauth.5602
x: usernot authorized to run x server, aborting
couldn't get a filedescriptionreferringto the console"

So I wonder if I should chown /home/brianokeefe/.serverauth.54.
 as well as . serverauth.41 and .server.56 and .server.94 as these files 
now have user and group owned by root. I didn't change the permissions.

I decided to chown .ICEauthority to brianokeefe and try to startx again as me:

"xauthtimeout in locking authoriy file/home/brianokeefe/.serversuth6782
xauth: error in locking authority file/tmp/.gdmzvrt
x: user not authorized to run x server"

So this seems to now be a permission issue but I don't know what to do. I am going to check a backup I did a few weeks back and compare permissions of all the files in my home directory-I guess. Is there no "repair permissions" utility like OS X Disk Utility?

---

### Post by Mustard on 2006-04-08
Are you able to login as your normal user in the command line though?

This is my .serverauthxxx permisssions..

```
mustard@slave:~$ ls -al .serv*
-rw-------  1 mustard mustard 50 2006-02-28 08:54 .serverauth.8875

```

I notice I only have one, so I'm not sure why you have so many. :)

I don't know of any repair permissions utility.  I know of a repair option on the install CD, but I don't know what its functions are (I suspect this problem would be outside of its range of functions, whatever they are.  I have never used it.)  I think the install repair option is for gaining access to your system if you have lost your password (at least thats one function I have seen it recommended for).

I'm curious as to whether the system will create new ones if they are absent.  You could, rather than deleting them, or playing around with permissions, use the move command (mv) to move them to another folder temporarily and see what happens.  At least if you just move them out of the way, you can always move them back.

I know with the .Xauthority and .ICEauthority that the system will create new versions if they are absent, as I distinctly recall reading that the answer to the permissions problems with these files was to delete them entirely.

With this in mind I think it might be worth cautiously moving a few files out of your  $HOME folder that are causing problems and see if the system replaces them when you attempt to start up X.

Please try to take into account that I am using just as much guesswork on this issue as you, as I really don't have a great understanding of how X works and what all these files do.  Your system is pretty trashed at the moment though, so on the brightside, it's a perfect time to experiment a bit. :)

I'm also wondering whether you would have more success with starting X with this command too..

```
sudo /etc/init.d/gdm restart
#the above assumes you are not in root
#below should work from root prompt
/etc/init.d/gdm restart
```

---

### Post by ubuntubrian on 2006-04-09
Thanks again. I appreciate your caution and candor which may help me not get further into trouble! Here are the current .serverauthxxx files in my /home directory:
-rw-------    1 root     wheel         153 Sep 22  2005 .serverauth.4178
-rw-------    1 1000     1000           51 Sep 15  2005 .serverauth.5419
-rw-------    1 root     wheel          51 Apr  8 17:06 .serverauth.9405
Which is interesting because there was a file with me as owner that is no longer there. This would indicate that these files are created at login but I am not sure. Anyone out there know?
I'll try the alternate login commands you posted tomorrow as it is 10:30PM here and time for bed.
Any idea on the .dmrc file permissions error? I may have to go to a LUG meeting the next time there is one and see if someone can crack that nut!
Thanks again Mustard and keep the suggestions coming.

---

### Post by ubuntubrian on 2006-04-09
As to your previous ? Mustard, no I cannot login as me from the command line. I just finished moving my .dmrc file out of the way and copying the .dmrc from a backup of a few weeks ago when I could log in. If I can't login with the same ".dmrc" error message then something is really strange and if the .serverauth error comes up again then ? I don't know why there are so many of them other than that they are generated at each login.

---

### Post by ubuntubrian on 2006-04-09
that didn't work. I thought that I would try to login a KDE session as me but I get a "no write access to Home directory". this seems to be a permissions problem with my home directory still so i checled my backup to my current settings and here they are:
Backup-drwxr-xr-x   41 brianoke unknown      1394 Apr  9 11:28 brianokeefe
Current-drwxr-xr-x   88 brianoke 1000         4096 Apr  9 11:19 brianokeefe

I don't know what these 1000's are. I'm checking the permissions from OS X so I suppose that OS X doesn't recognize the "1000" group and just calls it unknown?

---

### Post by Mustard on 2006-04-09
I wonder what would happen if you created a completely new user account (via the command line).  You could then transfer over important files and work from the user account.

---

### Post by ubuntubrian on 2006-04-11
Thanks so much for the input Mustard. I had thought of doing something similar but then i thought that I would contact our local LUG here in Santa Fe. Luckily a couple of people figured out the problem in 4 or so postings and I started to wonder about this myself.
I dual boot and I was accessing my Ubuntu partition from a shell in the other so each time I issued a command to change permissions, or whatever, the user ID from one got pasted into the other and that, of course, doesn't work. Eventually I ran:
sudo chown -R 1000 /volumes/UNTITIED/home/brianokeefe
and 
sudo chown root /volumes/UNTITLED/home

from my OS X partition and all is well, no harm done.
Thanks again. You were right about permissions, just how to correctly change them was in issue.

---

### Post by Mustard on 2006-04-11
[QUOTE=ubuntubrian]Thanks so much for the input Mustard. I had thought of doing something similar but then i thought that I would contact our local LUG here in Santa Fe. Luckily a couple of people figured out the problem in 4 or so postings and I started to wonder about this myself.
I dual boot and I was accessing my Ubuntu partition from a shell in the other so each time I issued a command to change permissions, or whatever, the user ID from one got pasted into the other and that, of course, doesn't work. Eventually I ran:
sudo chown -R 1000 /volumes/UNTITIED/home/brianokeefe
and 
sudo chown root /volumes/UNTITLED/home

from my OS X partition and all is well, no harm done.
Thanks again. You were right about permissions, just how to correctly change them was in issue.[/QUOTE]

I'm glad you worked that one out.  I doubt I would have been able to reach the same solution myself. :)

---

