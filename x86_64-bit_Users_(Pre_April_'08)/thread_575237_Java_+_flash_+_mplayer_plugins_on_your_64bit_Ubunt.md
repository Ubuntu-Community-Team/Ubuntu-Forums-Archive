---
title: "Java + flash + mplayer plugins on your 64bit Ubuntu"
date: 2007-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by LiMaO on 2007-10-13
[B]IMPORTANT, READ THIS:

- The script will run and work under Gutsy, with no problems whatsoever.
- If you had the script installed under Feisty, you may upgrade to Gutsy and will have no problems with the script either. Everything will work perfectly.
- The only change made when upgrading to Gutsy is that it sets your default browser back to the 64bit one. You can still run 'firefox32' to have the same working environment, or re-run the script and use it to set your 32bit firefox as default again.

- With the release of Gutsy, this script is only recommended if you need Java to work, as Gutsy makes flash available through the new plugin installation manager. When Java 1.7 is released (no release date yet) this script will be removed from here.[/B]

Here's a new script for everyone to get Firefox 32bit installed + java + flash + mplayer plugins on their 64bit system.

It's easy to follow (have nice user friendly interaction) and effective.

Any problems with it just let me know.

IMPORTANT:
1) this script have an uninstall option, which reverts the system to how it was before installation. (Everything is put on a single folder, which is deleted upon uninstall)
2) the installation of such files will get you a stable flash (with sound) and java that will not crash on some sites.
3) 32bit Java will be installed through apt-get, and will NOT be removed upon uninstall, because it may be in use by any other application.

Enjoy! :)

**[COLOR="Red"][SIZE="3"]THE SCRIPT HAS BEEN REMOVED, AS SOME PROBLEMS HAVE BEEN FOUND WITH THE PLUGINS WHEN USING FIREFOX 2.0.0.8 - IT WILL BE BACK WHEN EVERYTHING IS FIXED AND WORKING CORRECTLY.[/SIZE][/COLOR]**

---

### Post by Kilz on 2007-10-13
I commend anyone wanting to help. But the script is basically a duplication of effort. [I long ago wrote a script that installs a 32bit firefox and plugins .]("http://ubuntuforums.org/showthread.php?t=202537"). Have you tried your 32bit browser script on Gutsy?
Nspluginwrapper will let flash work on a 64bit browser and mozilla-mplayer also works with the 64bit browser. For the most part the 32bit browser is no longer needed.
The uninstall feature is a good idea, but while it cleans out some things, it litters files all over, and removes just a few of them. You will still have flash, pango, mplayer and other files in place even after the removal. Not only that but it moves the 64bit browser and completely replaces it with the 32bit one. Im not sure thats such a great idea.

---

### Post by LiMaO on 2007-10-13
The uninstall processes also copies back the 64bit Firefox to place, and removes the ENTIRE folder where everything was stored, so NO, you won't have firefox32 + flash, nor mplayer plugins installed after you choose to uninstall everything (only the ones related to your 64bit system. This script does NOT mess up your system). The only file left is the pangorc and java (which was installed by apt-get).

Btw, I myself have used Kilz script, when he used to promote it here in the forums and not on his own site. It was great, but I found too many people having problems with it on IRC (besides that, his new script install applications that presents too many flaws, with java crashing all the time - not a script problem however), so I decided to write this version, which seems to be easier to use and presents fewer options to the user, which is good for newbies (just like the default browser option... as some newbies don't even know how to create a launcher)

Kilz's script are great and highly recommended, although, if you happen to have problem with any of them, just try this one out.

---

### Post by ryanVickers on 2007-10-13
rather nice piece of work!  It seems very simple too - always a good thing ;)

---

### Post by Kilz on 2007-10-13
> **LiMaO said:**
> The uninstall processes also copies back the 64bit Firefox to place, and removes the ENTIRE folder where everything was stored, so NO, you won't have firefox32 + flash, nor mplayer plugins installed after you choose to uninstall everything (only the ones related to your 64bit system. This script does NOT mess up your system). The only file left is the pangorc and java (which was installed by apt-get).
 It may not mess your system, but you said that your script completely removes what it installs. This is not the truth. You may want to create packages that can be removed because there will be files in your system even after you uninstall.

> **LiMaO said:**
> Btw, I myself have used Kilz script, when he used to promote it here in the forums and not on his own site. It was great, but I found too many people having problems with it on IRC (besides that, his new script install applications that presents too many flaws, with java crashing all the time - not a script problem however), If someone has issues with one of my howto's on IRC, they are in the wrong place as I am never in chat. Yes I have moved support for my newest script that installs a 64 bit browser, 64bit java, and flash that works in a 64bit browser to my site. But I still reply to people who post to my old howtos. I still support them almost a year and a half after posting.

> **LiMaO said:**
>  so I decided to write this version, which seems to be easier to use and presents fewer options to the user, which is good for newbies (just like the default browser option... as some newbies don't even know how to create a launcher)I recommend that you create installable packages that include a launcher. That way you wont have to replace the 64bit browser. You will also have problems if someone tries to install other things for the browser from the repos. The things they install will be looking for a 64bit browser. like in Gutsy and the nspluginwrapper setup. Since you have moved it , there will be issues. 
Secondly, how is someone going to upgrade your install when a new version of any of the components are released?

> **LiMaO said:**
>  Kilz's script are great and highly recommended, although, if you happen to have problem with any of them, just try this one out.
Thanks, and your script shows some thought, Im just not sure of the usable life a 32bit browser has anymore. I hope you plan on improving it and supporting it.

---

### Post by LiMaO on 2007-10-13
Kilz, I think you are posting just to defend yourself and to flame others' work, but that's just my humble opinion.

1. The 64bit is never "replaced" by the 32bit browser. The 64bit one is still installed. The link to its binary is renamed, and that's it.

2. If the user wishes to install any other extras to their browsers, it will work flawlessly, as the 64bit browser is still installed and functional.

3. As you said, the life span of such 32bit browser is limited on a 64bit system, with that in mind, a user will not probably have to use any other script, nor update any of the individual components installed by my script.

4. When the user upgrades his/her system, everything will work fine, as the 32bit firefox (along with the plugins) will be kept isolated on a directory in his system (just like unused libraries are kept) - also, the user always have the uninstall option (which yes, will leave some stuff that was installed by apt-get, but that will make no harm).

5. Just to explain one more time, I wrote this because NONE of your scripts would work correctly on my system. And my script does work on my system. Many other people are having such issues, which you are not aware of, because as you said, you are not on IRC. My script has been serving such people, and I'm happy to see they're happy with it.

6. If you don't like it, just don't use it =)

I know this is not a great post, but I had to say it. I just hate it when people want to hold all credits for something, flaming on other people's work.


PS.: you didn't see me saying anything bad at all about your script, but I guess it's now time to remind you of something you told me in YOUR 'support' site:

LiMaO: [SIZE="1"]How do I revert everything that the script did to my system? I mean, as it doesn't seem to have an 'uninstall' option, which files should be deleted and/or uninstalled? For instance, it installs Java by running a .bin file, but what files does that .bin file installs and where? I just want to make sure that everything is back to how it was before running the script, as Java kept crashing on me, just like it did on Firefox. Btw, I do need Java for homebanking and I really don't want to go back to 32bit Ubuntu.
Kilz, nothing wrong with your script, your work to help the community is awesome, just hope you understand it wink
Thanks in advance.
[/SIZE]

Kilz: [SIZE="1"]Code: sudo rm -rfd /usr/local/j2re1.4.2
The above command will remove the java that is only used by the swiftweasel browser. Some java sites will crash. If you want you could try my 32bit firefox.,flash and java script. It installs 32bit versions to your 64bit ubuntu. The java is 32bit java 5.[/SIZE]

As you may have noticed, your answer makes no sense at all to my question. As far as I'm concerned, your script also installs swiftweasel and flash. And deleting the j2re folder doesn't get rid of any of those other stuff.

Also, the script you mentioned, that works like the one I made, would not work on my system. I didn't bother asking for help, because I knew the answer would be as vague as the one you had given me before. One more time, that's WHY I wrote this script of mine.

I don't see the point of you flaming me. Just keep up the great work helping the community, I'll do my part aswell, and it's all fine.

---

### Post by Kilz on 2007-10-13
I asked some questions about a script from someone with 1 post on the forum. I could care less if anyone used anything of mine. But I dont want people exposed to something that may not be safe. If you cant answer questions about the scripts actions do you think anyone will use it?

1. By renaming the 64bit Firefox in /usr/bin to firefox64 and placing your 32bit firefox in its place you are in fact removing it from the system as nothing else will know where it is.
2. I ask you to think about this situation. You have just replaced the 64bit browser in /usr/bin by renaming it and placing a 32bit version there. What happens when someone wants to use the 64bit browser as a base? Your 32bit browser is what it will find and it may not work.
3. In the last 3 months Firefox has seen 3 upgrades. Exactly how will users be notified of your upgrade?
4. But you have lied to people by telling them it removes everything. This leads me to ask, What else have you not told them about? 
5.You are a distinct minority. For the most part people dont use the 32bit browser scripts anymore anyway. The nspluginwrapper and flash script makes a 32bit browser obsolete. 
6.At this point I hope lots of people read your posts before trying it. That should be easy as they are only in this thread.

You received the answer on how to uninstall the java that was causing problems. You got what you asked for. The only other thing was swiftweasel, its a deb file. Everyone should know how to open synaptic and uninstall a deb.

So you didnt ask a question on some problem because you could see into the future and see what I would say about another script? 

No one got flamed, if you cant stand someone asking questions about an install script that newbies will use and suggesting improvements, dont post it.

---

### Post by LiMaO on 2007-10-13
As you said, you could care less about people using your stuff. Actually I DO care about them. I write stuff that suits my needs, but when I provide it to the public, I do worry about what they'll get.

Here are you answers (once again)
1. A symbolic link is not what a system relies on to find what's installed on your system. I thought you were aware of that.

2. If they want to install a 64bit plugin, they'll do it using either synaptic (that DOES know that you have a 64bit system, and DOES know where to place the files - original firefox (64bit) folder) - so that will not break anything.

3. In the next 3 months, a next version of Ubuntu will be already under development, the Sun may have gone off, we may be dead. I think that by then a new script can be re-written if needed, which probably will not.

4. Well, I can make it remove java too, just by adding an apt-get remove command and that's all.

About 5 and 6, they do not deserve my consideration.

And just one question: can't you read?! I didn't ask how to remove Java. I used it as an example. I asked how to REVERT the system, UNinstall EVERYTHING your script did.

Suggesting improvements is one thing, saying that your script should be used, but not mine is not constructive criticism. Specially when you start your post by saying that 'you could care less about anyone using your scripts'.

OH, btw, something I just remembered... making Firefox 32bit the default browser is AN OPTION. The user may choose to keep it as it is though. When checking out others' code, do it PROPERLY.

---

### Post by FredB on 2007-10-14
Your script have no interest at all or nearly.

Flash ? What about nspluginwrapper ?
Mplayer ? Erh... What about VLC  ?

Java ? Just show me a java enabled web site ;)

---

### Post by Urgazhi on 2007-10-14
I have found that Mplayer can play more file types than VLC... (like .rmvb, which VLC cannot (In Linux, or Windows...))

---

### Post by Kilz on 2007-10-14
> **Urgazhi said:**
> I have found that Mplayer can play more file types than VLC... (like .rmvb, which VLC cannot (In Linux, or Windows...))

There is 64bit mplayer and mozilla-mplayer packages in the repos for the browser that already comes with Ubuntu. With nspluginwrapper for flash most users will have everything they need using what is installed by default in ubuntu.
In Gutsy all people will have to do is enter this command. 
```
sudo apt-get install mozilla-mplayer mplayer flash-nonfree
```
To have flash and a media player in their 64bit browser.

---

### Post by FredB on 2007-10-14
> **Kilz said:**
> There is 64bit mplayer and mozilla-mplayer packages in the repos for the browser that already comes with Ubuntu. With nspluginwrapper for flash most users will have everything they need using what is installed by default in ubuntu.
In Gutsy all people will have to do is enter this command. 
```
sudo apt-get install mozilla-mplayer mplayer flash-nonfree
```To have flash and a media player in their 64bit browser.

What to add to this ?

Script are no longer useful. Even if Mplayer plays more files types, it is really hard to setup. VLC works just out of the box ! :)

---

### Post by LiMaO on 2007-10-14
FreD, alright it's no longer useful. Now everytime I needs to access my homebanking I'll give a run to your place, ok?! See ya in a few minutes, as I need to manage some transactions ;)

Just to remember that most banks over the world uses java for their access.

Oh, and YES, all other scripts and java installation attempts on gutsy 64bit would result in browser crashes when accessing some banks. =)

---

### Post by madsmeg on 2007-10-14
Kilz, from an outsiders point of veiw you look like you are just getting pissy and LiMaO is making sense. Stop getting so defensive (dont say your not).

LiMaO stop being so damn argumentative.

Now lets all play like happy penguins :D

---

### Post by LiMaO on 2007-10-19
I suggest you to read the 1st post of this Thread, for new information about compatibility with Gutsy.

Thanks for all the great private messages, and such nice words. It's good to see people are benefiting from the script (even though a few people think no one needs it).

---

### Post by eyelessfade on 2007-10-19
what I'd like to see is a mplayer 32 bit with win32 codecs. Since not all file types play with the 64 version. Files like HD-wmv

---

### Post by slicker on 2007-10-19
This script has broken Ubuntu . All was fine until I installed it. I did a clean install of Gutsy. Now my computer freezes up all the time. I have not installed anything but this script. Help!!!! This script broke everything.

---

### Post by LiMaO on 2007-10-20
Slicker: this script basically creates a folder and put the needed files in there. In no way it can break a system =) Are you sure the script was the only thing installed? Also a linux system almost never freezes. A single application may hang, but that's solved by killing the process. I'm starting to think you're not sure about what you are saying.
Btw, if it really did break your system, just run it again and choose to 'uninstall'.

---

### Post by idby on 2007-10-20
This stupid script messed up my java. It makes the browser that comes with ubuntu crash. Then you cant start it without shuting the computer down. I didnt install anything but Gutsy Gibbon and this stupid script. Even doing its uninstall didnt fix everything. Dose it install some rootkit?

---

### Post by LiMaO on 2007-10-20
idby, home come you just installed Gutsy and the script messed up your java?! I mean, Gutsy doesn't come with Java installed by default. Anyway, I've rechecked the script, tested it myself on two other machines, and also asked another person to check it on his machine. It worked flawlessly, with no problems at all. Anyway, I've re-written some lines, to make sure it's foolproof. Try downloading it again, using the uninstall feature and then install again.
Feel free to write here again if you have any other problem with it.

---

### Post by LiMaO on 2007-10-23
The script will be available again when it works correctly with Firefox 2.0.0.8

Best regards,

LiMaO

---

### Post by ghormax on 2007-10-26
> **LiMaO said:**
> Slicker: this script basically creates a folder and put the needed files in there. In no way it can break a system =) Are you sure the script was the only thing installed? Also a linux system almost never freezes. A single application may hang, but that's solved by killing the process. I'm starting to think you're not sure about what you are saying.
Btw, if it really did break your system, just run it again and choose to 'uninstall'.

since I have installed Ubuntu 7.10, my Linux system **freezes** every time when I try to listen to KSCS ([www.kscs.com](www.kscs.com)) which uses an embedded mplayer and Flash is also loaded. I used to listen to KSCS without problem on my Linux Ubuntu system.

---

