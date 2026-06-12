---
title: "Installing needed Wine packages with Bash script"
date: 2016-10-11
forum: Wine
---

### Post by jdo300 on 2016-10-11
Hello All,

I'm working on a bash script to automate the installation process of wine and wine apps to deploy on several Ubuntu 14.04 machines that I am configuring. So far, I am able to manually install wine using the following commands:

```
sudo dpkg --add-architecture i386
echo -e '\n' | sudo add-apt-repository ppa:wine/wine-builds
sudo apt-get update
sudo apt-get -y install --install-recommends winehq-devel
```

Then, I run the following to install one of the apps I'm using:

```
wine '/home/user/Desktop/femm42bin_win32.exe'
```

But then a dialog box pops up saying, 
> Wine could not find a Mono package which is needed for .NET applications to work correctly. Wine can automatically download  and install it for you.

Note: it is recommended to use your distribution's packages instead.
See [http://wiki.winehq.org/Mono](http://wiki.winehq.org/Mono) for details.
I also got a similar message saying that I needed to download Gecko as well. If I just follow the prompts and download the missing files, the application installs and runs fine. However, I would like to include these missing packages in my bash script so that after I manually install the applications on one machine, I can simply install the wine packages and dependencies, and then copy the .wine folder with my windows apps over to the new machine (also using the bash script).

So, I did some research on how to automate the installation of mono and gecko and came across a couple of other posts talking about this, such as

[http://askubuntu.com/questions/577311/mono-package-for-wine](http://askubuntu.com/questions/577311/mono-package-for-wine)

and

[https://askubuntu.com/questions/399536/wine-1-7-9-and-mono-package](https://askubuntu.com/questions/399536/wine-1-7-9-and-mono-package)

In these two posts, the people solved the problem by manually specifying the mono package and installing it along with wine, so I the modified my original procedure to the following:

```
sudo dpkg --add-architecture i386
echo -e '\n' | sudo add-apt-repository ppa:wine/wine-builds
echo -e '\n' | sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get -y install wine-mono4.5.6
sudo apt-get -y install wine-gecko2.40
sudo apt-get -y install --install-recommends winehq-devel
```

The packages all installed without problems, but when I go to install the app again, I still get the same dialog prompting me to download mono and gecko, as if it wasn't even aware that they were on the system. Thinking that the problem could be relate to the order of operations, I tried installing the mono and gecko packages first, followed by wine, but that made no difference either. Has anyone had this problem before?

Thanks,
Jason O

---

### Post by jdo300 on 2016-10-14
Hi Everyone,

I was ultimately able to solve my problem, though not the latest version of Wine (1.9) installed. I'm running Ubuntu 14.04 LTS currently and finally opted to just use the older version from the Ubuntu repository (1.6). I did run into another problem where the ttf-mscorefonts-installer poped up an EULA agreement that required user intervention to accept, but I found some code to auto-accept that as well and complete the installation completely automatically. For those interested, here's the bash script code I wrote: ```
#!/bin/bash

echo "Installing Wine..."

# Pre-install microsoft fonts package and pre-accept MS EULA licence agreement
echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | sudo debconf-set-selections
sudo apt-get -y install ttf-mscorefonts-installer

# Install Wine
sudo apt-get -y install --install-recommends wine
```

- Jason O

---

### Post by howefield on 2016-10-14
Moved to the "*Wine*" forum.

---

### Post by deadflowr on 2016-10-15
quick tip:
Drop the sudo's within the script and just run the script with sudo, like
```
sudo ./name-of-script.sh
```
then all the commands will run without needing sudo for each one, as the script will be run as root as a whole.

sudo has a timeout of 15 minutes or the length of the running command.
Since the script would be run as sudo, the 15 minute timeout won't affect it, if any of the commands go beyond the timeout limit.

You could run the script with sudo and have each entry have sudo added, but then that's just redundant.
If that makes sense.

---

