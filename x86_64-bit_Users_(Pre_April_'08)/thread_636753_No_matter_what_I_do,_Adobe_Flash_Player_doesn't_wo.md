---
title: "No matter what I do, Adobe Flash Player doesn't work!?!"
date: 2007-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by markjs on 2007-12-10
I installed in in synaptic, and it doesn't work (on my favorite site NFL.com).  I tried installing it in the link that's provided by NFL.com, and when I download and install the tar.gz file, it says my architecture (x86_64) is not supported.  So I downloaded ies4linux and it doesn't work (though it said it did install the plugins).  I un-installed, and reinstalled in synaptic, and it didn't work.  I closed all browsers, un-installed it in synaptic, re-installed it in synaptic, rebooted, and it still didn't work.  The thing that seems insane to me is that I had to install Ubuntu a second time because the first time the partition was the wrong size and I wanted more space so I just reinstalled using the whole hard drive.  But the first time I had it installed flash player was working just fine.....I am at wits end, please help!?!  Thanks in advance!

---

### Post by coskierken on 2007-12-10
Here you go!  Follow this link and you will put it in.  I used the method listed below, but list the link also.  This worked for me and I have not gone to a flash site that it does not work on.  :lolflag:

Download Flash
Download the .tar.gz Flash player 9 from Adobe site  [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) 

Run nspluginwrapper
Copy “libflashplayer.so” and “flashplayer.xpt” to /usr/lib/mozilla-firefox/plugins/ 

Shutdown Firefox and run this: 

nspluginwrapper -i /usr/lib/mozilla-firefox/plugins/libflashplayer.so
Now flash should work! 

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#head-74ed36356cdab258889ed4e9ad010f068e13ff38](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#head-74ed36356cdab258889ed4e9ad010f068e13ff38)

---

### Post by markjs on 2007-12-10
Well that would be all great if I knew what I was doing, but from those instructions being a total noob, I get BARELY a vague idea of what you are talking about.  I have no idea where I would find “flashplayer.xpt” because when I download it from adobe there are only two files once it is extracted; they are "flashplayer-installer", “libflashplayer.so”.  I have NO idea at all how one is to copy a file from one folder to another?  Some arcane terminal commands I don't know since I am a noob?!?  I can use "sudo" but I really have no idea how to become root in terminal because when I try it won't accept any password I used and I only have one I know of.

I am about to go back to windows and wait yet ANOTHER 5 years till Linux actually catches up in as much as "ease of use" ....

Well it's not that bad, ***yet***, but it is damn frustrating!

---

### Post by coskierken on 2007-12-10
You say you can't remember your password you created when you installed Ubuntu?  I am not sure what to do with this except install again and write down the password you create.  Maybe someone out there can help more on this.  Many people have reported this bug in the install via Synaptic.  I followed directions via Kilz (loads of experience!!!!) and could not get mine to work until I found the link I told you to follow.  

From this point on, I will give  you step by step on getting flash to work.

1. Once you have password, open a terminal and type "sudo su" and hit enter.  This will prompt for password.  Once accepted, you are now the superuser.  

2.  Type "nautilus" and enter.  This will give you a file manager in superuser mode.  You will use this when you pull the file from another nautilus you open from 'Places' , 'My Computer'.

3. In the 2nd nautilus, go to the directory where the tar.gz file you download from macromedia.  If you keep clicking on the tar.gz file you will get to the point (with Archive Manager) of seeing the libflashplayer.so file. 

4. In the superuser nautilus you have opened, go to the /usr/lib/mozilla-firefox/plugins/ directory.  From the 2nd nautilus, pull the file over to the directory above (in the superuser nautilus) and drop it there.  

5.  Now, make sure all Firefox browsers are closed. 

6. Once this file is copied, you close the nautilus superuser and return to the terminal window.  In here type:

nspluginwrapper -i /usr/lib/mozilla-firefox/plugins/libflashplayer.so

and enter and then start your Firefox and all should be well.  

7.  If you know your paths to the libflashplayer.so file, you can circumvent all this by just becoming the superuser via sudo su and typing:

cp libflashplayer.so  /usr/lib/mozilla-firefox/plugins/ 

enter and then type:

nspluginwrapper -i /usr/lib/mozilla-firefox/plugins/libflashplayer.so

Important to remember is the path to the file you want to copy.  You do not need the other file in the tar.gz file at all.  If for some reason you cannot see the /usr/lib/mozilla-firefox/plugins/ directory (it could be hidden and I can't remember if it is hidden or not), put the file in a folder somewhere else and remember the path to it as you will use this path in the nspluginwrapper line.


Good Luck and don't give up!  I pulled a few hairs out over this! Let us know if you need anything else.  I hope this helps and that I put everything in the correct order!!
:lolflag:

---

### Post by markjs on 2007-12-10
Thank you SO MUCH.  The second set of instructions was SO easy, and now I know how to do things like this in the GUI for the future.

Still being a noob though I had the same problem with ies4linux, but I ended up figuring out that I just download the Windows version for that, and now that works great.  This is what seems to be nice about Ubuntu.  It is aimed at replacing Windows and friendly enough that noob dummies like me can learn easily and people involved seem to be MUCH friendlier than the people I used to deal with back when I was trying even Redhat Or SuSE, or Mandrake, and certainly not the stuck up "if you don't know command line interface I'd rather make fun of you than help you" types I met while trying to learn Debian.  I really appreciate your help and the way you give it.  It means a lot.

You see  I am a Windows professional, and I deal with idiots all day long and I have to be nice to them or I'd lose my job.  Give me a windows box with a problem and I can fix it, and the one and only time I failed to, it was because the woman was convinced that since I didn't get all the ghosts out of the machine the first time that I was incompetent.

The thing about Linux is, is that I have always wanted to use it for my personal use as a Windows replacement.  I have tried it many times over the years and I saw progress, but I never saw the "light at the end of the tunnel" anywhere near as much as I do with Ubuntu 7.10 "Gutsy Gibbon".  I decided that at the point where I could use it as a full windows replacement is the point at which I would start recommending it to "tru dummies".  I could have learned Linux at any point in the past, but I did not want to bother until it was a viable Windows replacement for the common man.  You see i have never had that "think different" mentality, nor have I had that anti Windows mentality.  Windows 98 was pretty decent for it's era, and XP was Micro$oft'$ crowning achievement.  I love XP, and it is a very good OS, and especially for the wealth of idiots that use computers. 

Enter Vi$ta, which is an OK OS.  Honestly it isn't near as bad as ME was no matter what some say.  But it's nowhere near as good as XP was, and I see it for what it is, Micro$oft$ way to force the market to ply their game, and since the republican administration green lighted the monopoly back when the case was going on, they are a monopoly and they can do that.  Vi$ta is something I recommend to home users.  Its is and should be a complete failure in the business sector.  If I had a business customer ask I would send the Linux's way, or tell them to stick with NT, 2000, or XP (whatever they currently have).  But now when a home user comes to me, depending on his/her needs, I am pleased to say that I can also endorse Ubuntu, and actually recommend it over Vista for some upgraders.

In the past most of the Linux geeks I asked for help had this attitude.  The attitude that all versions of Windows were garbage, and anyone who didn't pour over arcane "man pages" and know all manner of arcane command line 'nix commands was just an idiot too pathetic to waste their time helping.  You see if I had the desire, I could have easily learned that on my own by doing just that, but my only reason for interest was to find a Windows replacement for the common man.  Ubuntu, and the people on this board have finally shown me that day is here. 

So any time you come across a noob, be kind, be gentle, because if you want Linux to gain widespread acceptance and Challenge the Micro$oft monopoly, you only hurt the cause when you lose patience with noobs.

---

### Post by coskierken on 2007-12-10
No problem:) We are all here to help.  I had to work through many problems and got most of the help through this forum.  Keep on experimenting and working things out.  I seem to do a few reloads as I test various things.  One indispensable tool is uBackup!  It is is the cafe and a buddy of my developed it.  Get it, use it, and put the files it creates in a safe place.  Believe me, it is a hair saver!  Do a search on the forum for it!

---

### Post by daradib on 2007-12-10
See this for more information: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

