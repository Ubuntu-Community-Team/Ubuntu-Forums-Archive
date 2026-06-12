---
title: "Confused newbie"
date: 2008-05-23
forum: Wine
---

### Post by linuxinireland on 2008-05-23
I am so new to this please if you decide to respond, please dont assume i know to much. 2 questions please

1   Ok, i am just going to have to admit i dont know what im doing.  Ok I installed Wine onto my main user account, was this bad? how do I fix?


2   So now I want to use wine from a different account login, like it said in wine faq to do, but i want to start with a clean slate. anybody care to help me?

---

### Post by fuzzyk.k on 2008-05-23
i don't know what you mean by main user account by am guessing the account you created on installation, installing wine on that account is ok , these nothing wrong with that what do you mean using it with a different account ?

---

### Post by linuxinireland on 2008-05-23
OK, Maybe Im trying to be to complicated but, this Ubuntu is hard to use.  I have been on here reading and reading but in the end, i cant seem to make things work.  I just put ubuntu on here, and now i feel like wiping it clean and starting over, the only problem, i dont think i can avoid making the same mistakes again, I simply cannot wrap my brain around all this stuff.  I feel like none of the how tos are all that helpful, as I am always left with questions, many of these instructional based how tos are simply out of order, one needing to be done before the other, or youll screw everything up. How is that any different than windows?  I dont want to format my HD. Please someone out there save me. Please assume I am dumb if you decide to help me becasue I need any free lessons out there.  Everything on my machine right now is running smooth, except I need help installing a game package, as I have almost no experience.  I want to run my computer as a server for this game to, its old so it shouldnt be impossible as i used to run this game smooth on a 233 MHZ.  I would like to run a small deathmatch server maybe 16 people at the most, using the quake team fortress 2 mod. Anyone familiar with this game, please message me.  I already have all the files i need, I just dont have a clue about whether or not I should use wine to play this game, Should I use wine to install this game  and its packages?  Some files that come with it are zip fles, do I have to install winzip? god I have so many questions. please somebody out there who likes a challenge, and obviously someone really smart, write me back.

---

### Post by roderick on 2008-05-23
Wine is as simple as:

1) Install it from the Add/Remove Programs (or use your favorite package manager - synaptic, Adept, etc). You do not necessarily have to get any more complicated than that. If you optionally, want to get the latest from winehq, then there are a couple of step. See here for info: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

2) From the user account you wish to run wine, you should run winecfg (If there is no menu item for this, then you should be able to type it in a run dialog - ALT+F2 should open that). Under Kubuntu, there are menu items for running wine config directly - not sure about Ubuntu. Wine config (winecfg) allows you to modify some common parameters like default folders, audio (use ALSA), Windows OS to simulate, etc. It also creates the default (hidden) directory structure (which can also be done via running wineprefixcreate - but you really only need to run winecfg).

3) Now you should be able to install your favorite app (assuming it works with wine - verify by researching in [http://appdb.winehq.org](http://appdb.winehq.org). Insert your CD/DVD or other media with the software to install. Locate the install.exe or setup.exe or similar and open it. Under Kubuntu, this will auto-launch wine and run the windows application you clicked. Not sure under Ubuntu if the file association is there or not, but I suspect it would be.

4) If there are problems with the program, visit [http://winehq.org](http://winehq.org) for tips. 

Most of these HowTo's are written for when it was not as simple as point and click. If you install Hardy Heron fresh, most things work correctly out of the box (at least my experience with the superb kubuntu version).

Also, wine is not a finished product and not everything works 100%. If you can get th epoint and click experience with your program, then that's all you should need. If it doesn't run this way, you will (unfortunately) need to resort to the command line (terminal) and you will have to learn about the bash shell (similar to the DOS shell in windows but more commands and ability).

As long as you installed wine via the package manager and not from source, then it get's installed system wide and each user can access wine and run their own virtual copy of windows programs. Each user will need to run winecfg, etc. Each user will not see another users wine installed programs.

---

### Post by aoanla on 2008-05-23
Note: it is easier to get help if you give people useful information in a clear and concise manner.

After some reading of your second post, it appears that you installed Wine because you wanted to get Quake (and then Team Fortress) working in it.

Firstly: you don't need Wine to play Quake - there are much superior ports of Quake than the original program, and many of these work natively in Linux. Wine is for using Windows programs in. 

Secondly: you certainly don't need to install WinZip - the "Win" might well imply to you that this is a Windows-based program, and Ubuntu knows, from install, how to deal with compressed files like zip files.

Can you please give us more details about precisely what you are trying to do?

---

