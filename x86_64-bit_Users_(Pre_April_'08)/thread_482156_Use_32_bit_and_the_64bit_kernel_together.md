---
title: "Use 32 bit and the 64bit kernel together?"
date: 2007-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by natman on 2007-06-23
Hi i have a the 64 bit ubunut, but certain things are not working, can some tell me if i can downlaod the 32 bit kernel and make it and the 64 options in grub, if so how to i go about doing that, what do i search for in adept?

---

### Post by supersonicdarky on 2007-06-23
what sort of things are not working? it is possible to forcibly install 32bit packages on 64bit os.

---

### Post by natman on 2007-06-23
Sound, firefox(32 bit on 64 ), C++ ides are all not right. If i install the 32 will there be problems?
What do is search for in adept?

---

### Post by natman on 2007-06-23
Can anyone just tell me if what i want to is safe, and how to go about it ( ie what to look for in adept to download, or a terminal command )
Thanks

---

### Post by Cappy on 2007-06-23
Not possible, 32-bit would require a full install on a separate partition.

---

### Post by Kilz on 2007-06-23
> **natman said:**
> Sound, firefox(32 bit on 64 ), C++ ides are all not right. **If i install the 32 will there be problems?**
What do is search for in adept?

Most of the time there will be the exact same problems you are faceting now. There is no such thing as a click, click, and everything runs cant possibly mess up linux version, heck there is no operating system like that on earth including proprietary ones.

---

### Post by incubus on 2007-06-23
Can you be more specific on what's wrong besides firefox and flash and java?

I say this because depending on what the problem is (e.g., hardware incompatibility), the 32 bit version would probably make no difference.

incubus

---

### Post by sp1nm0nkey on 2007-06-23
Okay. So, both the 32-bit and 64-bit kernels have support for loading 32-bit executables, it's just the 64-bit kernel has support for running 64-bit executables. Changing out your kernel won't do you any good since your userspace will still be 64-bit, so it won't be able to load 32-bit libraries. To remedy this, what you do is create a 32-bit chroot that you install separate instances of your libraries and select binaries compiled for 32-bit in, so all binaries that need them can get them. [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) is a good howto for doing this. You could totally add separate entires in your grub file for 2 separate kernels compiled differently, it's just unnecessary.

---

### Post by jpkotta on 2007-06-23
[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

This is the most robust solution to running 32-bit apps on a 64-bit system.  If you're new, it takes some effort.  Just about the only thing that can't run in a 32-bit chroot are kernel-space drivers (i.e. kernel modules).

Often, you can use ia32libs and maybe a few other libraries without a full-blown chroot.

---

### Post by Kilz on 2007-06-23
A chroot for the average users is a huge waste of space and work. The number of 32bit applications most users need can be counted on one hand. There are 64bit versions of almost all applications. There may be some people that may need one (like Developers who want to make packages for other versions). But for most people its just a lot of wasted effort imho.

---

### Post by natman on 2007-06-24
Okay so let me get this straight, the problems im having at the moment, no sound, firefox not working with flash, are probably not 64 bit problems but just general ones. And switching to 32 is more a time waste than anything lese.
But when i try to download stuff from the web, it only ever gives a 33 app, and when i force it to install it complains about the system architecture being different ( yahoo messenger is the app ).
Anyway i will probably stick with 64 feistym and hope ( like ive done for the last 5 versions ) that gusty will JUST work out of the box.
Thanks for the help

---

### Post by Kilz on 2007-06-24
> **natman said:**
> Okay so let me get this straight, the problems im having at the moment, no sound, firefox not working with flash, are probably not 64 bit problems but just general ones. And switching to 32 is more a time waste than anything lese.
But when i try to download stuff from the web, it only ever gives a 33 app, and when i force it to install it complains about the system architecture being different ( yahoo messenger is the app ).
Anyway i will probably stick with 64 feistym and hope ( like ive done for the last 5 versions ) that gusty will JUST work out of the box.
Thanks for the help

Exactly what steps have you done to get Flash to work? 
Yes, each time you "force" install anything it will warn you what you are forcing it to accept. This does not mean the application did not install. Are you saying that Yahoo isnt working? What have you done to try and see if it is?

What I would like to know, is exactly what the issue is? We dont need to reinvent the wheel. What problems you are pointing out here, solutions for both, are posted all over the 64bit section.

---

### Post by Mr_bleu on 2007-06-24
*when i force it to install it complains about the system architecture being different ( yahoo messenger is the app ).*
Have you tried gaim?  It's included in Feisty's installation and is a  multiple protocol messenger.  I have msn and yahoo signed in with it.  Just about any plugin you had for yahoo, you have in gaim, plus.

---

### Post by natman on 2007-06-24
> Exactly what steps have you done to get Flash to work?
Yes, each time you "force" install anything it will warn you what you are forcing it to accept. This does not mean the application did not install. Are you saying that Yahoo isnt working? What have you done to try and see if it is?

What I would like to know, is exactly what the issue is? We dont need to reinvent the wheel. What problems you are pointing out here, solutions for both, are posted all over the 64bit section.


When i tried to install yahoo, it gave the warnings, but would not allow me to progress any further ( perhaps it was my lack of knowledge, but i could not install it).To lay down what was giving me trouble is the following.
I got edgy and most things worked ( bar mic and web cam and i can live without them ), then i used adept and upgraded to feisty, and since then i only have sound on random boot ups, i have tried getting new alsa stuff and tweaking settings, but still nothings ( makes no sense since sound worked fine in edgy). Also of late firefox just crashs when i play a video on you tube ( once again only happens sometimes - i have given flash a higher cache, altered the resoulution - nothing fixes it).
I was under the impression that it was the 64bit problem, but after the responces its probably not. Its just that i do like kubunut, but windows has the advantage of just working, with out me worrying about about sound or firefox on each boot up.
I will try the 64 forums to see if anyone else has posted for a similar problem. Also i am using firefox 32, because of your script "kilz" thanks very much - nice and easy to use- even for me:)

---

### Post by Cappy on 2007-06-24
Try using firefox 64 with Kilz's other flash install script:
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

Sound problem solution here:
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

---

### Post by natman on 2007-06-24
Thanks very much for those two links, the sound now seems a lot better, no sound at boot up, but amarok and firefox all give sound, thats pretty mush all i wanted.
And firefox seems ok for the moment, thanks

---

### Post by Kilz on 2007-06-24
> **natman said:**
> When i tried to install yahoo, it gave the warnings, but would not allow me to progress any further ( perhaps it was my lack of knowledge, but i could not install it).To lay down what was giving me trouble is the following.
I got edgy and most things worked ( bar mic and web cam and i can live without them ), then i used adept and upgraded to feisty, and since then i only have sound on random boot ups, i have tried getting new alsa stuff and tweaking settings, but still nothings ( makes no sense since sound worked fine in edgy). Also of late firefox just crashs when i play a video on you tube ( once again only happens sometimes - i have given flash a higher cache, altered the resoulution - nothing fixes it).
I was under the impression that it was the 64bit problem, but after the responces its probably not. Its just that i do like kubunut, but windows has the advantage of just working, with out me worrying about about sound or firefox on each boot up.
I will try the 64 forums to see if anyone else has posted for a similar problem. Also i am using firefox 32, because of your script "kilz" thanks very much - nice and easy to use- even for me:)

I understand that you get the warning on the yahoo.
Anytime you force anything regardless if it installed or not you will get that warning. Why do you think yahoo isnt installed? Was there a error that said that the setup didnt continue? Are you sure it didnt install? Exactly how did you know it didnt install? If you are not sure, please try installing it again and copy the contents of the terminal to a post here.

---

### Post by natman on 2007-06-25
Hi cappy,>  Re: Use 32 bit and the 64bit kernel together?
Try using firefox 64 with Kilz's other flash install script:
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

Sound problem solution here:
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

I tried the second link for the audio fix, and restarted amarok and it was fine, did three reboots all fine. Amarok and youtube both gave sound, while gaim and noatun did not.

I got up this morning and booted up to not sound whatsoever, tried the solutiion three time from the above link, nothing, few hrs later i booted up again, and sound is back in amarok, but no start up music.
Do you know what the problem might be?

---

