---
title: "Finally made Paint Shop Pro 8 and Wine work as before under 18.04 LTS! But..."
date: 2018-10-20
forum: Wine
---

### Post by armrek on 2018-10-20
Yes that's right - I did get it to work!

But the solution came in another form than I had expected. I have  recently gotten the Update to 18.04 dialog for while, and gave the  update a go. An everything went smoothly, and even Wine works as before.  

So a couple of things comes to mind:


[LIST=1]
[*]Has Wine been fixed? 
[*]Or do you need make a fresh  install of 16.04 LTS + Wine and the update to make it work? 
[/LIST]

If anybody knows what is correct I would like to know, because it would be a hassle to install 16.04, Wine, Upgrade and then install all the stuff I use?


No matter what I've got a system where Wine now takes care of my needs :-)

---

### Post by armrek on 2018-10-21
> **armrek said:**
> Yes that's right - I did get it to work!

So a couple of things comes to mind:


[LIST=1]
[*]Has Wine been fixed? 
[*]Or do you need make a fresh  install of 16.04 LTS + Wine and the update to make it work? 
[/LIST]

If anybody knows what is correct I would like to know, because it would be a hassle to install 16.04, Wine, Upgrade and then install all the stuff I use?

I have now made some experiments on some old machines I have, and unfortunately I have to conclude that you have to install 16.04 LTS first to get at functional Wine that also works from the context menus. You have to follow this recipe:

[LIST=1]
[*]Install a clean 16.04 LTS 
[*]Install Wine by calling '*sudo apt install wine1.6*' in a terminal 
[*]Now you can install Paint SHop Pro or any other old windows program you got by right clicking on xxx.exe and selecting to open with '*Wine Windows Program Loader*' 
[*]Update Ubuntu 16.04 LTS through the details dialog 
[*]Rebooting 
[*]Then updating again and accepting an update to 18.04 LTS from the requesting dialog, that appears after a while 
[/LIST]
I have also tried to call '*sudo apt install wine1.6*' in a terminal on a clean 18.04 LTS installation but that gives me Wine 3.0.1 which is broken, as in no context menu with the '*Wine Windows Program Loader*' item and several strange errors and warnings when calling wine xxx.exe on the command line. It installs alright but *Paint Shop Pro* crashes when starting as I have described in earlier threads...

My conclusion is *Wine 3.0.1 and the current development version are broken*, I do not know why they messed it up after 1.6?

For now this trick is a way to solve it, but not a good long term solution I am afraid...

---

### Post by mastablasta on 2018-10-23
if all you need is older wine you can use "play on linux" and install an older wine instance on the disk. what i like about play on linux is that you can manage multiple wine version easily with it.

---

