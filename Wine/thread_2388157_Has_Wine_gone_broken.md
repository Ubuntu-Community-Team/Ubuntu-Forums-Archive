---
title: "Has Wine gone broken?"
date: 2018-03-29
forum: Wine
---

### Post by armrek on 2018-03-29
Recently I ordered a new laptop, since I am using Ubuntu 16.04 LTS currently I have made some tests with 17.04 LTS and 18.04 daily builds. To see if I could shift to one of these.

I installed Wine in all sorts of ways on these platforms, it seems that the newest strain of Wine is broken, I have not been able to get Wine to show in the context menu for starting up exe files no matter what. 

Had to install mono from an msi file in the wine uninstaller to get one exe running, I could only run it from a terminal:

wine someprg.exe

Doubleclicking is not an option since Wine seems unregistered and the default is trying to unpack an exe.

On 16.04 LTS, the version I get from the official software app runs smoothly, with double click on exe files and all. 

What gives, is wine broken?

---

### Post by shag00 on 2018-03-31
I have wine-devel 3.4 running on Ubuntu 17.10 both installed via synaptic so there is no problem with Wine.

---

### Post by armrek on 2018-03-31
> **shag00 said:**
> I have wine-devel 3.4 running on Ubuntu 17.10 both installed via synaptic so there is no problem with Wine.

Thanks for your reply, 

I am still a newbie to Linux/Ubuntu can you explain stepwise how you installed it ? :-)

---

### Post by shag00 on 2018-03-31
Follow these detailed instructions [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)  uses the terminal but works fine.

---

### Post by moto1860 on 2018-03-31
> **shag00 said:**
> Follow these detailed instructions [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)  uses the terminal but works fine.
Had this at the end of instsallation:

```
Errors were encountered while processing: /tmp/apt-dpkg-install-7exLPL/153-libsane1_1.0.27-1~experimental2ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by armrek on 2018-03-31
> **shag00 said:**
> Follow these detailed instructions [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)  uses the terminal but works fine.

[SIZE=4]Thank you, tried that on Ubuntu 18.04 and got some errors[/SIZE]:

[SIZE=3]No problem getting the architecture and the Keys with the three first commands[/SIZE]

[SIZE=3][FONT=courier new]**On Add repository**([/FONT]sudo apt-add-repository [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)[/SIZE][FONT=courier new][SIZE=3]):[/SIZE]
-------------------------------------------------------

E: The repository 'https://dl.winehq.org/wine-builds/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


[SIZE=3]**On Update**([/SIZE][/FONT][SIZE=3]sudo apt-get update[/SIZE][FONT=courier new][SIZE=3]):[/SIZE]
-------------------------------------------------------

Ign:5 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease                
Err:6 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic Release            
  404  Not Found [IP: 151.101.36.69 443]
Reading package lists... Done
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

[SIZE=3]**On Install**([/SIZE][/FONT][SIZE=3]sudo apt-get install --install-recommends winehq-devel[/SIZE][FONT=courier new][SIZE=3]):[/SIZE]
-------------------------------------------------------
devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winehq-devel

[/FONT][SIZE=4]As you can see there are problems with wine on 18.04, it might be trivial but for a newbie maybe not, **so what gives**?[/SIZE]

---

### Post by oldos2er on 2018-03-31
17.04 is not LTS, it went end-of-life in January.

---

### Post by mc4man on 2018-03-31
> **armrek said:**
>  I have not been able to get Wine to show in the context menu for starting up exe files no matter what. 


Doubleclicking is not an option since Wine seems unregistered and the default is trying to unpack an exe.

On 16.04 LTS, the version I get from the official software app runs smoothly, with double click on exe files and all. 

What gives, is wine broken?

That's because the latest wine packages don't install a wine.desktop file. Without that you won't get a context menu option.
Seems rather dumb.
You can copy the previous wine.desktop in 16.04 (/usr/share/applications/wine.desktop) to an applications folder in 18.04 for ex. to
~/.local/share/applications

---

### Post by moto1860 on 2018-03-31
How can I fix this?

 [IMG]https://image.ibb.co/c5jD9n/Screenshot_from_2018_03_31_22_21_34.png[/IMG]

---

### Post by shag00 on 2018-03-31
18.04 is still in beta, repositories may be lagging a little.

Apropos the libsane error, see this: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1725928](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1725928)  

NB:You use this code:```
sudo apt-get -o Dpkg::Options::="--force-overwrite" install --reinstall libsane1:i386
``` 

or if it is in the repository download libsane1 1.0.27-1~experimental[COLOR=#ff0000]3[/COLOR]ubuntu1 which replaces the faulty libsane1 1.0.27-1~experimental[COLOR=#006400]2[/COLOR]ubuntu1,
I found installing libsane first worked then (in my case) wine-development.

---

### Post by moto1860 on 2018-03-31
[COLOR=#000000]*edit*[/COLOR]

---

### Post by shag00 on 2018-03-31
> **moto1860 said:**
> According to ubuntu software I've both Wine and Wine development version installed (can't find them under show applications tho) however clicking on them from there and then *Launch *nothing happens

Your 2nd last post indicated a specific problem with a dependent package required to run wine, to which I gave you an equally specific remedy. Your last post does not refer to my last reply in any way whatsoever so you are wasting everyone's time. How about start your own thread.

---

### Post by shag00 on 2018-04-01
No, it's not mine, it's just after all these years I finally found a question I could answer lol.

---

### Post by armrek on 2018-04-01
> **mc4man said:**
> That's because the latest wine packages don't install a wine.desktop file. Without that you won't get a context menu option.
Seems rather dumb.
You can copy the previous wine.desktop in 16.04 (/usr/share/applications/wine.desktop) to an applications folder in 18.04 for ex. to
~/.local/share/applications

I do not see that file. Even though the menu works on my 16.04 based system. .

---

### Post by armrek on 2018-04-21
I have tried everything, It runs on 16.04LTS, but on 1804 nothing happens when I click *Install Paint Shop Pro* in the splash screen of autorun.exe. 

So I'm sticking to 16.04 of this reason...

---

