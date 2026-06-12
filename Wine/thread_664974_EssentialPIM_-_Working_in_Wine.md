---
title: "EssentialPIM - Working in Wine"
date: 2008-01-11
forum: Wine
---

### Post by MaxVK on 2008-01-11
I don't know if this information will be of any use, but I figured to put it here just in case.

I have Ubuntu 7.10, running as a dial boot with Windows 2000.

Iv just recently moved to Ubuntu, and the one thing that I really, *really* needed was a calendar application that I could sync with my Windows calendar. In windows I use [EssentialPIM Pro]("http://www.essentialpim.com/").

However, under Wine it was crashing quite spectacularly until I found and installed[ Wine-Doors]("http://www.wine-doors.org/wordpress/").

Once Wine-Doors was installed I used it to install the "Microsoft Data Access Components 2" and  then in the Wine config made sure that EPIM was set to run as if on XP, and from then on it works like a dream.

Just thought to share.

Max

---

### Post by newmusic on 2008-02-05
Im a newbto linux but have installed wine doors and managed to get essentialpim installed to but it hangs. Am trying to get the microsoft data access etc - where can I get this file? - microsoft want me to verify.
2. Please guide me thru the config file thing

I guess the file system is similar - I have installed opensuse 10.2

Yourhelp will be much appreciated.
thanks

---

### Post by hagalaz on 2008-06-02
newmusic You can install MDA with wine door. It's in the list of software you can download when you run it.

It's not working for me though. 

Max, did you have to add the gds32.dll manually? If I don't do that, there's an DB error that keeps epim from loading and if I do,  once loaded, epim says it can't find the DB (?)

What version of epim are you using?

I'm interested in hearing from anyone trying to get it working.

---

### Post by MaxVK on 2008-06-02
Hi hagalaz.

Im using EPIM 2.2 which is probably quite old now (Iv been wary of installing any updates in case they broke the Wine installation, and besides, Iv not really needed any of the thing that have been updated).

I downloaded it from the official EPIM site and simply installed it with Wine. I have no idea about the gds32.dll, but Id be suspicious that the problem may be with the way Winedoors installed it.

If I remember rightly you can download either a free Lite version, or a demo version from the official site, so it might be an idea to go for that option and then just use Wine to install it and see what happens.

By the way, if its just a calendar you are looking for you could always have a look for Rainlendar, which is much lighter but works really well (Another reason why EPIM has not been updated recently).

Hope you get things sorted

All the best

Max

---

### Post by hagalaz on 2008-06-10
Thank you for your reply Max.

That may be the answer to my problem. I can't get it to work with 2.5 but it got installed seamlessly with wine for a prior version. (between 2.1 and 2.5 I guess).

Unfortunately I had to reformat my ubuntu partition and it didn't occur to me to back it up. I'll give a shot to the light version as you suggested.

I'm going to have to stick with epim as I have several heavy projects making use of it. If all fails, I will run it under my windows boot.

---

### Post by killerwhale65 on 2008-07-12
hello,

I am new to this. I was wondering how exactly to install essentialpim with WINE? I get an error during install that it can't find language files for writing. My guess is it has no rights to write files/folders into the system. Should i do this as root? How?

thanks!

Matt

---

### Post by MaxVK on 2008-07-13
Simply put, you can right click on the setup.exe (or similar) and from the menu select to run the program with Wine. I'm not sure what errors you are likely to get, but if it looks like you are missing a bunch of Windows files make sure you use "Wine-Doors"  to install the libraries that are needed.

You shouldn't have to install as sudo and I would strongly advise you not to do so, most especially when dealing with a Windows program! (I have no idea what would happen if you inadvertently activated a virus in Wine, but I suspect that Wine would get rather upset!)

Regards

Max

---

### Post by killerwhale65 on 2008-07-13
hello,

Thanks for your answer.

That is how i try to install it. It is not missing windows files, but its own files: it starts with saing that it cannot write to ..../Essentialpim Pro/Languages/Bulgarian.lng. If i click ignore it says the same but with another language file, and like that it continues with all possible languages. When i go to the specified folder, the Languages folder does not exist, and no single file or folder is in the EPIM folder, so it seems logic that it cannot open them. But i dont know why the files arent copied.

---

### Post by MaxVK on 2008-07-13
I would be inclined to check the source files. It almost sounds like the EPIM setup program is corrupted in some way. Perhaps you could download it again? What version is it? The only version I have tried is fairly old by now so I have no idea if a newer version would work.

Other than that I'm afraid I cant really help. The method I described above is just how it worked for me, and I don't really know where I would start looking for a solution to your problem. Perhaps a visit to the Wine application database ([http://appdb.winehq.org/](http://appdb.winehq.org/)) might throw up an answer for a specific version/problem. Sorry.

Good luck

Max

---

### Post by killerwhale65 on 2008-07-13
ok, i will download it again. Its the latest version 2.7.

---

### Post by rph2go on 2008-07-16
I got epim 2.7 to work!! when I (in addition to the steps already mentioned) installed MS Visual C++ with Wine-doors. Hope this helps someone.

---

### Post by houman001 on 2009-09-28
Or you could alternatively download msvcp60.dll and put it next to the other .dll files in EssentialPIM.
I got it from here: [www.dll-files.com/dllindex/dll-files.shtml?msvcp60](www.dll-files.com/dllindex/dll-files.shtml?msvcp60)

---

