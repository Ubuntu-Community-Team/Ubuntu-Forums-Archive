---
title: "64-bit concerns"
date: 2008-06-04
forum: x86 64-bit Users
---

### Post by SeePU on 2008-06-04
I am interested in installing a 64-bit version of K/Ubuntu but I wanted to ask a few questions.  I built a new Intel-based Quad Core system and installed a 64-bit distro.  However, the boot-up into the desktop takes an awfully long time.  I can't figure out what's wrong.  I was given ideas of bad hard drive, cooling, RAM issues etc. etc. but I haven't concluded the problem yet.  

Is there anything that would result in the system being slow?

Also, if I try K/Ubuntu 64-bit, do I use the AMD64 image?  Also, I'm used to the KDE desktop.  But, will it matter whether I choose Ubuntu or Kubuntu?

Thanks in advance for all answers.

---

### Post by tamoneya on 2008-06-04
first of all kubuntu = kde, ubuntu = gnome
To solve the boot time issue try installing boot chart: [http://www.bootchart.org/](http://www.bootchart.org/)```
sudo apt-get install bootchart
```
Then post the results and we will see if we can speed it up.  
While it might be a bit more than you can handle at the moment you may find this thread interesting:[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by zarvox on 2008-06-04
Most likely, the initial loading of all the program's resources and libraries off disk is taking a while.  The fact that 64-bit libraries are usually larger than their 32-bit counterparts might be increasing that.  After the initial load from disk, these files will be cached in RAM, which is much faster.  You may notice this effect when you try to open an application that you just closed; it will likely open much faster the second time, since it already has a copy of all the necessary files in RAM.

So while native 64-bit libraries might make a *slight* difference in boot time, they will likely make up for it in performance, particularly for CPU-bound tasks.

I'm currently running 64-bit Kubuntu on my Core 2 Duo laptop, and have no complaints.  If you like KDE, go for the AMD64 Kubuntu install.

---

### Post by saru411 on 2008-06-05
Have you looked at your system log files? I'm sure your long boot issue is reported somewhere in there. Once you see the error you should look around the forums and also search Launchpad.

---

### Post by Sef on 2008-06-05
> So while native 64-bit libraries might make a *slight* difference in boot time, they will likely make up for it in performance, particularly for CPU-bound tasks.

With the update to the .18 kernel, my boot time is much faster.

---

### Post by Plasma_NZ on 2008-06-05
> **Sef said:**
> With the update to the .18 kernel, my boot time is much faster.

I can confirm this too...

---

### Post by saru411 on 2008-06-06
how do you update your kernel?

---

### Post by Sef on 2008-06-06
> how do you update your kernel?

I did it through System > Administration > Update.

---

### Post by saru411 on 2008-06-08
That's strange. I'm running HH and i can only upgrade to .17 not .18

---

### Post by RaleTheBlade on 2008-06-08
Did you install Ubuntu from Windows? I noticed when I did that, it was rather slow booting up. Ive since burned a copy to a CD and installed it that way, and it runs pretty quick now. Ive got the 64 bit desktop version.

Also, the initial bootup from a Windows setup will take awhile. I think its copying the files it needs before it can run. After that it should be alright.

Ive also got an Intel Core2 Quad Q6700 2.66 GHz and it runs fantastically. Definitely a better alternative to... *shiver* Vista

---

### Post by Sef on 2008-06-08
> That's strange. I'm running HH and i can only upgrade to .17 not .18

What happens when you type in this code:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by saru411 on 2008-06-09
> xxxx@XXXX:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for xxxx: 
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy Release.gpg
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/main Translation-en_US   
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/restricted Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/universe Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/multiverse Translation-en_US
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates Release.gpg       
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/main Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/restricted Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/universe Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/multiverse Translation-en_US
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security Release.gpg
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/main Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/restricted Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/universe Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/multiverse Translation-en_US
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-proposed Release.gpg      
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-proposed/restricted Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-proposed/main Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-proposed/multiverse Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-proposed/universe Translation-en_US
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-backports Release.gpg     
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-backports/restricted Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-backports/main Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-backports/multiverse Translation-en_US
Ign [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-backports/universe Translation-en_US
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy Release
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates Release           
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security Release          
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-proposed Release          
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-backports Release                        
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/main Packages                            
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/restricted Packages                      
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/main Sources                             
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/restricted Sources                       
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/universe Packages                        
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/universe Sources                         
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/multiverse Packages                      
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy/multiverse Sources                       
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/main Packages                    
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/restricted Packages              
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/main Sources                     
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/restricted Sources               
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/universe Packages                
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/universe Sources                 
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/multiverse Packages              
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-updates/multiverse Sources               
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/main Packages                   
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/restricted Packages             
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/main Sources                    
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/restricted Sources              
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/universe Packages
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/universe Sources
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/multiverse Packages
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-security/multiverse Sources
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-proposed/restricted Packages
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-proposed/main Packages
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-proposed/multiverse Packages
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-proposed/universe Packages
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-backports/restricted Packages
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-backports/main Packages
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-backports/multiverse Packages
Hit [http://mirror.imbrandon.com](http://mirror.imbrandon.com) hardy-backports/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Notice it says I'm up to date. My current version is 2.6.24-17-generic

---

### Post by saru411 on 2008-06-09
> **RaleTheBlade said:**
> Did you install Ubuntu from Windows? I noticed when I did that, it was rather slow booting up. Ive since burned a copy to a CD and installed it that way, and it runs pretty quick now. Ive got the 64 bit desktop version.

Also, the initial bootup from a Windows setup will take awhile. I think its copying the files it needs before it can run. After that it should be alright.

Ive also got an Intel Core2 Quad Q6700 2.66 GHz and it runs fantastically. Definitely a better alternative to... *shiver* Vista

I haven't run windows on this build (built 4/07). I've only run Ubuntu and other Linux flavors on it, but Hardy Hereon is the only distro currently installed. This thread is about a bug found on Asus motherboards with pre -18 kernels. I don't believe you understand the issue, but thanks for the effort.

---

