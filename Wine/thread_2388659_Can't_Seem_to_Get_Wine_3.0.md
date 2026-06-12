---
title: "Can't Seem to Get Wine 3.0"
date: 2018-04-05
forum: Wine
---

### Post by open4epl on 2018-04-05
I done what the website said about getting Wine 3.0 but I still got Wine 1.6.2. How can I get Wine 3.0 w/out running into Ver 1.6.2?

---

### Post by monkeybrain20122 on 2018-04-05
Which website? What did you do? More info please. Also I think playonlinux is a better way to run wine than just wine, from POL you can install any version of wine no matter what the system's version is.

---

### Post by open4epl on 2018-04-05
I did what this website said to do> [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

---

### Post by monkeybrain20122 on 2018-04-05
It works here in 16.0.4, the package is called "wine-stable" rather than "wine"

---

### Post by oldos2er on 2018-04-05
> **open4epl said:**
> I did what this website said to do> [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

Please provide some basic information such as Ubuntu version, what if any commands you tried, and copy and paste any error messages into a post here (or provide a screenshot if you used a GUI program). No one here is psychic, least of all me, so the more you can tell us, the quicker you'll get an answer to your question.

---

### Post by open4epl on 2018-04-05
I didn't get any error messages. I've done the commands that this website> [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu) said. I've put a screenshot of the Wine-Stable & Ubuntu version.

---

### Post by monkeybrain20122 on 2018-04-05
Install synaptic and see which versions of wine are displayed and installed. Like I said it works here.
```

sudo apt install synaptic
```

---

### Post by open4epl on 2018-04-05
Here's a screenshot of what version is installed.

---

### Post by monkeybrain20122 on 2018-04-05
Go ahead to install synaptic (type y) then start it, search for wine and see what versions are available and which one you installed. I have the feeling that for some reasons you haven't really added wine's repository since even if you installed wine instead of wine-stable you still should have 1.8 instead of 1.6

---

### Post by oldos2er on 2018-04-06
Please copy and paste terminal text into a post here instead of a screenshot.

Nothing there tells me which Ubuntu version you're running.

---

### Post by open4epl on 2018-04-06
I tried doing the same thing on the terminal but it just tells me "[COLOR=#000000][FONT=&amp]synaptic is already the newest version" so I just do another screenshot of "About This Computer". [/FONT][/COLOR]

---

### Post by deadflowr on 2018-04-06
> **monkeybrain20122 said:**
> Go ahead to install synaptic (type y) then start it, search for wine and see what versions are available and which one you installed. I have the feeling that for some reasons you haven't really added wine's repository since even if you installed wine instead of wine-stable you still should have 1.8 instead of 1.6

Then I would suggest the OP post the results of 
```
sudo apt update
```
which will confirm whether or not the wine repositories have been properly added or not.

We will need to see the full output, so a screenshot might be grab it all.
In which case copy and then paste the output in a post.

---

### Post by open4epl on 2018-04-06
```
eddie@eddie-HP-Notebook:~$ sudo apt install synaptic
[sudo] password for eddie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version (0.83).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
eddie@eddie-HP-Notebook:~$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Ign:3 http://build.openvpn.net/debian/openvpn/<stable> <xenial> InRelease      
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Err:5 http://build.openvpn.net/debian/openvpn/<stable> <xenial> Release        
  404  Not Found [IP: 52.53.189.67 80]
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Ign:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:8 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) xenial InRelease           
Hit:9 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Reading package lists... Done                     
E: The repository 'http://build.openvpn.net/debian/openvpn/<stable> <xenial> Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by deadflowr on 2018-04-06
You need to fix the openvpn repository source list entry.
Basically you need to remove the < > brackets.

I'm guessing you followed the guide here:
[https://community.openvpn.net/openvpn/wiki/OpenvpnSoftwareRepos]("https://community.openvpn.net/openvpn/wiki/OpenvpnSoftwareRepos")

Tha would be simple enough to fix.
In a terminal run
```
sudo nano /etc/apt/sources.list.d/openvpn-aptrepo.list
```
and change the entry from
```
deb http://build.openvpn.net/debian/openvpn/<stable> <xenial> main
```
to
```
deb http://build.openvpn.net/debian/openvpn/stable xenial main
```
then press ctrl + X to save and exit
(ctrl + X then press Y to accept the changes and then press Enter to exit)
then re-run the update command again.

---

### Post by open4epl on 2018-04-06
```
eddie@eddie-HP-Notebook:~$ sudo apt install synaptic
[sudo] password for eddie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version (0.83).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file 'openvpn-aptrepo.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'openvpn-aptrepo.listmbb' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
eddie@eddie-HP-Notebook:~$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Ign:4 http://build.openvpn.net/debian/openvpn/<stable> <xenial> InRelease      
Err:5 http://build.openvpn.net/debian/openvpn/<stable> <xenial> Release        
  404  Not Found [IP: 52.53.189.67 80]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Hit:7 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) xenial InRelease               
Ign:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:9 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Reading package lists... Done                     
N: Ignoring file 'openvpn-aptrepo.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'openvpn-aptrepo.listmbb' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: The repository 'http://build.openvpn.net/debian/openvpn/<stable> <xenial> Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
eddie@eddie-HP-Notebook:~$ sudo nano /etc/apt/sources.list.d/openvpn-aptrepo.list
eddie@eddie-HP-Notebook:~$ sudo apt update
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Ign:5 [http://build.openvpn.net/debian/openvpn/stable](http://build.openvpn.net/debian/openvpn/stable) xenial InRelease          
Get:6 [http://build.openvpn.net/debian/openvpn/stable](http://build.openvpn.net/debian/openvpn/stable) xenial Release [2,653 B]  
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Get:9 [http://build.openvpn.net/debian/openvpn/stable](http://build.openvpn.net/debian/openvpn/stable) xenial Release.gpg [512 B]
Hit:10 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) xenial InRelease               
Get:12 [http://build.openvpn.net/debian/openvpn/stable](http://build.openvpn.net/debian/openvpn/stable) xenial/main amd64 Packages [1,243 B]
Get:13 [http://build.openvpn.net/debian/openvpn/stable](http://build.openvpn.net/debian/openvpn/stable) xenial/main i386 Packages [1,237 B]
Fetched 312 kB in 1s (161 kB/s)                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
N: Ignoring file 'openvpn-aptrepo.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'openvpn-aptrepo.listmbb' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```

---

### Post by deadflowr on 2018-04-06
So all repos are up and correct.
(at some point you may want to remove those two files it's ignoring, but that's user preference as it has no bearing on things functioning properly. It's more of an annoyance than anything else, really)

I'd follow monkeybrain20122's suggestion to open synaptic and do a search for wine.

---

### Post by open4epl on 2018-04-06
I did a search for wine & installed a version I'm wanting. It installed fine but it's not showing in the Application Launcher.

---

### Post by monkeybrain20122 on 2018-04-06
> **open4epl said:**
> I did a search for wine & installed a version I'm wanting. It installed fine but it's not showing in the Application Launcher.

So where does wine 1.6 come from if wine3 is installed fine? If you install wine 1.6 that would remove wine 3.

To see all wine packages you have installed with apt, post the outputs of
```
apt list --installed | grep wine
```


e.g here is mine
```
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

wine-stable/xenial,now 3.0.0~xenial amd64 [installed,automatic]
wine-stable-amd64/xenial,now 3.0.0~xenial amd64 [installed,automatic]
wine-stable-i386/xenial,now 3.0.0~xenial i386 [installed,automatic]
winehq-stable/xenial,now 3.0.0~xenial amd64 [installed]
winetricks/xenial,xenial,now 0.0+20141009+svn1208-2ubuntu1 all [installed]


```

Note that the package name is not wine, but wine-stable or winehq-stable

---

