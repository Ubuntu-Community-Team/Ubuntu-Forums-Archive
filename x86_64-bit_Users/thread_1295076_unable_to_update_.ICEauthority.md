---
title: "unable to update .ICEauthority"
date: 2009-10-19
forum: x86 64-bit Users
---

### Post by a7j_72 on 2009-10-19
Hi ... im new to Linux/Ubuntu...

Last week i tried out for the first time setting a partition aside for ubuntu 9.04 (64-bit)

Everything was great and perfectly smooth until I had to install manually some drivers for an external sound card, which ultimately, I ended up not installing.

Thats when I noticed that in all that mess i had messed up something...
 because now I get the **" unable to update .ICEauthority file"** error message.

This happens _AFTER_ i successfully log in. (notably different from other cases)
I accept the error message and continue normally.

...possibly unrealated (I think it is related) When I hit "Shut down" or "restart",
It does the little "countdown or push the button" thing, 
but It takes me directly to the login screen. 
     I then have to select shutdown again from the lower left side menu.
( I tried 'sudo reboot' and it worked flawlessly)



I have googled other similar problems and tried different variants of :
chown user:user /home/user/.ICEauthority
chmod 644 /home/user/.ICEauthority
exit

but all with no success. 

Thanks in advanced for any help.:popcorn:

---

### Post by a7j_72 on 2009-10-19
Ok... no replies tonight? Ill be back tomorrow morning...

---

### Post by hal10000 on 2009-10-19
The .ICEauthority file should have the permissions set to
chmod 600 /home/user/.ICEauthority

And it should be owned by yourself (not by root or another user, so do
```
sudo chown user:user /home/user/.ICEauthority
```

To come to your soundcard-problem:
Are you sure  that you have to install a driver, and if so, are you sure that is has to be installed manually?
The very most linux drivers come with your system, and the most of those, which are not installed by default can be installed from your repositories simply by using your package-manager.

So maybe it's agood idea to describe your soundcard in detail (manufacturer, chipsets etc.), the steps you made to get it working and the problems that occurred.
With a little luck you may find someone here in the forum who has the same or a similar soundcard to help you.

---

### Post by a7j_72 on 2009-10-20
Ill try that right now, then reboot... thanks.

---

### Post by a7j_72 on 2009-10-20
hal10000,
thanks for your help... 
but I has not worked...

sudo chown aj:aj /home/aj/.ICEauthority
chmod 600 /home/aj/.ICEauthority
sudo reboot

I still get the update error message after i punch in my login.

In Places>>Home>> (ctrl+H) >> .ICEauthority (properites) >>> Permissions tab.
owner : aj 
access : Read & Write 
(Just to verify settings. seems correct.)


In regards to my soundcard... It was a M-Audio MobilePre USB 2x2chnl which I only had because it was great for portability... It wouldnt autodetect, and synaptic had nothing for it... I googled and figured it wasnt worth my time trying to configure it. So I grabbed a 7.1 internal and, voila... Autodetected.

---

### Post by hal10000 on 2009-10-20
I found a possible solution for your ICEauthority problem on a mac-forum: [http://forums.macosxhints.com/showthread.php?t=14741](http://forums.macosxhints.com/showthread.php?t=14741) (posting #4)

```
sudo chown -R your_username /home/your_username
```

---

### Post by a7j_72 on 2009-10-21
aj@HyperProcessor:~$ sudo chown -R aj /home/aj
chown: cannot access `/home/aj/.gvfs': Permission denied

it seems that when it runs into FOLDER : ".gvfs" it stops due to permission problems.
Could it be that, the folder is in actively under use... therfore it cannot be modified?

If I try to edit .gvfs properties in File Browser... It immediately reverts all changes.

---

### Post by hal10000 on 2009-10-21
> it seems that when it runs into FOLDER : ".gvfs" it stops due to permission problems.
Could it be that, the folder is in actively under use... therfore it cannot be modified?

If I try to edit .gvfs properties in File Browser... It immediately reverts all changes.

I'm not sure about this since i don't use gnome, but i think the .gvfs folder in your homedirectory has something to do with the gnome virtual file system.
Maybe if you quit gnome and go to the console (STRG-ALT-F2), then login and then do
```

sudo killall gdm
sudo chown -R your_username /home/your_username

```
again, it may work (the killall gdm is just to ensure that no more gnome programs are running, i assume you use gdm as your display manager)

---

### Post by a7j_72 on 2009-10-22
No luck...
Yes, Gnome is my display manager... 
(out of curiosity... what does kubuntu use?)
 I have attempted entering the code into Console (ctrl+Alt+F2)...
but I still get the same "unable to update .ICEauthority file" error.

afterwards, I even attempted this on DROP TO ROOT SHELL mode...
to make sure gdm was not interfering... but still?:confused:

 I am increasingly convinced that [shutdown&reboot taking me to the main login screen], have something to do with this same problem... What do u think?

---

### Post by hal10000 on 2009-10-22
> (out of curiosity... what does kubuntu use?)

There are three display managers, xdm, gdm and kdm. You can use any of them independ of the desktop environment you use, but in kubuntu kdm is installed by default.

A last idea: Just rename the .ICEauthority file and see what happens:
```
 mv /home/yourname/.ICEauthority /home/yourname/.ICEauthotity.backup
```

---

### Post by a7j_72 on 2009-10-22
I will rename both,
.ICEauthority
and 
.Xauthority

from what I've read, this might be a problem too...
this should lead to automatic re-creation of the 2 files...:)

---

### Post by a7j_72 on 2009-10-22
I have renamed both... 
verified with  **ls -a ~**

no files named 
.ICEauthority
.Xauthority
exist.

only 

.ICEauthority.backup
.Xauthority.backup

Error is still present. :( lol

---

### Post by a7j_72 on 2009-10-22
If it helps...

ls -la .ICEauthority 
               gives me back a -rw (negative for user read and write permissions)
-rw------- 1 aj aj 1050 2009-10-13 15:07 .ICEauthority
but it does show me as the owner for .ICEauthority, i think?


I tried ...

 sudo chown +rw .ICEauthority 

and time after time it remains the same...
would I get a different result by dropping into root shell?

---

### Post by hal10000 on 2009-10-22
I had the same error some years ago and i could fix it, but i can't remember how.
I guess it has someting to do with the files in **/tmp/.ICE-unix** and with the file /home/yourname/.DCOPserver_yourthostname__0
Maybe it works if you rename this file

---

### Post by a7j_72 on 2009-10-22
Thnx for the pointer... I will look at it in-depth tommorrow... I need to catch some sleep, Its almost 0400hrs where I live.

---

### Post by a7j_72 on 2009-10-22
> **hal10000 said:**
> I had the same error some years ago and i could fix it, but i can't remember how.
I guess it has someting to do with the files in **/tmp/.ICE-unix** and with the file /home/yourname/.DCOPserver_yourthostname__0
Maybe it works if you rename this file

(username)@(computername):~$ ls -al /tmp/.ICE-unix
total 8
drwxrwxrwt  2 root root 4096 2009-10-22 13:21 .
drwxrwxrwt 13 root root 4096 2009-10-22 13:23 ..
srwxrwxrwx  1(user)(user)   0 2009-10-22 13:21 3284

*******************
(username)@(computername):~$ ls -al /home/user/.DCOPserver_user__0
ls: cannot access /home/user/.DCOPserver_user__0: No such file or directory

ls -al /home/user/
reveals that there is no file similar to .DCOPserver...

*******************

---

### Post by a7j_72 on 2009-10-24
bump... does anybody have any other clues as to what I should do?:confused:

---

### Post by Michael.Palone on 2009-10-26
[http://ubuntuforums.org/showthread.php?t=1021106](http://ubuntuforums.org/showthread.php?t=1021106)

I don't know if you're still having this problem but I was and this fixed it for me. The second post has instructions.

---

### Post by a7j_72 on 2009-10-26
Yes, still having this problem... Ill update you if it worked. Thanks.

---

### Post by a7j_72 on 2009-10-26
Did not work...
it might help to add...

username@computername:~$ ls -l .ICEauthority
-rw------- 1 username username 1050 2009-10-13 15:07 .ICEauthority

It doesn't seem to be an ownership problem... its not root that owns it, its my username.

I dont know too much about typing these codes in. But It seems that chown is used to revert ownership back to user (assuming it was incorrectly owned by root.), right?

Therefore, my problem lies somewhere else... it just seems that nobody else is having this issue... I have not been able to find a forum (under any distro) that is having this issue.

I have also tried renameing it without success.(shown on previous posts)

---

### Post by a7j_72 on 2009-10-27
bump...  anyone?

---

### Post by hal10000 on 2009-10-27
> (username)@(computername):~$ ls -al /tmp/.ICE-unix
total 8
drwxrwxrwt 2 root root 4096 2009-10-22 13:21 .
drwxrwxrwt 13 root root 4096 2009-10-22 13:23 ..
srwxrwxrwx 1(user)(user) 0 2009-10-22 13:21 3284

There has to be at least one more file in this directory, here is my own:
```

ls -la /tmp/.ICE-unix/
insgesamt 20
drwxrwxrwt  2 root          root           4096 2009-10-26 09:26 .
drwxrwxrwt 14 root          root           16384 2009-10-27 00:23 ..
srwx------  1 myusername    myusername     0 2009-10-26 09:25 5162
**srwx------  1 myusername    myusername     0 2009-10-26 09:26 dcop5506-1256545590**

```

> (username)@(computername):~$ ls -al /home/user/.DCOPserver_**user**__0
ls: cannot access /home/user/.DCOPserver_**user**__0: No such file or directory


If you look at the bold part you see a small but deciding error. It has to be 
```

ls -al /home/user/.DCOPserver_**yourhostname**__0

```

"yourhostname" is your computer's name.

This is a small text file and the content has to be like this (it is my own)
```

cat ~/.DCOPserver_myhostname__0
local/myhostname:/tmp/.ICE-unix/dcop5506-1256545590
5506

```
If you look at this content and compare it to the listing of my own /tmp/.ICE-unix directory, you will see that one line of this file refers to the socket-file in /tmp/.ICE-unix

But because you don't have this socket-file in /tmp/.ICE-unix i guess that there is something wrong with your DCOP configuration or something similar.

Maybe you can find some hints to this error in your /home/yourname/.xsession-errors file, but i have no idea how to fix this.

I recommend you create a new user, make him member of all the groups which your current user is a member. Then you can copy all important files from the home directory of your current user to the home directory of the new user and make the new user the owner of all these files (with chown -R ) and start over with that new user.
I'm sorry to have no better idea.

---

### Post by a7j_72 on 2009-10-28
hal1000, that actually sounds like a great idea... 
quite thankful for your help.

ps: 
"(username)@(computername):~$ ls -al /home/user/.DCOPserver_**user**__0"
would never work... because as 
"ls -al /home/my_username/"   reveals, there is no file starting with .DCOPserv...
It just seems to be missing.


I will be working on a new user and its permissions... I will return to 
(hopefully all goes well) close the thread, or ask for more help... 
thanks.

---

### Post by a7j_72 on 2009-10-28
[SIZE=2]UPDATE: problem has been **resolved** by creating a **new user**...[/SIZE]
All groups were automatically identical. Did not have an issue.

When asked to chose a main group, I had not yet created one identical to my user-name...
so not knowing what to choose and not wanting to select my old one, I chose "admin"](*,)

so while transfering files to the new user, I had to use ' sudo mv ' at the terminal due to permission problems.  after transfering all my music and files, I noticed some didn't have the proper permissions to read/write. This is due to me not selecting my old Main Group as my current Main group. ](*,)

I realized this **_after_** setting all the new permissions to "admin" group,
heres my example:


[I]~$ sudo mv /home/oldusername/Desktop/ubuntupocketguide-v1-1.pdf            /home/newusername/Desktop/ubuntupocketguide-v1-1.pdf

~$ sudo chown new_username:admin Desktop/ubuntupocketguide-v1-1.pdf[/I]


 so If I can get away with this I wont change the group;). (even though Its not hard.)
hope that this will not cause any problem... right?

---

### Post by hal10000 on 2009-10-28
> When asked to chose a main group, I had not yet created one identical to my user-name...
so not knowing what to choose and not wanting to select my old one, I chose "admin"

You should create a group identical to your new_username and make this to your main group.
The new user should also be a member of these groups:
admin (if you want to use the sudo command)
adm (if you want to view logfiles)
dialout (if you want to use a serial modem or other hardware which is connected via serial bus)
cdrom
audio
video
plugdev (you will need this if you want to mount usb sticks or similar devices as a normal user)
fuse (if you want to mount your windows partition as a normal user)
lpadmin (if you want to administrate your printers via cups)
sambashare (to create usershares with samba)
vboxusers (if you have virtual box installed)

After you copied (or moved) the files you need from your old user to the new users homedirectory, you should also make all files in the new users homedirectory belong to this new user and the new users main group, so do:
```

sudo chown -R new_username:new_username /home/new_username/*

```

---

### Post by a7j_72 on 2009-10-28
These groups do not exist. As far as I could remember I don't recall ever seeing them.

[I]adm
dialout 
cdrom
audio
video
plugdevuser
vboxusers[/I] 

however I could my audio settings are correct, video can play
USB sticks and cdrom auto-mount perfectly fine.
Does the fact that they are missing, mean something might not work properly?

my new-*username* was automatically added to ALL other groups you listed.

I have changed successfully changed my *usergroup* to match my *username*, using *chown -R*

---

### Post by hal10000 on 2009-10-28
> however I could my audio settings are correct, video can play
USB sticks and cdrom auto-mount perfectly fine.
Does the fact that they are missing, mean something might not work properly?

No, if they are working, then everything is o.k.
Maybe i'm not up-to-date with the group-settings on the newest ubuntu-releases.

---

### Post by a7j_72 on 2009-10-29
Once again, thanks for you time and patience.

---

### Post by jcpeart on 2009-10-30
I solved my inability to update .ICEauthority by using nautilus to change the permissions for .ICEauthority in my home directory so that all users have read and write permissions for the file.  It works well now.

Jim

---

### Post by shushek on 2009-11-02
Hello All, I'm a not not a new user to Ubuntu, but was using is every now and then since 8.04 was introduced. Well, i also ran into trouble with this issue you all were discussing. I tried almost all the tips that you people provided. But no go. Also I was getting the following error along with the "ICEauthority update" error.
---------------------
Nautilus could not create the required folder "/home/ogamico/Desktop".
Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.
---------------------
So i believe it has to do more than that. So i run around with a few forums and eventually got my issue resolved by killing the gdm session from the terminal.

>gdm-stop

Don't know if that is the only thing that was causing the 
problem, it gave me quite a rubbing. I thought it might help someone if they are unsuccessful in getting it fixed with the above tips. 

Once again, just a newbie to the penguin community. Apologies for my mistakes if any.

-----------------------------
Current system conf: Ubuntu Studio 9.10 512 MB RAM, AMD Athlon X2 3600+ 160GB.

---

### Post by aumshantih on 2009-11-07
> > sudo gdm-stop

This command worked beautifully for me.   I was following Psychonaut's seperate /home partitition instructions:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

On ubuntu 9.10 with ext4 file systems.  I had to add in UUID's in the fstab to get the /home partition to mount properly, but I kept getting the Ice Authority error.

After using the command, I was forced to login again, but then my permissions to my /home directory were set properly, and I was able to change them.

Thanks!

---

### Post by ebozzz on 2009-11-08
I was able to resolve my issues using the following and substituting the actual user name where the word user appears in the code..... 

```
sudo chown *user*:*user* /home/*user*/.ICEauthority
```

After that I entered...

```
chmod 644 /home/*user*/.ICEauthority
```

I then used the method to makes the necessary changes for all of my remaining users with one exception. Use the sudo command prior to the chmod code...

```
sudo chmod 644 /home/*user*/.ICEauthority
```

Every user now owns that file in their home folder.

---

