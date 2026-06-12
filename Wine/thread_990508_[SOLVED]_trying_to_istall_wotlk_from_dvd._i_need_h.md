---
title: "[SOLVED] trying to istall wotlk from dvd. i need help completly lost!"
date: 2008-11-22
forum: Wine
---

### Post by habelman on 2008-11-22
Alright. iv looked through all the forums i can find all the posts i can read. I have not found a suitable fix to my problem. Im trying to install Wotlk from my dvd my wine is up to date 1.1.9 but wont run the installer.exe
I found the code to do the unhide for the dvd which worked. But even then i cant get the installer.exe to do anything nor can i copy the files to my hard drive. Anyone know of a solution?

---

### Post by habelman on 2008-11-23
alright i just tried doing this

sudo umount /media/cdrom"
4. ```
sudo mkdir ~/Wrath
```
5. ```
sudo mkdir /mnt/temp
```
6. ```
sudo mount /dev/cdrom /mnt/temp -o unhide
```
7. ```
sudo cp -R /mnt/temp/* ~/Wrath
```/
8. ```
sudo chmod -R 777 ~/Wrath
```
9. ```
sudo umount /mnt/temp
```
10.```
sudo rmdir /mnt/temp
```

which is supposed to copy and create Wotlk folder into your home folder. Well i belived it work i have 10 files directx, autorun.inf, disk.ico , installer.exe installer tome.mpg installer tome2.mpg installer tome.mpg3 installer tome.mpg4 installer tome.mpg5 and movies.mpg ... but i dont know if thats all the files because now i cant access the cd? and when i try open installer.exe with wine nothing happens at all. when i double click nothing happens at all. and i cant open the directx folder. when i try to access the directx folder it says you do not have the required permission to acess this folder. so what am i supposed to do now?

---

