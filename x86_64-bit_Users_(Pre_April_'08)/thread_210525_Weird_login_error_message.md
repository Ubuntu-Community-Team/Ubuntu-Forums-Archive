---
title: "Weird login error message"
date: 2006-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-07-07
I am the only user of this laptop. My username is jjj and there has never been a problem logging in ever since I first installed Dapper-64. This is summer vacation so I have just had the computer running at home. However, today I went to the university. After entering my username and password I got the following error message:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

Now, that certainly makes sense, except that I had just given it my username and password as "jjj." The error message popup had an "OK" button. I clicked on it and it proceeded to display the desktop as always. And everything seemed to be working as always. I opened Nautilus and I do, indeed, own /home/jjj and have full read/write/execute permission for it.

The first thing I thought was that it must have something to do with logging in from the university. In retrospect, that makes no sense. Sure, I needed to connect to the university wifi network, but at the time of logging in Ubuntu would have no idea yet where I was. In any event, as soon as I got home I booted the computer and got the same error message again. And, as at the university earlier, it seems to make no difference. I can still open and save files, etc. Everything is working the same as always.

Earlier in the day I did two things that might have affected the issue. The first is that I had a problem playing a WAV file and, in the process of troubleshooting it, I changed the ownership and permissions of /etc/dsp from root to jjj. 

The second thing I did was explore Nautilus in great detail. I had always eschewed Nautilus under Breezy, but perhaps that opinion was shortsighted. I spent some time configuring how I wanted it to appear and work. However, I did not change any permissions for anything while doing so.

Does anyone know what causes this error message and/or how to fix it?

---

### Post by woedend on 2006-07-07
sudo chmod 644 .dmrc
did you try that command?
also, if this doesnt work, set proper permissions to the entire home folder

---

### Post by John Jason Jordan on 2006-07-07
> **woedend said:**
> sudo chmod 644 .dmrc
did you try that command?
also, if this doesnt work, set proper permissions to the entire home folder
I just tried that command. Made no difference. Still get the error message on login. I am already the owner and have full permissions to the entire /home/jjj folder.

Thanks for the suggestions. Any more ideas?

---

### Post by woedend on 2006-07-07
right, but are you sure that others don't have write access to your home folder as is suggested by the error msg?

---

### Post by John Jason Jordan on 2006-07-07
> **woedend said:**
> right, but are you sure that others don't have write access to your home folder as is suggested by the error msg?
The only other user account was "jxj," an account I had created as an emergency account in case some day I was unable to log in as myself (jjj). Just now I deleted the jxj account, so I am now the only user. And I still get the same error message on logging in.

Anyone have any other ideas? Any way to find out what process generates this particular error message?

---

### Post by woedend on 2006-07-07
right, but you don't have to have another account for your permissions to be fubared.
you'd probably want your home folders permissions set to 755.
sudo chmod 755 /home/xxx

---

### Post by John Jason Jordan on 2006-07-07
> **woedend said:**
> right, but you don't have to have another account for your permissions to be fubared.
you'd probably want your home folders permissions set to 755.
sudo chmod 755 /home/xxx
Thanks again,. Set the permissions to 755, but I still get the error message. The weird thing is that if I just click on OK it goes ahead and everything works fine.

Another odd thing: Just before this started I had been having trouble playing WAV files. Someone told me it might be the /dev/dsp file, because the error message was that the sound system was busy. (This turned out to be bogus; the real problem was that Firefox was holding a death grip on /dev/dsp so nothing else could use it.) Before discovering that, in an attempt to troubleshoot the problem, I changed ownership and permissions on /dev/dsp to jjj and gave everyone permission to do anything with it. This morning I decided to change it back to root to see if that would make the error message go away. When I looked at /dev/dsp, it had been changed back to root, and I didn't do it. 

I have a second installation of Dapper-64 in another partition on the same computer. The second installation is just bare-bones, to use as a rescue system. It has never been tweaked, adjusted, folded, spindled, mutilated, or anything else, and no programs have ever been installed on it. Both installations mount the other's partition on bootup, so I can go look at files on the second installation to see how things are normally supposed to be. The ownership and permissions of /dev/dsp is identical on both systems.
Ditto for the /home/jjj folder.

I'd like to know what the login process looks at that makes it generate that error message. If I knew that I might have a clue how to fix it.

Does anyone have any ideas?

---

### Post by helter2 on 2006-07-13
You have to give write/read/execute acess ONLY to the owner of the /home/jjj. The group and other should not have write/read access. You can do that with nautilus or with chmod.

If you have more questions, or it doesnt work again. Post again.

Good luck.

---

