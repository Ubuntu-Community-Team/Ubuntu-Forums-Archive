---
title: "ALIEN ARENA 2009 how i got it to work on Ubuntu 9.04"
date: 2009-08-03
forum: x86 64-bit Users
---

### Post by orangeapostle on 2009-08-03
so i just installed Ubuntu 9.04 the other day on my alienware. this is the first time ive used linux in like 2 years and its still pretty frustrating but i can see the rewards if your willing to learn and put in the effort. still a longggg way to go though. 
but i digress.
i downloaded alien arena 2009 and tried to first off move it to my usr/local/games folder or whatever. now for me right off the bat the usr folder is locked and i have no permissions. im a total linux n00b and after some research i found out how to change my permissions. open your terminal and enter the following:
sudo chmod o+wx /usr
then it'll ask for your password so enter it. this gives you write and execute permissions for the usr folder. it doesnt really matter where you put alien arena 2009, but this will matter when you try and run the crx file and it gives you the error cannot access shared libraries or whatever. now when you first install ubuntu for some strange reason the default update manager does not install the 64-bit libraries so you need to get getlibs, from here [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb) and then just run it.
from your terminal type sudo getlibs -p libxxf86dga1 and select yes. this will install that magical openAL library you need for your 64bit ubuntu version. if after all of this you still don't have some library, go back to your terminal and enter
sudo getlibs /whateverdirectoryyourcrxfileisin/crx

that should let you run alien arena 2009. if you have a shitty ATI card like me, from what i gather there is no solution to the low fps due to some proprietary driver garbage. i read something about maybe compiz or hardy fixing the problem or downloading some xorg libraries. if when you enter a server you lose all function of your mouse go to the console, which is under settings i think and enter 
export SDL_VIDEO_X11_DGAMOUSE=1
that will fix your mouse problem and you can adjust your mouse speed settings if its too slow. if i find anymore info about how to increase frame rate here.

---

### Post by orangeapostle on 2009-08-03
okay i think i fixed the fps problem for my ATI Radeon HD card. i went to synaptic package manager and in the search i typed in ati.
if you see 'xorg-driver-fglrx-dev' then check that. working for me so far

---

### Post by lyghtkruz on 2009-08-04
> **orangeapostle said:**
> i downloaded alien arena 2009 and tried to first off move it to my usr/local/games folder or whatever. now for me right off the bat the usr folder is locked and i have no permissions. im a total linux n00b and after some research i found out how to change my permissions. open your terminal and enter the following:
sudo chmod o+wx /usr
then it'll ask for your password so enter it. this gives you write and execute permissions for the usr folder.

I would advise against chmod on the /usr directory.  You don't have write access to it on ANY Linux distribution for reasons of security.  Changing this will give write permission to ANYONE who has access to your computer, whether they are an admin or not.

If you want to copy/move directories/files into any directory you don't have access to, copy/move via the sudo command.  

sudo cp filename /newlocation/filename (copies a file)
sudo mv filename /newlocation/filename (moves a file)
(warning, if a file already exists with the same name. these commands will overwrite the file)

-Kruz

---

