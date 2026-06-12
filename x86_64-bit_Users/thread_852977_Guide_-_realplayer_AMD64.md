---
title: "Guide - realplayer AMD64"
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by jimmy the saint on 2008-07-08
********THIS GUIDE IS OBSOLETE.  THERE IS NOW A VERSION IN THE REPOSITORIES AND YOU CAN NO LONGER DOWNLOAD .BIN FILES FROM HELIX.  USE THE REPOS INSTEAD (SYNAPTIC/APT-GET)**********

Here is how I did it.  I haven't tried the plugins and chose not to mess with the "browser helpers" as I have heard they are problematic, and I am fine with video being opened in a separate window.  Much of this is from other guides.  essentially, with the 64 bit build, the process is similar to the 32 bit one.

1)  Get latest AMD64 .bin from [http://forms.helixcommunity.org/helix/builds/?category=realplay-current]("http://forms.helixcommunity.org/helix/builds/?category=realplay-current")

2)  Save it to home directory
3)  Make it executable
```
chmod a+x realplay* 
```
4)  install it
 ```
./real*
```
Note:  If you get an error about libstdc++.so 5, install the package libstdc++ 5 via synaptic or apt. then try again
5)  Just go through the installer.  Don't change the install directory or anything, it worked fine for me.
6)  Make the install directory usable by your.  (For some reason it is restricted to root access, so when you open a link to a real file, you cannot select the program)
```
cd /usr/local/real/
```
then
```
sudo chmod 755 RealPlayer
```

Now the first time you select a link to a real media file, you will need to navigate to that folder and select the program as the default to play that file type.  You will only need to do it once if you select the checkbox that makes it the default.

I hope this helps someone!  If you see an error, or something I did that could have been done better let me know.  I am still learning so feel free to grade me!  Just be nice about it.:KS

Note::  It has been brought to my attention that the default install directory has been changed. When the installer gets to confirming the install directory, just make a note of it and do everything I mentioned to that directory rather than the one I listed above.  I don't know why it changes, but I don't want to download every nightly build to confirm the directory and update this tutorial every time it changes.  As long as you make a note of the install directory, all the steps are valid to that directory.  So for example, if the install directory is /usr/blah/bleh/real, just pretend my instructions are for that directory (that is a totally made up directory for example purposes only!!!).  If you have trouble, post a question here and I will do my best to help you!! 

JTS

---

### Post by Tubes6al4v on 2008-07-08
When I installed the Linux-based Real Player, it was only the player and .rm codec. I already had that from the "Comprehensive Multimedia Thread". What I want is the MP3 player support that the Windows  version has. Does your set-up have that?

---

### Post by jimmy the saint on 2008-07-08
I doubt it.  Essentially the only real reason to install realplayer at all on linux systems (as far as I know) is to be able to play real media files.  There are ways to get other players to kind of work for them, but it is a pain and video never works, only audio.  The linux version is a lot lighter than the win version.  For MP3 player support I would recommend Amarok, Songbird or one of the many programs you can find specifically for the task of ipod management.

---

### Post by sonnet on 2008-08-24
Hi

I followed your guide but I get an error, maybe I did something wrong or misunderstood your guide.
Here's the problem:
-I downloaded the file from the site and saved onn the desktop.
The I used the command:
chmod a+x realplay*
and
./real*
As I was missing libstdc++ I had to install it through synaptic.I retyped the command again and it worked (I didn't change anything as suggested), creating a folder on my desktop named "Reaplayer".
I checked permission on this folder and I had permission on it.
The problem is that the folder /usr/local/real/ was not created
and I couldn't xomplete the installation.
Here's what the command ./real* return to me on the terminal:

Extracting files for Helix installation........................

Welcome to the RealPlayer (11.1.0.1188) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...
Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/giuseppe/Desktop/RealPlayer]: 

You have selected the following RealPlayer configuration:

Destination:            /home/giuseppe/Desktop/RealPlayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: f


Copying RealPlayer files...No write-permission to  /etc/profile.d ...skip.
Succeeded.
installing application icons resource...
installing document icons resource...
.Succeeded.
Configuring Mozilla...
Installing .mo locale files...
Setting selinux context...
/usr/share or /usr/bin no write-permission...skip.

RealPlayer installation is complete.

---

### Post by jimmy the saint on 2008-08-24
It looks like they changed the install directory.  When it comes to the point in the installation that it asks for the install directory, just use that one instead.  For the rest of the install, simply substitute that directory for the one I mentioned.  It seems that they change the default install directory periodically (I'm not smart enough to know why!).  All the steps are the same, you simply have to pay attention to which directory they are using.  I will add a note to the tutorial about this rather than change it every time they release a new build.

Make sure you run the installer using sudo!!!  this is necessary for the installer to have access to the files in question!!

---

### Post by mhenriday on 2008-11-29
**Jimmy the saint**, I've just tried following your instructions above to install the  **realplay-11.1.1.1247-linux-2.6-glibc23-amd64.tar.bz2** package, but the response to :```
./real*
``` wasn't quite what I expected :> bash: ./realplay-11.1.1.1247-linux-2.6-glibc23-amd64.tar.bz2: det kår (sic !) inte att köra binär fil [it is not possible to run the binary file]When I then tried ```
sudo ./real*
``` I got > ./realplay-11.1.1.1247-linux-2.6-glibc23-amd64.tar.bz2: 1: Syntax error: Unterminated quoted stringAny suggestions as to what I'm doing wrong and how the mistake might be remedied ?...

Henri

---

### Post by jimmy the saint on 2008-11-29
Unfortunaltely, They are no longer putting .bin files up for download for some reason.  In order to install realplayer using the one you downloaded would require compiling the software from the source contained within the the .gz file.  You can find instructions for that process elsewhere. 
For your needs, though, I would suggest simply installing the version in the repositories as Ubuntu has FINALLY added a working version.  Simply open synaptic and search for real.  Realplayer should show up and you can install it that way.

---

### Post by John Jason Jordan on 2008-11-29
> **jimmy the saint said:**
> Unfortunaltely, They are no longer putting .bin files up for download for some reason.  In order to install realplayer using the one you downloaded would require compiling the software from the source contained within the the .gz file.  You can find instructions for that process elsewhere. 
For your needs, though, I would suggest simply installing the version in the repositories as Ubuntu has FINALLY added a working version.  Simply open synaptic and search for real.  Realplayer should show up and you can install it that way.

Can't find it in Synaptic in Hardy, x86_64. I have most of the repositories enabled, but evidently I'm missing one. Which repository has the Realplayer package?

---

### Post by Arup on 2008-11-29
Correct me if I am wrong, the Helix player which is in the repos is supposed to play real media files?

---

### Post by John Jason Jordan on 2008-11-29
> **Arup said:**
> Correct me if I am wrong, the Helix player which is in the repos is supposed to play real media files?

It doesn't play all of them. Realplayer.com and helix.com are separate organizations but related. Helix is pure open source. Realplayer takes the open source code and adds proprietary features to enable playing other proprietary formats, e.g., MP3 files.

---

### Post by Arup on 2008-11-30
> **John Jason Jordan said:**
> It doesn't play all of them. Realplayer.com and helix.com are separate organizations but related. Helix is pure open source. Realplayer takes the open source code and adds proprietary features to enable playing other proprietary formats, e.g., MP3 files.

Thanks for the clarification.

---

### Post by drs305 on 2008-11-30
> **John Jason Jordan said:**
> Can't find it in Synaptic in Hardy, x86_64. I have most of the repositories enabled, but evidently I'm missing one. Which repository has the Realplayer package?

It's in the medibuntu repository.
If you haven't enabled it, add the Medibuntu repository from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"):

Here is the code for Intrepid. For other versions, see the link above as the instructions are version-specific.
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by John Jason Jordan on 2008-11-30
> **drs305 said:**
> It's in the medibuntu repository.
If you haven't enabled it, add the Medibuntu repository from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"):

I still have Hardy on my laptop so I went to the Community page above and got the terminal commands for Hardy. They ran without error. Then I opened Synaptic and searched on "realplayer." All I got was a Konqueror plugin. 

On the Community page there is a link to the list of packages available for Hardy here:

[http://packages.medibuntu.org/hardy/index.html]("http://packages.medibuntu.org/hardy/index.html")

But Realplayer is not on the list. I have Intrepid on my desktop computer and, after doing the command line code for Intrepid it does find the Realplayer package. I'm assume that the Realplayer package is only in the Intrepid repositories.

---

### Post by drs305 on 2008-11-30
> **John Jason Jordan said:**
> But Realplayer is not on the list. I have Intrepid on my desktop computer and, after doing the command line code for Intrepid it does find the Realplayer package. I'm assume that the Realplayer package is only in the Intrepid repositories.

I went to the medibuntu packages lists and you are correct - it doesn't appear RealPlayer is available in the hardy repository.
[http://packages.medibuntu.org/]("http://packages.medibuntu.org/")

---

