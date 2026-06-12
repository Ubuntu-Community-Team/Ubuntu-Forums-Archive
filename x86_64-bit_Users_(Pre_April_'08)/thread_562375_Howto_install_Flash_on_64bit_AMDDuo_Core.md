---
title: "Howto install Flash on 64bit AMD/Duo Core"
date: 2007-09-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by tobyarnett on 2007-09-28
OK for what ever reason I had a hard time sorting through all the howto's. I know there are plenty of them out there but hopefully this is just another spin on how to cut through the BS and install what you want. Flashplayer to work on your 64bit Ubuntu system. Note: DO NOT have Firefox open while  you are doing this.



1.      Use wget to download rpms for nspluginwrapper:

```

sudo wget http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.3-1.x86_64.rpm
sudo wget http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.3-1.x86_64.rpm

```

2.      Download alien to convert .rpm to .deb

```
sudo apt-get install alien
```


3.      Go into the folder with the downloaded .rpm files and convert the packages 

```
sudo alien nspluginwrapper-0.9.91.2-1.x86_64.rpm 
sudo alien nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm
```

4.      Install the packages

```
sudo dpkg -i nspluginwrapper-0.9.91.2-1.x86_64.deb 
sudo dpkg -i nspluginwrapper-i386-0.9.91.2-1.x86_64.deb
```

5.      Download flashplayer from adobe using wget:

```
sudo wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz

```

6.      Go into the folder with the downloaded file and untar it

```

tar -xvzf install_flash_player_9_linux.tar.gz

```

the &#8220;install_flash_player_9_linux&#8221; folder has been created


7.     Move the 2 files &#8220;libflashplayer.so&#8221; and &#8220;flashplayer.xpt&#8221; from that folder into the /usr/lib/mozilla/plugins folder

```

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo cp flashplayer.xpt /usr/lib/mozilla/plugins/

```

8.      Use the following command to make 32bit compatible with 64bit

```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

should return no errors. Look in your ~/.mozilla/plugins and you should see: npwrapper.libflashplayer.so

9,      Copy the file npwrapper.libflashplayer.so into the folder /usr/lib/mozilla/plugins/

```

cd ~/.mozilla/plugins/
sudo cp npwrapper.libflashplayer.so  /usr/lib/mozilla/plugins/

```

10.      Create a link or copy the file into /usr/lib/mozilla-firefox/plugins/

```

sudo cp npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/

```

and it should work.

---

### Post by John.Michael.Kane on 2007-09-28
This must be for feisty??  As these steps are not needed under Gutsy64bit.

I have to ask

1) Why write a howto that does the same thing as this [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)?

2) You have seven posts of which none are asking for help with installing flash under 64bit. Yet you claim having a hard time sorting through all the howto's. Would it not have been easier to ask throes in the know about the subject for help before embarking on writing a howto?

3) Has this howto been throughly tested before posting, and do you plan to offer support to those who use it? Or is it use at your own risk with no support from you?

---

### Post by tobyarnett on 2007-09-28
1) Yes this is for Fiesty

2) Why write the howto: because I was already writing it as I went step by step to resolve my issue, and I did not see the above link till you just linked it. 

3) No I don't believe it would of been easier to ask for help, as most people that respond ask simple one line responces like try "try using apt-get install flash-nonfree" or something to that extent with out considering to list other steps if said responce does not work. 

4) I have installed this one 4 different 64bit platforms so I don' t know what you would consider "thorough" as I am not going to set up a lab to test other senarios

5) I probably will not continue to post too much more on this thread as I read more than I post. Use at your own risk.

---

