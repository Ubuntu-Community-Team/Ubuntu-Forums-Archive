---
title: "Playonlinux"
date: 2012-11-27
forum: Wine
---

### Post by Beardedturtle on 2012-11-27
Updated to the latest playonlinux and get a error:
 PlayOnLinux cannot find 7z (from P7ZIP full)

Any advise??

Using Ubuntu 12.04

---

### Post by donaldhall on 2012-11-27
I am getting this too along with everyone running 12.04/12.10 I think. It hasn't effected anything of mine so I am sorry I couldn't help you more.

---

### Post by Mr. Hibba on 2012-11-28
It sounds like maybe PlayOnLinux didn't install 7z as a dependency.  You may want to try searching for 7z in the Ubuntu Software Center, or run 
```
sudo apt-get install p7zip
```  in a terminal.  


Hope this helps, 

Mr. Hibba

---

### Post by Beardedturtle on 2012-11-28
> **Mr. Hibba said:**
> It sounds like maybe PlayOnLinux didn't install 7z as a dependency.  You may want to try searching for 7z in the Ubuntu Software Center, or run 
```
sudo apt-get install p7zip
```  in a terminal.  


Hope this helps, 

Mr. Hibba
  Got it installed and the error keeps coming up,,,

---

### Post by Mr. Hibba on 2012-11-29
I may have made a mistake.  According to [https://answers.launchpad.net/ubuntu/+source/playonlinux/+question/203379](https://answers.launchpad.net/ubuntu/+source/playonlinux/+question/203379), it looks like the package might actually be p7zip-full.  

```
sudo apt-get install p7zip-full
``` might do the trick.  

Mr. Hibba

---

### Post by Beardedturtle on 2012-11-30
> **Mr. Hibba said:**
> I may have made a mistake.  According to [https://answers.launchpad.net/ubuntu/+source/playonlinux/+question/203379](https://answers.launchpad.net/ubuntu/+source/playonlinux/+question/203379), it looks like the package might actually be p7zip-full.  

```
sudo apt-get install p7zip-full
``` might do the trick.  

Mr. Hibba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
p7zip-full is already the newest version.
p7zip-full set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

=\ Might just need to remove the playonlinux completely. And not look back.

---

### Post by Beardedturtle on 2012-11-30
Got it to work but when I try to install a gog.com game it will say login failed even though I am typing in my account info correctly.

---

