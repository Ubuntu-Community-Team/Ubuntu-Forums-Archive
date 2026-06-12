---
title: "rosseta stone for beginners"
date: 2012-02-23
forum: Wine
---

### Post by briar rabbit on 2012-02-23
Hello from beginnerville,

I would like to put rosseta stone language program on my laptop.   I have the CD.

I found an excellent guide for doing just such at: [http://forums.devshed.com/linux-help-33/wins-apps-running-on-ubuntu-10-04t-725817.html](http://forums.devshed.com/linux-help-33/wins-apps-running-on-ubuntu-10-04t-725817.html)

However when I followed those directions (as best I could) it did not work.

I have Ubuntu 10.04 and everything else works fine ... well except the wireless internet - which would be next.

Any help would be greatly appreciated.

---

### Post by yeats on 2012-02-23
> I would like to put rosseta stone language program on my laptop. I have the CD.

I found an excellent guide for doing just such at: [http://forums.devshed.com/linux-help...4t-725817.html](http://forums.devshed.com/linux-help...4t-725817.html)

However when I followed those directions (as best I could) it did not work.

Can you describe what you've done and what isn't working?

> I have Ubuntu 10.04 and everything else works fine ... well except the wireless internet - which would be next.


General advice: open one forum post per separate issue for the best help ;-).

---

### Post by briar rabbit on 2012-02-23
hI, yes thank you yeats,

I already had Wine 1.0.1.

I copied my rosetta language to a file.

I went to wine configure from Applications, checked the audio tab and saw it was on 'alsa' which I wanted.  

Then I clicked 'add new drive'  found the directory I had put the language files on and clicked add and apply.

I then went to rosseta stone and right clicked it and tried to open 'setup.exe' with wine windows program loader.  This is where things stopped as in nothing else happened nor could I find rosseta in the 'Applications > wine> list.

I hope I am making enough sense for you.  I followed the above link directions as best I can tell.

---

### Post by haqking on 2012-02-23
> **briar rabbit said:**
> hI, yes thank you yeats,

I already had Wine 1.0.1.

I copied my rosetta language to a file.

I went to wine configure from Applications, checked the audio tab and saw it was on 'alsa' which I wanted.  

Then I clicked 'add new drive'  found the directory I had put the language files on and clicked add and apply.

I then went to rosseta stone and right clicked it and tried to open 'setup.exe' with wine windows program loader.  This is where things stopped as in nothing else happened nor could I find rosseta in the 'Applications > wine> list.

I hope I am making enough sense for you.  I followed the above link directions as best I can tell.

did you check to see your rosetta version is supported in wine ?

[http://appdb.winehq.org/appview.php?appId=1867](http://appdb.winehq.org/appview.php?appId=1867)

alot are listed as garbage

---

### Post by briar rabbit on 2012-02-23
hello haqking,

According to the link you provided; yes.

I was on that wine site before but did not find that page.

my 2.0 ver.  is said to work on 8.04, I would guess that it will work on my 10.04

thanks

---

### Post by haqking on 2012-02-23
> **briar rabbit said:**
> hello haqking,

According to the link you provided; yes.

I was on that wine site before but did not find that page.

my 2.0 ver.  is said to work on 8.04, I would guess that it will work on my 10.04

thanks

why would you guess that ;-)

the 2 versions of OS are 2 years apart.

I am not personally a Wine user or Rosetta, but was just providing some pointers.

Best of luck

---

### Post by briar rabbit on 2012-02-23
Thanks for the input haqking,

I guessed because, as things progress they get better - maybe my bad. :-)

In my searches I have seen were  a lot of people have problems with RS and Linux.

some things are worth a little patience before moving on.

---

### Post by haqking on 2012-02-23
> **briar rabbit said:**
> Thanks for the input haqking,

I guessed because, as things progress they get better - maybe my bad. :-)

In my searches I have seen were  a lot of people have problems with RS and Linux.

some things are worth a little patience before moving on.

well problems are to be expected because Rosetta stone do not develop a linux version, you are trying to run a windows .exe/executable in Linux which is why problems exist.

If you cannot get it to work with wine then i suggest a virtual machine if you have a valid copy and licence for a windows or a dual boot.

Cheers

---

### Post by briar rabbit on 2012-02-23
don't know anything about 'virtual machines'

I have another pc with MS but the sound is out on it; 'no audio device' a perpetual problem with that other OS.

After my last go-round with MS I said no more.

Some people have put RS on their linux machines and if I understand 'virtual' from what little I have already read ... well I am seldom on the Internet.

peace

---

### Post by forrestcupp on 2012-02-23
Sometimes it's best to copy the entire contents of your CD to your hard drive and install it from the hard drive. When you do that, find your setup.exe file in Nautilus, right-click it, and choose properties. In the "Permissions" tab, check the box next to "Allow executing file as a program" and close.

Then open a terminal and navigate to the folder where your setup.exe is, and type
```
wine ./setup.exe
```If you try to install it from the terminal and there are errors, you will see the error output in the terminal. If it still doesn't work after doing this, post the errors you see in the terminal, and it might be easier to troubleshoot.

But you're sure your version of Rosetta Stone is listed as working with your version of Wine? There have been a lot of Wine releases since your version 1.01, and maybe whoever got it working was using a newer version of Wine. Also, sometimes there are workarounds you have to do to get specific software to work properly with Wine.

---

### Post by briar rabbit on 2012-02-23
howdee forrestcupp,

I went to the Help Center "Using the Command Line" to find and read the 'File and Directory Commands' and I got and "Unable to load page" The requested URl "xref:files-directories-commands' is invalid"

I then tried "System Information Commands" in the same Help Center and got the same error.

I do not know the 'exact' command to copy a disc to the hard drive.  

When I try to just copy RS it or send it those areas after a right click on the mouse they are just grayed out.
When I right click on the RS desktop icon I get; Open, Browse Folder, Open with Auto Prompt (which I have already tried and does not work), Stretch Icon,  Compress, Unmount, Properties. 

compatibility;
Listed as 'Platinum' here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7335](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7335)

Listed as 'Silver' here:  [http://appdb.winehq.org/appview.php?appId=1867](http://appdb.winehq.org/appview.php?appId=1867)

I suppose I just know a whole lot of nothing about linux and pc's in general.

I do thank everyone for their input, help and time.

---

### Post by forrestcupp on 2012-02-24
You don't have to copy the CD from the command line; you only need to run the setup.exe from the command line so we can see your error output.

To copy the CD, just insert the CD and make sure it is mounted. Open up Nautilus, the file manager, and go to your CD. Press Ctrl+A to select all, then press Ctrl+C to copy. Then go to your Downloads or Documents folder and create a new folder and name it Rosetta, or something. Open that folder and press Ctrl+V to paste, and the contents of the CD will copy to your new folder. Copying a CD to the hard drive this way is pretty much exactly like doing it in Windows Explorer in Windows. When you create the new folder, try not to use spaces in the name because it makes it a pain to get to it from the terminal. You can do it, but that's not something you need to be worrying about right now.

When it's done copying, open the terminal, and assuming you created a folder named Rosetta in the Downloads folder, type this:
```
cd ~/Downloads/Rosetta
chmod +x ./setup.exe
wine ./setup.exe
```

The first line changes to the folder where you copied the files, the second line sets the permissions of the setup.exe so that it can be run as an executable, and the last line runs it with Wine. You probably don't have to chmod the setup.exe file if you're going to be running it with Wine from the terminal, but it's good practice because you need to do it to be able to double click the file and run it from Nautilus.

If it doesn't work, it should output errors that give some clue as to why it's not working.


Edit: Most people that got good results in the links you provided were using newer versions of Wine than you are. The ones who got it to work on old versions of Wine suggested that they had to capitalize the names of the language pack folders and files before it would work, which means that it has to be on the hard drive. Some people with newer versions of Wine said that it worked perfectly without doing anything special. So you'll probably have to upgrade your wine version or capitalize all of those language pack folder and file names.

---

### Post by Mark Phelps on 2012-02-24
> **briar rabbit said:**
> my 2.0 ver.  is said to work on 8.04, I would guess that it will work on my 10.04

thanks

A SILVER rating means that little of the product will actually work.  The test results in the Wine page often indicates results other folks have had and will provide clues as to what works and what does not.

My general rule to folks is:  if you need to use a Windows app in Linux on a daily basis and rely on it, the minimum rating you need to see in Wine is GOLD.

---

### Post by forrestcupp on 2012-02-24
> **Mark Phelps said:**
> A SILVER rating means that little of the product will actually work.  The test results in the Wine page often indicates results other folks have had and will provide clues as to what works and what does not.

My general rule to folks is:  if you need to use a Windows app in Linux on a daily basis and rely on it, the minimum rating you need to see in Wine is GOLD.

True. But one guy gave it a Platinum rating by doing what I said above. I think it's possible for him to get this working.

---

### Post by philinux on 2012-02-24
Thread moved to Wine forum.

---

### Post by briar rabbit on 2012-02-24
forrestcupp

OK I did what you said.

The terminal comes back with: No such file or directory.

I do not know how to attach a screen shot of the terminal.

The next line in the terminal says: wine ./setup.exe

When I click enter again it says: wine: can not find './setup.exe'

I can see Rosseta in the downloads folder and it has properties and opens, etc.

I copied and paste into the terminal so it must have been right.

I tried it twice. 

many thanks

edit: I do not see wine 1.3 in my synaptic package manger or I would upgrade to it.

---

### Post by forrestcupp on 2012-02-24
It said "No such file or directory" after the **cd** command because you didn't type in the directory name exactly like it is. If that command doesn't work, you won't be in the right directory, and nothing else will work. So I assume that you got all of the files from the CD copied to a folder on your hard drive, right? And from the way you made it sound, you put it in your Downloads folder. Well, I'm using 11.10, and I have no idea how they named things in 10.04. Is the name of your Downloads folder capitalized? If it's not capitalized, then you need to change your **cd** command to not be capitalized. The name has to be exactly right, and capitalization matters. If you can't figure it out, then you can navigate there one step at a time.
```
cd ~
ls
```That will get you to your user's home folder and list the contents of that folder. Look in the list for your Downloads folder and type
```
cd ./*Downloads*
ls
```only substitute the exact name for Downloads. The ls command will list the contents of that folder. Hopefully, your Rosetta folder will be in there, so type
```
cd ./Rosetta
```or whatever the exact name is you created. After that you should be in there, and if you copied all of the files right, you should be able to use Wine to run the setup.exe file. The only problem I could see is if they happened to put setup.exe within another folder, then you would just have to cd into whatever folder it is in.

Also:

If you want to install the latest Wine in 10.04, you need to install the PPA for their repository, because they're not ever going to update the version in the official 10.04 repos. To do that, follow [these directions](http://www.winehq.org/download/ubuntu) on the WineHQ web page. After you get their PPA entered, go to your terminal and type
```
sudo apt-get update
sudo apt-get upgrade
```And it should update Wine to their latest release, which may be a beta. If you're going to do that, I suggest you do it before you try again to install Rosetta Stone. If you update to the latest Wine, Rosetta Stone may work without having to capitalize your language pack files and folders.

---

### Post by briar rabbit on 2012-02-24
OK I did the terminal entries, this is what I got:

ferg@ferg-laptop:~$ cd ./Downloads
ferg@ferg-laptop:~/Downloads$ ls
Rosseta
ferg@ferg-laptop:~/Downloads$ cd ./Rosseta
ferg@ferg-laptop:~/Downloads/Rosseta$ 
ferg@ferg-laptop:~/Downloads/Rosseta$ ./setup.exe
bash: ./setup.exe: Permission denied
ferg@ferg-laptop:~/Downloads/Rosseta$ 

quote:  After that you should be in there, and if you copied all of the files  right, you should be able to use Wine to run the setup.exe file.

When I open the Rosseta folder it has all the language files in it and each one has its own sound and text files that work (each individually) but not as a whole.

I have found a couple other post about RS I am reading as well.

When I did the "cd ./Rosseta" in the terminal shouldn't have listed all the files in that directory/folder?

If I copied all the files from the CD into a folder wouldn't that automatically put them on the hard drive?

thanks

---

### Post by donkyhotay on 2012-02-24
the 
```

cd ./Rosseta

```
got you into the right folder which was the problem previously. Now that you're here finish what forrestcupp told you
```

chmod +x ./setup.exe
wine ./setup.exe

```
you need to do the chmod to tell the system that you want permission to run the file (since it's an application) and you also need to have 'wine' before the name of the file you're running to let the system know it should be run through wine otherwise it will treat it as a linux native application which it isn't.

---

### Post by briar rabbit on 2012-02-24
Wow.

donkyhotay,  I do not know how I missed that.  just another newbie :-)

It setup - as instructed - and when I opened it from the Applications> Wine> Programs; I got the startup screen.  But, no RS until I put the CD back in.

At first I had no sound but a restart and a couple minutes later and the sound came on.

This is actually very good.  I have to put the CD in the drive, start from Wine> Programs (not the desktop icon) and it all works

I will go back over everything I have read and see what I missed to actually put the program on the hard drive.

Thanks to all especially forrestcupp and donkyhotay.

---

### Post by forrestcupp on 2012-02-24
> **briar rabbit said:**
> Wow.

donkyhotay,  I do not know how I missed that.  just another newbie :-)

It setup - as instructed - and when I opened it from the Applications> Wine> Programs; I got the startup screen.  But, no RS until I put the CD back in.

At first I had no sound but a restart and a couple minutes later and the sound came on.

This is actually very good.  I have to put the CD in the drive, start from Wine> Programs (not the desktop icon) and it all works

I will go back over everything I have read and see what I missed to actually put the program on the hard drive.

Thanks to all especially forrestcupp and donkyhotay.
Hey, that's great! I'm glad you got it to work. I don't have a clue how you could tell Rosetta Stone to look on your hard drive. Since I don't have any experience with it, I don't even know how you would do that in Windows. But at least you got it working with the CD.

By the way, did you update Wine with the PPA, or did it just work with Wine 1.0.1, or whatever version you had?

---

### Post by donkyhotay on 2012-02-24
> **briar rabbit said:**
> Wow.

donkyhotay,  I do not know how I missed that.  just another newbie :-)

Don't feel bad, we were all newbies once. Anyone that says otherwise is either forgetful or a liar. (c:

---

### Post by briar rabbit on 2012-02-24
hey forrestcupp,

I still have the same Wine 1.0.1
I read something bad about Wine 2 and RS on winehq.
There 'seems' to be sooo many ways to do the same thing - getting the right results.
Seems again too the more I do the more my list grows.
Anyway I will have time to figure it out - fascinating languages and fascinating Linux.

And yeah donkyhokay, one happy newbie, maybe always a newbie - at one thing or another.

Fascinating community of support, Thanks again.

---

