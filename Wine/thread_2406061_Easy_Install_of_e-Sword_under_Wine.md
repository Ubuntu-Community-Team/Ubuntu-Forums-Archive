---
title: "Easy Install of e-Sword under Wine"
date: 2018-11-15
forum: Wine
---

### Post by MSGone on 2018-11-15
```
# I found this on the net and have no idea who did the script. It works!
# Using bash script in your terminal. Don't type in the lines with # at the start.
# It works great in Ubuntu 18.04. I just did it and it works great. 7-16-2018
# How to install e-Sword bible software in Ubuntu 18.04.1 LTS 64-bit using a bash script
# prerequisites: wine 2.0 or newer, winetricks wsh56 mfc42 vcrun6
# Your first command with sudo at the start should ask for your password.
# copy-paste each line below one by one into the Linux Terminal and hit return:
# Last updated on October 23, 2017
sudo apt-get update
sudo apt-get install wget
wget -nc --no-check-certificate [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key)
sudo apt-key add Release.key
sudo apt-add-repository [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)
sudo apt-get update
sudo apt-get install unp build-essential checkinstall
sudo apt-get install wine-staging winetricks
winetricks wsh56 mfc42 vcrun6 msls31 msxml3 * vbrun6 wsh57
cd /tmp
rm -rf download*
rm -rf setup*
# URL="http://www.e-sword.net/"
# wget --no-check-certificate `echo $URL`downloads.html
# FILENAME=`grep setup downloads.html |cut -d"\"" -f2|head -n 1`
# wget --no-check-certificate `echo $URL``echo $FILENAME`
wget --no-check-certificate [http://www.e-sword.net/files/setup1110.exe](http://www.e-sword.net/files/setup1110.exe)
wine setup*
cd
cd ".wine/drive_c/Program Files (x86)/e-Sword"
wine e-Sword.exe
# e-Sword works great
```

---

