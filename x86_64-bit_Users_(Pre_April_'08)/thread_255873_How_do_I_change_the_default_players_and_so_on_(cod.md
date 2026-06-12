---
title: "How do I change the default players and so on (codec problems)"
date: 2006-09-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Saubazi on 2006-09-12
Firstly, what irritates me in the first place is the default player - is it Totem or what that firefox is trying to open. Almost any kind of movie file and it is moaning about missing codecs - in fact I don't think I have been able to play anything with it yet? Is there a way to improve situation - where should I place codecs so that this one also does something?

I installed mplayer and that works already fairly well - only for windows codecs (wmv etc.) I installed it on chrooted environment. I did the same for firefox, in order to get it run with flash - now I have executables mplayer32 and firefox32. 

Problem is that I can't play wmv's directly from mail program my mplayer32 executable is not offered? Same if I open a link to some flashfile the mail wants to start firefox and not firefox32 ... any change to fix this one?

---

### Post by Kilz on 2006-09-12
> **Saubazi said:**
> Firstly, what irritates me in the first place is the default player - is it Totem or what that firefox is trying to open. Almost any kind of movie file and it is moaning about missing codecs - in fact I don't think I have been able to play anything with it yet? Is there a way to improve situation - where should I place codecs so that this one also does something?

I installed mplayer and that works already fairly well - only for windows codecs (wmv etc.) I installed it on chrooted environment. I did the same for firefox, in order to get it run with flash - now I have executables mplayer32 and firefox32. 

Problem is that I can't play wmv's directly from mail program my mplayer32 executable is not offered? Same if I open a link to some flashfile the mail wants to start firefox and not firefox32 ... any change to fix this one?

You are experencing one of the reasons a chroot is a problem. Its a jail. It only runs things it can see in its chroot. Lucky for Dapper users a chroot isnt nessasary to run most common things. In my signature you will find a link to installing firefox and flash without a chroot. Also, [in the sticky]("http://www.ubuntuforums.org/showthread.php?t=191205") for getting programs to work is [32bit mplayer]("http://www.ubuntuforums.org/showthread.php?t=188974") .
Once you have those installed its possible to replace the 64bit firefox if you want to. The howto's install along side, they dont replace. As it is now with a chroot I dont think its possible.

---

### Post by Saubazi on 2006-09-12
I am not sure I follow - I accomplish more or less exactly the same bits and pieces with the chrooted environment. I have linked the executables to 64bit environment and "normally" for example the web browser icon starts firefox32. However, the problem is that thunderbird for example when having a hyperlink launches 64bit firefox - I think it would be just the same if I had force installed 32bit version parallel to the 64bit - or am I missing something?

The same is with mplayer, I think? 
It is only about the default executables the programs choose, isn't it - could try to point that gmplayer link to my mplayer32 too:confused:

---

### Post by Kilz on 2006-09-12
> **Saubazi said:**
> I am not sure I follow - I accomplish more or less exactly the same bits and pieces with the chrooted environment. I have linked the executables to 64bit environment and "normally" for example the web browser icon starts firefox32. However, the problem is that thunderbird for example when having a hyperlink launches 64bit firefox - I think it would be just the same if I had force installed 32bit version parallel to the 64bit - or am I missing something?

The same is with mplayer, I think? 
It is only about the default executables the programs choose, isn't it - could try to point that gmplayer link to my mplayer32 too:confused:

Can you open the 32bit browser and then open the files with Files > Open Files ? If not the applications in the chroot may not be able to see files outside of the chroot, a common problem.
You could try to add a symlink to the applications in the chroot, replacing the files in the non chroot area if you can open the files.

---

