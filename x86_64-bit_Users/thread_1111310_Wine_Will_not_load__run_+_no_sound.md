---
title: "Wine Will not load / run + no sound"
date: 2009-03-30
forum: x86 64-bit Users
---

### Post by kehon on 2009-03-30
i just installed wine yesterday since then i have installed a few apps like eclipse,vuze, etc but now wine wont load at all and besides that(in another topic) my sound stopped working on my compaq presario c700 i've never had a problem with the sound before but i'm new to linux altogether can someone help me with either of these

---

### Post by hellblade on 2009-03-31
Please use one thread per topic.

**Wine**
Did wine, or more specifically the applications installed with wine run before? If yes, do you remember doing anything between working/not working states?

Try wine with a clean settings directory to see if your settings got corrupted somehow:
In a console run the following two commands:
```

mv .wine .wine.old
winecfg

```

The second command should launch a configuration window. I have noticed that in my pc I have to switch to the audio settings tab once (for each wineprefix) and dismiss a warning popup before the audio starts working with wine.

Then install again a windows application to the now clean wine and see if that works.

If it doesn't, run the application in a console to see the output produced and paste it here.
To run it in a console, the easiest way is:
```

cd ~
wine ".wine/drive_c/Program Files/Application Directory/Program.exe" 

```

Finally I prefer to run the latest wine version from [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)


**Audio**
**Start a new thread** and post your audio card details, which programs did your try in which the audio is not working etc.
Also make sure you volume is not too low or muted.
Run "lspci -v" and paste the block of output about your card (it starts with "Multimedia audio controller: ").

---

### Post by kehon on 2009-04-01
moved home directory back and that fixed wine

edit: was on ntfs partion and moved home back to ext3 partion because ntfs does not support permmisons and i think wine must need them or something

---

### Post by stchman on 2009-04-01
> **kehon said:**
> i just installed wine yesterday since then i have installed a few apps like eclipse,vuze, etc but now wine wont load at all and besides that(in another topic) my sound stopped working on my compaq presario c700 i've never had a problem with the sound before but i'm new to linux altogether can someone help me with either of these

Eclipse is available in the repos.

Remember WINE tries to support Windows apps.  It is not 100% guaranteed compatibility.

---

