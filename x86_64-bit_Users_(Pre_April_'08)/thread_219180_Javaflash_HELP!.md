---
title: "Java/flash HELP!"
date: 2006-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Deathcab on 2006-07-19
I am getting very frustrated. For the past hour and a half I have tried to get Java and Flash to work on my AMD64 computer with firefox. I installed automatix, I followed that 32 bit tutrial in that one persons sig, I have tried almost everything and I still cannot get them to install properly.  I really need help. Also Since I tried to install java there is a folder on my desktop "jre1.5.0_07" that has a lock in upper corner and I cannot delete it becuase "I am not the owner"???

Help.Please.

Thanks

---

### Post by Kilz on 2006-07-19
> **Deathcab said:**
> I am getting very frustrated. For the past hour and a half I have tried to get Java and Flash to work on my AMD64 computer with firefox. I installed automatix, I followed that 32 bit tutrial in that one persons sig, I have tried almost everything and I still cannot get them to install properly.  I really need help. Also Since I tried to install java there is a folder on my desktop "jre1.5.0_07" that has a lock in upper corner and I cannot delete it becuase "I am not the owner"???

Help.Please.

Thanks

To get rid of the jre1.5.0_07 folder type this in a terminal. Relpace <username> for your username
```
sudo chown -R <username:users ~/Desktop/jre1.5.0_07
```
Then you will be able to delete the folder.
I notice you have probably tried my howto, if you cant make it work, use the [auto setup script.]("http://tghc.org/files/Firefox32-flash-java.tar.gz") Save the file to your desktop. Right click on the file and select "Extract here" a ffinstall folder will extract. Open a terminal type in
```
cd ~/Desktop/ffinstall
```
then
```
sudo ./Firefox
```
Answer yes to a few questions
Click on the firefox icon on your deskop when its done. The script will even clean up after itself.

---

### Post by Deathcab on 2006-07-19
Okay I got the flash/java working but there is no sound when movies play? Sound plays with music on my HD but not in the browser. Wonder what the problem could be. Also I couldt delete that folder, It said directorys not found.

---

### Post by Kilz on 2006-07-19
> **Deathcab said:**
> Okay I got the flash/java working but there is no sound when movies play? Sound plays with music on my HD but not in the browser. Wonder what the problem could be. Also I couldt delete that folder, It said directorys not found.

It could be one of 3 things if they are flash movies.
1)alsa-oss needs to be installed
```
sudo apt-get install alsa-oss
```
You may have to reboot to get this one to work for some reason.
2)libraries need to be linked
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib32/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib32/libesd.so.0
```
3)files owned by root. Replace <username> with your username
```
chown -R <username>:users /home/<username>/.macromedia
sudo chown -R <username>:users /usr/local/firefox32
```

To delete the java folder on your desktop, here is an alternate way.
```
gksudo natulius
```
Will open up the file manager as root, then navigate up, then to home, then th the folder with your username, then Desktop. Then delete the java folder.

---

### Post by Deathcab on 2006-07-19
The first one said That it was up to date. Second one did something but Didnt help. Number 3 said no direcroty found. And number 4 said command not recconized or something.

---

### Post by Kilz on 2006-07-19
> **Deathcab said:**
> The first one said That it was up to date. Second one did something but Didnt help. Number 3 said no direcroty found. And number 4 said command not recconized or something.

my bad spelling
```
gksudo nautilus
```

If you have not rebooted since installing the script, it also installs 1) you may just need to reboot.
You may want to go over 3) because at least the firefox32 folder should exist. The script creates it. You do have to edit the command to replace <username> with the name you sign in with.

---

### Post by tjmoes on 2006-07-20
Ihave still not been able to install this new jre  have done the things that were suggested but it just will not install and cant copy file to the java folder
sudo says file or directory not there and im so cornfused

---

### Post by Kilz on 2006-07-20
> **tjmoes said:**
> Ihave still not been able to install this new jre  have done the things that were suggested but it just will not install and cant copy file to the java folder
sudo says file or directory not there and im so cornfused
Looking at all 6 of your past posts, I dont see any java questions. What and how exactly are you trying to setup?

---

### Post by tjmoes on 2006-07-21
im trying install the new jave but i guess im in the wrong forum cuz dont have a 64 bit

---

