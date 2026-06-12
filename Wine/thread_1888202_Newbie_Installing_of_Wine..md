---
title: "Newbie Installing of Wine."
date: 2011-11-28
forum: Wine
---

### Post by Mackus on 2011-11-28
Hello. I am using Ubuntu 11.04, I've downloaded wine-1.3.31, and I want to install it. But:
I want to keep my existing .wine folder
I want to use folder of my choosing, for example: .wine2
I dont want to litter other folders and settings with shortcuts and such i wont use,
i want everything installed to be contained in /home/me/.wine2 and run it NOT with "wine file.exe" command, because i want to keep it to my old wine.

I am however newbie when it comes to installing anything in linux, I dont really understand how it will work, last time I though I did, I entered "sh winetricks vcrun2005sp1 vcrun2005" installing it to my default wineprefix, because i assumed its was idiotproof, and would ask "do you want to irreversibly modify wour wine?"
and now I can't use tiberian sun (i essentially want to make fresh wine just to do that).
I understand its impossible to "uninstall" them by one click, but is it impossible to remove those libraries manually (get list of files, then delete them?)

Manual in downloaded package lists commands needed to be inputed to build and install wine.
"Build" if i understand correctly means "compile", and probably does not affect my system, but according to what I understand of manual, use of both "make" and wineinstall WILL mess my system.
Unless unlike winetricks both ask usual "do you want to" questions.

Thanks.

---

### Post by cwwilson721 on 2011-11-29
To make things easy for you:

DON'T compile wine (make, make install, configure...), unless you REALLY HAVE TO. 

For a 'beginning Linux User', it's not reccomended to compile wine. Just install wine1.3 from the repos, and it will work. (I do alot of compiling of many programs, and even kernels, and DO compile my own wine for 'special' boxes that need it. But I've been doing this for a long time. For a 'newb', just use the repos. Compiling comes with many, many. many headaches for the new guy. I generally use the wine1.3 from the repos just for the ease of installation)

Just get into a terminal and type
```
sudo apt-get install wine1.3
```

This will NOT mess with your .wine folder, it only installs the program 'wine'. Your .wine folder will be untouched.

wine is the program running in Linux, and your 'wine' folder is the program and data you want to run. They are different animals. An example of the difference is wine is the car, and your wine folder is the trailer you are towing behind it. You can change cars, and the stuff in the trailer is still there.

Now, for your other concerns:

What you basically want to do is create different folders for different programs, correct?


I do the same thing. I play World of Warcraft, and have Office, and a few other programs and games that need wine to run on Linux, but I do not want each of them to 'mess' with the others. A great example is I run a program that needs the vcrun things, but WoW does not. Rather than screw up my perfectly working WoW install (and have to redownload 16+ GB of files), I create different folders for each, and run them with a modified laucher command.

A good way to install programs is this 'checklist' I use to get things installed, then make it into it's own folder:
(NOTE: Substitue your own username wherever the following has <USER>)

[LIST]
[*]Delete any existing '.wine' folder in my current 'home' directory, making sure it is REALLY empty first. (I hate deleting a program I actually use...lol). If anything useful is in it, make a backup.
[*]Run the command 'winecfg' in a terminal. This creates a 'fresh' .wine folder with defaults
[*]I then install whatever program needs to be installed, along with whatever other 'requirements' it needs.
[*]I test the program, to make sure it works.
[*]I then rename the .wine folder to another name I will use (For WoW, I use '.wine-wow')
[*]I then edit the launcher command (or create one) with the new name. To continue with the WoW example, the original launcher has this command to launch: 
env WINEPREFIX="/home/<USER>/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
[*]I change that to : 
env WINEPREFIX="/home/<USER>/.wine-wow" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
 (Note the difference of '.wine' and '.wine-wow. The '.' in front of a folder name means it's 'hidden' in Linux)
[*]I make sure the new launch command works. If not, I try, try again...lol
[/LIST]

The 'env WINEPREFIX=' command is what makes this possible. It allows a separate 'environment' to run the wine 'bottles' in, without them messing with each other. In this way, I can run WoW and Office at the same time without them 'mixing', kind of like having to different Windows computers running at the same time. If one messes up, it generally does not mess with the other install. As an aside, wine does not care WHERE the program is actually located, as long as the 'env' is pointed to it. Programs running under wine do NOT have to be in the '.wine' folder, or even in your home directory. There are caveats with this, so tread carefully.

For example, I have Office launch with 'env WINEPREFIX="/Office/.wine-office" wine "C:\Program Files\Office\Office.exe" (I move things around sometimes, just so I know where it is. And I have Office in it's own partition even, and I run it with other users on my network using network shares and wine. Permissions are a bugger sometimes, but you gotta do what you gotta do)

Hopefully, this makes sense to you.

Good luck!

Let me know how it goes, and any questions you may have.

(BTW, as a bonus, doing it this way is EXACTLY what Play On Linux does, without the added 'layer of complexity'. Also, YOU know how it works. Knowledge is POWER!)

---

### Post by cwwilson721 on 2011-11-29
BTW, I use the launch command in terminal, too, so I can see what the issue is when I'm testing the install or the new 'bottle', and it doesn't work.

A just-in-case type of thing.

---

### Post by Mackus on 2011-11-30
Thanks, it works perfectly, as you told it would. Only thing I made differently was that I backep up my old .wine, then restored after I created/renamed .wine2 directory and tested it. Now I can use both, at same time even. In hindsight its actually quite easy.
Thank you very much :D

---

### Post by cwwilson721 on 2011-11-30
Yeah, I should say that in that post...I'll edit it for that.

Could you mark this thread as 'solved'? Under "thread tools" at the top of thread.

---

