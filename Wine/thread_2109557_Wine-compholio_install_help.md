---
title: "Wine-compholio install help"
date: 2013-01-27
forum: Wine
---

### Post by luckystrikes23 on 2013-01-27
Sorry if I'm rehashing something, but I couldn't find this anywhere else.
I'm trying to install wine using the directions located here [http://www.compholio.com/wine-compholio/#patches](http://www.compholio.com/wine-compholio/#patches)

I'm running into problems here:


[LIST]
[*]Apply each of the individual patches:
[/LIST]
[INDENT]patch -p1 < ../000X-YYYYYYY.patch

[/INDENT]Here is what I've done in my terminal:[INDENT]luckystrikes23@ubuntu:~$ cd wine-compholio_1.5.20_i386
luckystrikes23@ubuntu:~/wine-compholio_1.5.20_i386$ patch -pl < ../0001-server-Create-directories-with-the-specified-securit.patch
bash: ../0001-server-Create-directories-with-the-specified-securit.patch: No such file or directory
luckystrikes23@ubuntu:~/wine-compholio_1.5.20_i386$ 
[/INDENT]Can anyone direct me to where I've gone wrong?

Using ubuntu 12.10, 64-bit

I've attached a screenshot [ATTACH]230731[/ATTACH] that shows the directory and the terminal window.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

You can install WINE through other means. If you are having trouble, open the terminal and try this;

sudo apt-get install wine

Or within the Software Center search up "wine" and install one of the versions they have, which is;

wine
wine.1.2
wine.1.3

---

### Post by luckystrikes23 on 2013-01-28
I should have mentioned, I've tried both of those, without any luck.

Terminal gets this:
[INDENT][I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/I]

[/INDENT]Software Center gets this with all versions:
[INDENT][I]Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.[/I]
[/INDENT]

---

### Post by Lightning Dragon on 2013-01-30
Hello,

Could you go into the home directory and unhide the hidden folders (CTRL+H) and see if there is a folder called ".wine"? There might be an older that is clashing with your attempts to install a new one. 

If not, please try to install an older version of wine. 1.5 is beta, try 1.4 or 1.3. Try this site and see if it fixes the problem for you;

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by Tweak42 on 2013-01-30
I think your syntax is wrong.

The command on the site is "patch -p1" <-- as in number one
Your command is "patch -pl" <-- as in the lowercase letter L

My question is why are you compiling it yourself?  You can add the PPA to your repositories and install it with ```
sudo apt-get install wine-compholio
```

Note: I don't think it's compatable with the normal wine packages so it may prompt you to uninstall default wine. 


> **luckystrikes23 said:**
> Sorry if I'm rehashing something, but I couldn't find this anywhere else.
I'm trying to install wine using the directions located here [http://www.compholio.com/wine-compholio/#patches](http://www.compholio.com/wine-compholio/#patches)

I'm running into problems here:


[LIST]
[*]Apply each of the individual patches:
[/LIST]
[INDENT]patch -p1 < ../000X-YYYYYYY.patch

[/INDENT]Here is what I've done in my terminal:[INDENT]luckystrikes23@ubuntu:~$ cd wine-compholio_1.5.20_i386
luckystrikes23@ubuntu:~/wine-compholio_1.5.20_i386$ patch -pl < ../0001-server-Create-directories-with-the-specified-securit.patch
bash: ../0001-server-Create-directories-with-the-specified-securit.patch: No such file or directory
luckystrikes23@ubuntu:~/wine-compholio_1.5.20_i386$ 
[/INDENT]Can anyone direct me to where I've gone wrong?

Using ubuntu 12.10, 64-bit

I've attached a screenshot [ATTACH]230731[/ATTACH] that shows the directory and the terminal window.

---

