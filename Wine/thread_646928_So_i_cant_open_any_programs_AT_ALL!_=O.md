---
title: "So i cant open any programs AT ALL! =O"
date: 2007-12-21
forum: Wine
---

### Post by Countra on 2007-12-21
Yeah, so i install a program you know, fix all the winecfg and stuff and there i am at that moment.. the final CLICK and i do the CLICK and guess what? As always, numpty ubuntu fails to live up to its reputation and fails me ONES AGAIN! This is IT! Ubuntu is clearly flawed and so is wine btw, i mean, this IS wines fault, yeah.. so i guessed some nice soul out there might just want to help me or i dont know.. bcuz this is a help forum, right? YEah.. And this is what i get when i typ winecfg btw:
> arsham@arsham-desktop:~$ winecfg
ALSA lib pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument
fixme:mixer:ALSA_MixerInit No master control found on Camera, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
err:module:import_dll Library vct3216.dll (which is needed by L"C:\\windows\\system32\\vct3216.acm") not found

something about my camera.. Which is intresting beacuse my cameras mic is not working! O.O yeah.. That it is! And btw, this is what i got from:
> arsham@arsham-desktop:~$ ps -deaf | grep defunct
arsham   17469 17373  0 02:19 pts/0    00:00:00 grep defunct
arsham@arsham-desktop:~$ 
 ok, so yeah, wine + my cameras mic are ***** up :P can anyone help me? Please? :-D

EDIT: my wines version is 1986! lol just kidding no really, its the newest version :P updates at the max

---

### Post by Countra on 2007-12-21
oh and btw, what it failed was to start the program! My original question was this: why does the programs not start with wine? Sorry, i tend to get VERY offtopic when i type LOL xD
the programs do come up in the panel though.. this is very weird! I know that there is another thread with a similiar question but he was in a diffrent situation so its diffrent ya know ;P

---

### Post by Countra on 2007-12-21
im going to sleep now, seems like noone has answered me, and i waited all these minutes! lol (i know, this one was a bump really lol xD) just.. yeah, thanks for answering :-D

---

### Post by cogadh on 2007-12-21
First off, if you want help, try using complete sentences that make some kind of sense. It is also preferable that you not use a help request to post an unwarranted rant, it doesn't exactly make helping you a welcome concept.

Now, if we are going to help you, you need to give us a little bit of specific information, such as what application are you trying to run and what exact steps have you taken to try and get it running.

As for the problems you already posted, "fixme" messages are just developer notes about incomplete or unimplemented functions of Wine. They usually mean nothing to an end user. The specific fixmes that you got are ones that most everyone gets, you can ignore them. However, the "err" message you got is actually something you can fix. Wine is basically telling you that a DLL that is used by your application, vct3216.dll, is not present in Wine. All you need to do to fix that is copy it from a Windows machine (or Google it, I'm sure you can download it somewhere) and place it in the ~/.wine/drive_c/windows/system32 directory. After you do that, run the app again and that error will go away, but others may crop up.

Now, to address some of your rant, Ubuntu is not flawed, it works fine for most everyone. Generally speaking the problems that people do have with it occur between the keyboard and the chair, not the fault of the OS. Wine is beta software and it is not even close to complete. You can't expect an incomplete implementation of the Windows API to work fully or correctly every time. Hell, you should be glad when it works at all, considering the devs are creating Wine by only referencing Microsoft's incomplete and crappy API documentation.

---

### Post by Countra on 2007-12-22
so i should download vct3216.dll eh? Okay, will do... Thanks! :-D

---

