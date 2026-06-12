---
title: "No Write Access 'ICEauthority'"
date: 2006-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by macminiman on 2006-02-25
OK, well, Ubuntu is great! But I've been installing packages with the Add Applications package manager, and  I don't know if that has to do with my problem. Well, I booted into ubuntu, everything started up fine, and then I came to my login screen, which is controlled by kubntu (I installed kde using apt-get install kubuntu-desktop). I selected GNOME from the session list, and type my username + password. It starts to login, then gave my the grainy screen (which it has never done before), and then came directly back to the login screen. I was confused by this as ubuntu never gave me any trouble before, so I selected KDE from the session list, and gave my username + password. This time, it gave me a error message:

X-server error: No write access to: '/home/craig/.ICEauthority'

Obviously I need to do something about the permissions, but I don't know how to do this in linux, only in osx. I can still get a failsafe terminal emulator, and the real fullscreen terminal, but neither will show the hidden files. Can you guys help me? If so, thanks alot!\\:D/  If not, back to osx only.:cry:

---

### Post by wylfing on 2006-02-25
I am not certain what you mean when you say the terminal won't show hidden files. Does this command work?

```
ls -l .ICEauthority
```

You may be able to remedy the issue by issuing this command:
```
sudo chown craig .ICEauthority
```

Also, if you are using KDE, I have read reports of certain tasks that must be performed as root or else they can aggravate .ICEauthority, one of them being K3B.

---

### Post by macminiman on 2006-02-26
Thanks!
I'll try that as soon as I get back to ubuntu. As for the hidden files, I meant like .gnome, .icons, .ICEauthority, .gimp, and all the files and folders you can't see in your home folder until you select 'Show Hidden Files'. And before I used
```
sudo chmod 755 /home/craig/.ICEauthority
``` but it didn't work.[-( 
Thanks again!

- craig

---

### Post by jdp on 2006-02-26
To show "hidden" files in a terminal, us the **-a** switch with **ls**.  So it'd be **ls -la** to have a detailed list of every file in the current directory.  Or, just **ls -a** to show the full list of files, including hidden ones.  By long standing UNIX default, any file starting with a period indicates a file that shouldn't show up on a regular **ls**.  When using a root terminal, it defualts to showing every file.

---

### Post by r3v3rs3pa on 2006-03-06
ya, i have run into the same problem...
run in from the failsafe terminal and just delete them.
i played with ownership and i had problems with some .dmrc file a few times.

yes, i am sure this could be considered a dirty fix, but i hadnt found anything else that worked... and i have used this method about, oh, i'd say 6-7 times with no failures. the only thing i notyiced that i lot was the next login, i had no default session type saved. OH NOES.

* so click session type BEFORE logging in
* select failsafe terminal
* then login
* um so in the FAILSAFE terminal from home dir...
* enter the following... what is INSIDE the quotes-->
* " rm .Xauthority "
* " rm .ICEauthority "
* " exit "
* now select your session n pick gnome/kde
and login like normal. sure beats a reinstall or bashing my head into the keyboard.

---

