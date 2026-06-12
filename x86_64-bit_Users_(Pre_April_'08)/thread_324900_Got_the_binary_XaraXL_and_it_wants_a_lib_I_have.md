---
title: "Got the binary XaraXL and it wants a lib I have"
date: 2006-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Unterseeboot_234 on 2006-12-24
Hello, am I too chicken to download the 100+ meg of support code to build XaraXL. No telling what dependacies such a **[COLOR="Red"]build-essential [/COLOR]**would need. Not to mention the time involved. However, I did a search and found a discussion about building XaraXL. 
[http://www.karakas-online.de/forum/viewtopic.php?t=6081]("http://www.karakas-online.de/forum/viewtopic.php?t=6081")

One person offered a 64-bit built binary attachment to download and claims it works from the terminal. When I try it, I get

```
user@user-desktop:~$ XaraLX
XaraLX: error while loading shared libraries: libwx_gtk2u_xrc-2.6.so.0: cannot open shared object file: No such file or directory

```

Yet, I have those libs installed using the Add/Remove "apt-get GUI". However, from Terminal I cannot find anything

```
user@user-desktop:~$ locate XaraLX
user@user-desktop:~$
user@user-desktop:~$ locate libwx_gtk
user@user-desktop:~$

```

The XaraLX is in my Home folder. libwx_gtk2u_xrc-2.6.so.0 is in my usr/lib64

Is there any tweak I can do?? Like putting in symbolic link or moving my binary of Xara?

Thanks

---

### Post by kuja on 2006-12-24
I don't know about your problem, but if locate doesn't seem to find it, try rebuilding the locate database
```
sudo locate -u;
```

---

### Post by John Jason Jordan on 2006-12-24
> **Unterseeboot_234 said:**
> Hello, am I too chicken to download the 100+ meg of support code to build XaraXL. 
I noted at the end of the discussion at 

[http://www.karakas-online.de/forum/viewtopic.php?t=6081](http://www.karakas-online.de/forum/viewtopic.php?t=6081)

Chris Karakas said just to download XaraLX and then run it from a command line. I have a fast connection, so I downloaded it, then tried to run it. All that happened was:

bash: XaraLX: command not found

So evidently Chris is not correct. Still, it's an executable file. I'm too new to Linux to want to try the stuff you did.

---

### Post by AgenT on 2006-12-26
Either use the Xara that is already in the Ubuntu (Edgy) repository or download the newest binary tar.bz2 file. Xara development is dead right now so the old binary is actually exactly what you will get if you compiled. This makes compiling not worth it right now.

The command not found happens because your binary is 1) not in any known path and 2) is lowercase. Because of #1, you have to be in the same directory as the binary file. Because of #2, you have to type:
```
xaralx
```The binary file is located in xaralx/bin/

---

### Post by John Jason Jordan on 2006-12-26
> **AgenT said:**
> Either use the Xara that is already in the Ubuntu (Edgy) repository or download the newest binary tar.bz2 file. Xara development is dead right now so the old binary is actually exactly what you will get if you compiled. This makes compiling not worth it right now.

The command not found happens because your binary is 1) not in any known path and 2) is lowercase. Because of #1, you have to be in the same directory as the binary file. Because of #2, you have to type:
```
xaralx
```The binary file is located in xaralx/bin/

Thanks for the suggestions, but I still can't get it working.

1) The file I downloaded, which appears to be the binary file, is XaraLX, not xaralx. Maybe it's not really the binary file. If so, where can I get the real binary file?

2) I left it in my download folder, which is /home/jjj/Desktop. From the command line I navigated to the Desktop folder before giving the command. I figured that if it worked I would move it someplace more logical later, (like /bin), then make a launch entry for it.

3) There is no XaraLX (or xaralx) listed in Synaptic. That's because I'm on Dapper AMD-64, not Edgy, so I don't have the Edgy repositories. 

So, the question now is, will it run on Dapper? I don't see why not, but that's the first question. Assuming the answer is yes, can I add the repository where it is located so that it will appear in Synaptic? I know how to add a repository with the Synaptic GUI or manually by editing the sources file, but I need the URL for the repository and the key.

And if I can't add the repository (Synaptic makes things so easy!), then where can I get the tar.bz2 file?

Thanks!

---

### Post by AgenT on 2006-12-26
> **John Jason Jordan said:**
> 1) The file I downloaded, which appears to be the binary file, is XaraLX, not xaralx. Maybe it's not really the binary file. If so, where can I get the real binary file?
**[Download Xara Xtreme (version 0.7 Revision 1764 Built 14-Nov-06 18:00)]("http://downloads.xara.com/opensource/xaralx0.7_rev1764.tar.bz2")** (Tar Bzip2 Archive - 18MB)

> **John Jason Jordan said:**
>  2) I left it in my download folder, which is /home/jjj/Desktop. From the command line I navigated to the Desktop folder before giving the command. I figured that if it worked I would move it someplace more logical later, (like /bin), then make a launch entry for it.Two things you forgot to do. 1) extract the archive you downloaded. To do this, on your Desktop, right click on file -> Extract Here. This will create a xara folder. 2) Navigate into this new folder and, as I mentioned earlier, go into the **bin** folder.

So assuming you extract to your Desktop and the new folder is xaralx your whole path would be:
```
/home/jjj/Desktop/xaralx/bin/
```Now from that bin folder, type this:
```
./xaralx
```If this does not work, then you are not in the correct folder or the binary name is different. Use the command ls to view the directory:
```
ls
```> **John Jason Jordan said:**
>  3) There is no XaraLX (or xaralx) listed in Synaptic. That's because I'm on Dapper AMD-64, not Edgy, so I don't have the Edgy repositories. Besides official distribution (Ubuntu, Debian, etc.) repositories, there are no Ubuntu (or even Debian) repositories that are maintained by Xara or anyone else.

> **John Jason Jordan said:**
>  So, the question now is, will it run on Dapper? I don't see why not, but that's the first question. Assuming the answer is yes, can I add the repository where it is located so that it will appear in Synaptic? I know how to add a repository with the Synaptic GUI or manually by editing the sources file, but I need the URL for the repository and the key.Xara should run on Dapper. No you cannot add any repositories because they do not exist. See answer to the question above. Adding the Edgy repository would break your system because it would automatically upgrade a TON of packages you do not want upgraded.

One word of warning: DO NOT move your xara bin file to /bin or any other system wide folder. You are asking for major trouble if you do this. And if you do want to do this, it should go into /usr/local/bin and NOT /bin. But you should not even do this. If you want, just move your extracted folder somewhere in your home folder where it does not bother you, and create a Launcher. For example, right-click on Desktop -> "Create Launcher" then enter the full path to your binary in the "command" field (or just click "browse" and browser to it). If you want you can also change the icon to the xara one in that same menu. The xara icon is located in the top directory of the program. This means in the same folder that was created when you extracted xara (xaralx/bin/ has your binary, xaralx/ has your icon called xaralx.png).

---

### Post by John Jason Jordan on 2006-12-27
> **AgenT said:**
> **[Download Xara Xtreme (version 0.7 Revision 1764 Built 14-Nov-06 18:00)]("http://downloads.xara.com/opensource/xaralx0.7_rev1764.tar.bz2")** (Tar Bzip2 Archive - 18MB)
Two things you forgot to do. 1) extract the archive you downloaded. To do this, on your Desktop, right click on file -> Extract Here. This will create a xara folder. 2) Navigate into this new folder and, as I mentioned earlier, go into the **bin** folder.
Got stuck here. I downloaded the file, no problem. But Archive Manager says "archive type not supported." I've never had a problem before, but Archive Manager does not like xaralx0.7_rev1764.tar.bz2.

Is there another way to unarchive it?

---

### Post by Unterseeboot_234 on 2006-12-27
Hey, I just wanted to add some more of my experiences with that binary. I downloaded the tar files and tried the build. The build wants the next version of C++, found in edgy. I'm Drake. Well, I forced the install on whatever C++ library. apt-get really got excited and said I had 6 broken links... Fix? Yeah, why not. CRASH. Ubuntu still worked, but everything else stopped working. Reformat. Reinstall. This time do backup of /home, ~/.

I looked around on the net. Xara is part of CoralDraw now. The Windows package for Xara costs $70. Add-on all the other packages to make it Xara Pro and you're out $380. I went back to using Inkscape. Sure would like to use Xara. I'll try moving the built binary I downloaded into /bin to see if that changes anything. Last time I had it going from /home and it just couldn't find the libraries.

If you're serious about building, download **build-essential **and the kernel source packages

from the terminal
```
~$ uname -r
2.6.15-27-amd64-generic

```

and then from the terminal
```
~$ sudo apt-get install 2.6.15
```

which gave me version -26 and version -27 of the linux kernal. Which was useful later on to build my 1394 firewire connection as a **make dev** to my dv camera. My version of Kino works now. I know why now. Kino could never anticipate all the different set-ups between a computer and external devices.

Yeah, I want Xara. If a sym link can't do this built binary, I'll wait. In the meantime, I'll be clear in my mind which backup worked before I made a mess.

---

### Post by AgenT on 2006-12-27
> **John Jason Jordan said:**
> Got stuck here. I downloaded the file, no problem. But Archive Manager says "archive type not supported." I've never had a problem before, but Archive Manager does not like xaralx0.7_rev1764.tar.bz2.

Is there another way to unarchive it?Archive manager does support tar.bz2. Either your download was corrupt or you were trying to uncompress the archive before the download finished. And then there is also the possibility that you removed tar (very highly unlikely) or that the version of archive manager you are using has a bug.

You can use tar the command line program to uncompress it. Go into the folder with the archive and, assuming the archive name is xaralx0.7_rev1764.tar.bz2 type:
```
tar -xvvjf xaralx0.7_rev1764.tar.bz2
```the -x is "e**x**tract", -v is for "**v**erbose", -**j** is for "bzip2" (my guess is they ran out of letters) and -f is for "**f**ile". Having two v's just makes tar more verbose.

---

### Post by John Jason Jordan on 2006-12-27
> **AgenT said:**
> Archive manager does support tar.bz2. Either your download was corrupt or you were trying to uncompress the archive before the download finished. And then there is also the possibility that you removed tar (very highly unlikely) or that the version of archive manager you are using has a bug.

You can use tar the command line program to uncompress it. Go into the folder with the archive and, assuming the archive name is xaralx0.7_rev1764.tar.bz2 type:
```
tar -xvvjf xaralx0.7_rev1764.tar.bz2
```the -x is "e**x**tract", -v is for "**v**erbose", -**j** is for "bzip2" (my guess is they ran out of letters) and -f is for "**f**ile". Having two v's just makes tar more verbose.
Thanks again, but I still can't unarchive it. I agree that Archive Manager should support tar.bz2, because I'm sure I have unarchived tar.bz2 files before. But it still won't touch this file.

To troubleshoot, first, I double-checked the name and it matched your code above. So I copied and pasted your code into a terminal window. That gave me:

jjj@Devil5:~/Desktop$ sudo tar -xvvjf xaralx0.7_rev1764.tar.bz2
tar: bzip2: Cannot exec: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

So then I double-checked in Synaptic and tar is definitely installed. Synaptic says it is version 1.15.1-2ubuntu2.1 and that that is the latest version in the repository.

Then I went back to the command line and did a ls. I copied the name of the file and pasted it into the command, just to be absolutely sure I didn't mistype it. Same error message. And then I tried sudo, just in case -- I'm not good at understanding permissions, so I always try sudo when something doesn't work. Still same error message.

Finally I re-downloaded the file and tried all the above again. I still get the same error message above.

Note: The file I downloaded is 16.8 MB. The only conclusion I can draw at this point is that the file on that site is corrupt or that it was created incorrectly.

---

### Post by AgenT on 2006-12-27
Very strange. It looks like you are having problems with bzip2 support in tar. Try the earlier version of Xara:
[**Download Xara Xtreme (version 0.7 Revision 1692)**]("http://downloads.xara.com/opensource/RecomXaraLX0.7_rev1692.tar.bz2") (Tar Bzip2 Archive - 19MB)

UPDATE: You mention that your download size was 16.8MB. Xara's website says it should be 18. That is a pretty big difference. It looks like you are not downloading the complete file. Before you attempt to install the version linked above, try this:

Make sure you have enough disk space! In terminal, type this:
```
df -h
```
The above will tell you how much disk space is still remaining. If you do not know how to read the output, paste it here but wrap it in code tags.


Once you are sure that you have enough disk space, do this:

Remove all your old xara files and in your terminal navigate into your Desktop folder. Then type the following to download the newest version of Xara using wget:
```
wget http://downloads.xara.com/opensource/xaralx0.7_rev1764.tar.bz2
```

---

### Post by John Jason Jordan on 2006-12-27
> **AgenT said:**
> Very strange. It looks like you are having problems with bzip2 support in tar. Try the earlier version of Xara:
[**Download Xara Xtreme (version 0.7 Revision 1692)**]("http://downloads.xara.com/opensource/RecomXaraLX0.7_rev1692.tar.bz2") (Tar Bzip2 Archive - 19MB)

UPDATE: You mention that your download size was 16.8MB. Xara's website says it should be 18. That is a pretty big difference. It looks like you are not downloading the complete file. Before you attempt to install the version linked above, try this:
Make sure you have enough disk space! In terminal, type this:
```
df -h
```
The above will tell you how much disk space is still remaining. If you do not know how to read the output, paste it here but wrap it in code tags.
Once you are sure that you have enough disk space, do this:
Remove all your old xara files and in your terminal navigate into your Desktop folder. Then type the following to download the newest version of Xara using wget:
```
wget http://downloads.xara.com/opensource/xaralx0.7_rev1764.tar.bz2
```
OK, first I did the df -h command. It said I had 31 GB free space. That sounds about right to me, as I knew I had lots of free space left.
Then I used the wget command and it downloaded the 1764 version. Nautilus said it is also 16.8 MB, although I noticed during the download that in bytes it was 17.6-something. I tried to untar it, but again got the same error messages.

So then I downloaded the 1692 version. When I tried to untar it I got exactly the same error messages.

Right now I think I need to go find another tar.bz2 file that is unrelated to Xara. If I can untar it, then there is no problem with my tar. If not, then the problem is in my tar and I'll have to figure out what is going on. The problem must be either in the Xara tar.bz2 files or in my tar. It has to be one or the other.

---

### Post by AgenT on 2006-12-28
I just downloaded xaralx0.7_rev1764.tar.bz2 and extracting it worked using:
```
$ tar -xvvjf xaralx0.7_rev1764.tar.bz2 
```(notice no sudo, but it also works with sudo)

Output of ls -l:
```
 $ ls -lh xaralx0.7_rev1764.tar.bz2 
-rw-r--r-- 1 agent agent 17M 2006-12-28 09:37 xaralx0.7_rev1764.tar.bz2
```Nautilus says the filesize is: 16.8 MB (17638733 bytes).

---

### Post by John Jason Jordan on 2006-12-28
> **AgenT said:**
> I just downloaded xaralx0.7_rev1764.tar.bz2 and extracting it worked using:
```
$ tar -xvvjf xaralx0.7_rev1764.tar.bz2 
```(notice no sudo, but it also works with sudo)
Thanks. That told me there was something wrong with my tar. I opened Synaptic and reinstalled file-roller, but still no joy. Then I reinstalled bzip2 and tar, and finally it worked!!

Then I followed the rest of your instructions and Xara is now happily running! Yay!

I'll probably never know what was wrong with my archiving tools. Oh well. All is fine now and I have you to thank for your patience in helping me figure it out!

---

### Post by AgenT on 2006-12-28
You are very welcome. It is rather strange that your tar was broken. Maybe it was the [update on tar from about 4 weeks ago]("http://ubuntuforums.org/showthread.php?t=308216"). I use tar on an almost daily basis and did not experience any problems. Then again, I never use bzip2 option in tar because it is just way too slow (tar gz is good enough).

---

### Post by Unterseeboot_234 on 2006-12-29
Hey thanks! Because of you two I got it to go. Strange! What I found out is this:

1. The download of xaralx0.7_rev1764.tar.bz2, which is a built 32 does NOT work by right-click the icon of the download --> Properties --> Permissions --> [check] OWNER Executable. And then double-click the archive. Try to run that extracted package from Terminal, 
/bin/xaralx
BASH xaralx not found.
**But**

2. **tar -xvvjf **xaralx0.7_rev1764.tar.bz2 runs as a Terminal extraction, you see it is setting the proper permissions as it unpacks. Afterwards /bin/xaralx runs!!!

I originally wasted a whole day trashing my ubuntu install by trying to build the 64-bit version, but sadly there are dependancies that Dapper cannot accomodate.

Thanks, thank you, Danke!

---

### Post by AgenT on 2006-12-29
> **Unterseeboot_234 said:**
> 
/bin/xaralx
BASH xaralx not found.

Just a quick correction: that should be ./bin/xaralx or bin/xaralx and not /bin/xaralx unless you specifically put xaralx binary into /bin which you should not do unless you want to break your system in the future.

---

