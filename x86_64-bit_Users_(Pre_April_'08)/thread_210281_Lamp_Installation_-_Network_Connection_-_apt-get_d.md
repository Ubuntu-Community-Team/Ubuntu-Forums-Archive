---
title: "Lamp Installation - Network Connection - apt-get does not seem to work"
date: 2006-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by sincereheart on 2006-07-06
I have 64 bit (EM64T chip) Dell Machines. Downloaded the ISO file and burnt on the CD.

1.    After installing the Ubuntu Server from the iso file (after download) I tried installing LAMP from  the CD (I burnt the CD myself after the download). However it seems to be re-installing UBUNTU and asking for partitioning etc.  Very weird to do so..

2.      Sudo apt-get update - does not seem to work.

3.      Ifconfig does not show me an IP address.  Seems like I am not connected to the internet.

4.       I searched for httpd. I do not have httpd daemon installed. So I wonder as to how would the system make a connection with the repositories to begin with. Should it not be part of default install.

5.        So is GNOME a default install or do I have to get it. What do I have to do to get GNOME. I do not think that I have GNOME currently installed.

Thanks.

---

### Post by Kilz on 2006-07-06
[QUOTE=sincereheart]I have 64 bit (EM64T chip) Dell Machines. Downloaded the ISO file and burnt on the CD.

1.    After installing the Ubuntu Server from the iso file (after download) I tried installing LAMP from  the CD (I burnt the CD myself after the download). However it seems to be re-installing UBUNTU and asking for partitioning etc.  Very weird to do so..

2.      Sudo apt-get update - does not seem to work.

3.      Ifconfig does not show me an IP address.  Seems like I am not connected to the internet.

4.       I searched for httpd. I do not have httpd daemon installed. So I wonder as to how would the system make a connection with the repositories to begin with. Should it not be part of default install.

5.        So is GNOME a default install or do I have to get it. What do I have to do to get GNOME. I do not think that I have GNOME currently installed.

Thanks.[/QUOTE]
Ok, 
1. When you chose the "install lamp" from the server install disk it installs the os with lamp. So whats happening is normal. 
2. If you are not connected to the internet you cant update. Are you connected?
3. You may not be, did you test the hardware with a live cd first?
4. The install, not install lamp, installs a OS for use by server daemons, like ftp or a mail server. You may want the "Install Lamp" option instead.
5. The server install disk dose not install a desktop. A lot of people who run a server dont want a desktop because it eats up a lot of resources for the little time they will use it, so they do the work on it with commands. If you want a gnome desktop, use the command 
```
sudo apt-get install ubuntu-desktop
```

---

### Post by sincereheart on 2006-07-06
[QUOTE=Kilz]Ok, 
>>1. When you chose the "install lamp" from the server install disk it installs the os with lamp. So whats happening is normal. << 
Thanks for clarification. By the way no where in your documentation it says that. I get the impression that it is going to format the previous installation of Ubuntu. So I may loose all my data.  I already installed the Ubuntu OS (Wiped off previous installation of Win XP completely). Now all I want to do is to install the LAMP...What are my options at this stage. 

>>2. If you are not connected to the internet you cant update. Are you connected?<< Connected in the sense - The wire to router is connected properly. I do see the light coming from the back of the computer. (Double checked by connecting the same wire to another Laptop. Connection works fine).  So how do I enable / disable internet connection.

>>3. You may not be, did you test the hardware with a live cd first?<< No. I downloaded the ISO image. It tested the CD but not the hardware. So you mean testing for the Network Card.... Before installing Ubuntu, I had Win XP installed on this computer - I could connect to internet and do ping etc without a problem. It is now after installing the Ubuntu that I am unable to.
So are you hinting at getting the drivers for the NIC card....Any tips in this regard will be highly appreciated. 

>>4. The install, not install lamp, installs a OS for use by server daemons, like ftp or a mail server. You may want the "Install Lamp" option instead.<<
I need httpd for the Apache2. So in order to get the httpd, I will follow your advice of installing LAMP.

>>5. The server install disk dose not install a desktop. A lot of people who run a server dont want a desktop because it eats up a lot of resources for the little time they will use it, so they do the work on it with commands. If you want a gnome desktop, use the command 
```
sudo apt-get install ubuntu-desktop
```<< 
Thanks. Yes I agree with you. it is going to be a trial server. 
[/QUOTE]

Please read my comments next to the quotes. Thanks.

---

### Post by Kilz on 2006-07-06
1. Im just a user, the documentation isnt mine. Ubuntu is a community thing, we help each other. I try to help answer questions where I can because other people helped me at one time. Your options are 3.
A. If you havent put to much time in, just pop the cd back in and chose "Install Lamp" then install the desktop if you want it.
B. If you have done some setup and want to keep it. [You could follow this howto]("https://help.ubuntu.com/community/ApacheMySQLPHP") to setup the amp part of lamp. 
C. You could download the live cd, install the desktop version, [then follow the howto.]("https://help.ubuntu.com/community/ApacheMySQLPHP") This wayyou could make sure your hardware is all suported first with the livcd os.
2. You enable the internet by getting your nic card working. Something that isnt impossible from the command line, but slightly harder.
3. Setting up drivers for NIC cards isnt my strong point. But if you know what card you have I may be able to help you find the documentation that will help.
4. Good , you have the choice above.
5. A desktop isnt that bad, you could use gnome, kde ,or the light Xfce the only diffrence would be ubuntu-desktop for gnome, kubuntu-desktop for kde, xubuntu-desktop for xfce. But imho gnome or xfce would be better than kde.

---

### Post by Lil_Eagle on 2006-07-06
Kilz, excellent advice.  I of course would choose to run apt-get install kubuntu-desktop, if I didn't just pick kde (which will install ALL of KDE :cool: ).

I couldn't figure out how to change the color of the task bar in gnome so I gave up.  I am damn picky ;).   I think I will try a few more desktops just to see, but I have a feeling that I will keep coming back to KDE.  Aside from the fact that it takes quite a few resources, what do you have against it?

It must be noted that there is another PC in the house that has edubuntu installed, so I am not totally ignorant to gnome.

To the task at hand, if the PC is just going to be a server, then it's probably better not to install a desktop, or at least not the packages that are the (name)-desktop because they all will start upon boot.  Of course, you could modify the init to change it from starting, but if you're not familiar with the way linux boots, it could prove difficult to stop GDM or KDM from starting.  I prefer for a server to type startx when I want X, otherwise it's just a command prompt.

---

### Post by Kilz on 2006-07-06
[QUOTE=Lil_Eagle]Kilz, excellent advice.  I of course would choose to run apt-get install kubuntu-desktop, if I didn't just pick kde (which will install ALL of KDE :cool: ).

I couldn't figure out how to change the color of the task bar in gnome so I gave up.  I am damn picky ;).   I think I will try a few more desktops just to see, but I have a feeling that I will keep coming back to KDE.  Aside from the fact that it takes quite a few resources, what do you have against it?

It must be noted that there is another PC in the house that has edubuntu installed, so I am not totally ignorant to gnome.

To the task at hand, if the PC is just going to be a server, then it's probably better not to install a desktop, or at least not the packages that are the (name)-desktop because they all will start upon boot.  Of course, you could modify the init to change it from starting, but if you're not familiar with the way linux boots, it could prove difficult to stop GDM or KDM from starting.  I prefer for a server to type startx when I want X, otherwise it's just a command prompt.[/QUOTE]

Gnome is just my fav, I really don't have anything against kde. In fact I started out on Linux using SuSE with kde. I tried gnome just to see what it was like, and never went back. I like the less is more feel of gnome. It just seems to work and do what I want it to do. Some people say that kde is more like windows and may be a better fit for windows users, maybe that backfired on me. I used windows so long, I might have been looking for anything that wasn't windows like.
But anyway to me kde seems real graphic intense. Not something you want on a server. I don't think it matters that much on a desktop.

---

### Post by sincereheart on 2006-07-09
I was able to install the LAMP (re-install of Ubuntu). 
ifConfig works now. I can also do a hostname and other similar things.

However if I do a ping to any server or even to local host etc; it goes into an un-ending loop of pinging.

My apt-get still does not seem to work. 
It says "unable to connect to ...(I guess the ip address for the repository..) ......."

Some times it seems like checking for dependencies and seem to say "done" but then in the end it says "unable to find package ...". 

On this installation of Ubuntu Server, I tried installing GNOME and got similar errors. .... unable to connect ......

(I made sure that hostname is working... wire is connected.. etc etc). 
 
Any help will be greatly appreciated.

Thanks.


Then I tried Kubuntu. Things seem to be going alright. But then it started asking for more partitioning. I already have 3 partitions including one for SWAP.

I was under the impression that GNOME or Kubuntu (i.e. KDE) will be installed on top of my previous installation of Drape Serve install.

---

### Post by sincereheart on 2006-07-09
I was able to install the LAMP (re-install of Ubuntu). 
ifConfig works now. I can also do a hostname and other similar things.

However if I do a ping to any server or even to local host etc; it goes into an un-ending loop of pinging.

My apt-get still does not seem to work. 
It says "unable to connect to ...(I guess the ip address for the repository..) ......."

Some times it seems like checking for dependencies and seem to say "done" but then in the end it says "unable to find package ...". 

On this installation of Ubuntu Server, I tried installing GNOME and got similar errors. .... unable to connect ......

(I made sure that hostname is working... wire is connected.. etc etc). 
 
Any help will be greatly appreciated.

Thanks.


Then I tried Kubuntu. Things seem to be going alright. But then it started asking for more partitioning. I already have 3 partitions including one for SWAP.

I was under the impression that GNOME or Kubuntu (i.e. KDE) will be installed on top of my previous installation of Drape Serve install.

---

### Post by Kilz on 2006-07-09
> **sincereheart said:**
> I was able to install the LAMP (re-install of Ubuntu). 
ifConfig works now. I can also do a hostname and other similar things.

However if I do a ping to any server or even to local host etc; it goes into an un-ending loop of pinging.

My apt-get still does not seem to work. 
It says "unable to connect to ...(I guess the ip address for the repository..) ......."

Some times it seems like checking for dependencies and seem to say "done" but then in the end it says "unable to find package ...". 

On this installation of Ubuntu Server, I tried installing GNOME and got similar errors. .... unable to connect ......

(I made sure that hostname is working... wire is connected.. etc etc). 
 
Any help will be greatly appreciated.

Thanks.


Then I tried Kubuntu. Things seem to be going alright. But then it started asking for more partitioning. I already have 3 partitions including one for SWAP.

I was under the impression that GNOME or Kubuntu (i.e. KDE) will be installed on top of my previous installation of Drape Serve install.
Kubuntu is a diffrent setup than Ubuntu. Each will overwrite existing instllations of themselves. You may want to delete the already existing partitions. 
The only diffrence is that I believe that Kubuntu setus up the /home directory on its own partition. Other than that they are the same except for the desktop. I do think that Kubuntu uses the most resources of the 3 versions and may not be the ideal candidate for a server.
You may still have problems accessing the internet, what NIC card are you using?

---

### Post by sincereheart on 2006-07-09
Greatly appreciate your response. It was very prompt of you.

I can do nslookup.
For example I just did:
nslookup yahoo.com and I got the response like IP address etc..
I got the following IP addresses:
66.94.234.13
and
216.109.112.135


When doing an apt-get installl packageName etc...
I guess it is looking in E: drive...
When I do apt-get install ... it says:

--------------------------------

Reading Package lists ... Done
Building dependency tree ... Done
E: Couldn't find package xyz (i.e. PackageName)

--------------------------------
Why does it look at E drive. (By the way I have 3 partitions).

If you still ask for NIC card .. then I will open up the box and let you know.

By the way:  tracert or traceroute does not seem to be a valid command on Ubuntu... I could not find any MAN entry for this...!!

Install of GNOME or Kubuntu:
I want to keep the ubuntu server. I thought by installing either one, I will be able to do certain tasks more conveniently on the same Ubuntu Server. I do not want a new partition for this purpose.

So for browsing / local testing of LAMP can I install Firefox? That way I do not have to shift machines.

Thanks once again. This forum is certainly an excellent resource.

---

### Post by Kilz on 2006-07-09
> **sincereheart said:**
> Greatly appreciate your response. It was very prompt of you.

I can do nslookup.
For example I just did:
nslookup yahoo.com and I got the response like IP address etc..
I got the following IP addresses:
66.94.234.13
and
216.109.112.135


When doing an apt-get installl packageName etc...
I guess it is looking in E: drive...
When I do apt-get install ... it says:

--------------------------------

Reading Package lists ... Done
Building dependency tree ... Done
E: Couldn't find package xyz (i.e. PackageName)

--------------------------------
Why does it look at E drive. (By the way I have 3 partitions).

If you still ask for NIC card .. then I will open up the box and let you know.

By the way:  tracert or traceroute does not seem to be a valid command on Ubuntu... I could not find any MAN entry for this...!!

Install of GNOME or Kubuntu:
I want to keep the ubuntu server. I thought by installing either one, I will be able to do certain tasks more conveniently on the same Ubuntu Server. I do not want a new partition for this purpose.

So for browsing / local testing of LAMP can I install Firefox? That way I do not have to shift machines.

Thanks once again. This forum is certainly an excellent resource.
If you have gnome you should be ok, you don't need any more. In fact most people will assume you are using gnome unless you tell them you are using Kubuntu. This is because most people on the forums use Ubuntu.
I thought you had Internet trouble, sorry my mistake, you obviously have access so nope don't need the nic. 
You need to add repositories for apt. Its looking at E: because thats the only source of packages it has in the list. [Here is a good howto]("https://help.ubuntu.com/community/Repositories/CommandLine") to help get that done. Then apt should work fine.
Yes add firefox if it makes life easier.

---

### Post by RAOF on 2006-07-09
Um... That "E: could not *foo*" does not refer to a drive letter (linux doesn't **use** drive letters at all).  The "E: " is a shortened version of "Error: could not *foo*".

---

### Post by sincereheart on 2006-07-10
I backed up and then modified the /etc/apt/sources.list file. Enabled the entries for Universe. Did not un-comment any thing from Multivers. So only going to use Univers (apart from main and restricted).

Things seemed better. Tried doing an apt-get update. Was Able to get "lgn" probably login for some pacages. However majority of these failed. Lot of failures came from manin and restricted...

Also tried removing the word "us" from the links from sources.list..
Still no luck......

---

### Post by sincereheart on 2006-07-10
What log file do I look at for 'apt-get' errors...
I was unable to do:
sudo apt-get install firefox 

It seemed to work partially... as if going through the dependencies and installing them.. but then it also errored out....

---

### Post by Kilz on 2006-07-10
> **sincereheart said:**
> What log file do I look at for 'apt-get' errors...
I was unable to do:
sudo apt-get install firefox 

It seemed to work partially... as if going through the dependencies and installing them.. but then it also errored out....
I was looking for a solution for the apt-get problems you are having. I must admit I have learned a lot I never knew about apt before. One of the advantages of trying to help people I guess.

One post with problems close to yours had a solution of opening the apt.conf
```
gksudo gedit /etc/apt/apt.conf
```
and changing the proxy acuire to true, or just deleting the line so it reverts to the true default.

There is also a good post by ubuntu_demon on [recommended repositories.]("http://www.ubuntuforums.org/showthread.php?t=185758")

Finaly I see you have found the [repository section]("http://www.ubuntuforums.org/forumdisplay.php?f=41"). I hope someone there can help you solve this problem. If they do please let me know what it was.

---

