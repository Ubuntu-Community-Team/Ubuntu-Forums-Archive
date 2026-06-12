---
title: "[SOLVED] Cannot install epiphany in Hardy 64"
date: 2008-05-25
forum: x86 64-bit Users
---

### Post by tooferson5 on 2008-05-25
I cannot login into one of my private torrent trackers(not going to say which one) with FF 3.  I have kde-desktop installed to so I've also tried Konqueror and that does not work either so I want to install epiphany but I get this message in terminal.  Any ideas? Also, I do have cookies enabled before anyone asks.  This is the only site that give me a problem.

```
usr@usr-laptop:~$ sudo apt-get update


Hit http://archive.canonical.com hardy Release.gpg

Ign http://archive.canonical.com hardy/partner Translation-en_US               

Ign http://ppa.launchpad.net hardy Release.gpg                                 

Ign http://ppa.launchpad.net hardy/main Translation-en_US                      

Hit http://us.archive.ubuntu.com hardy Release.gpg                             

Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  

Hit http://archive.canonical.com hardy Release                                 

Ign http://ppa.launchpad.net hardy Release.gpg                                 

Ign http://ppa.launchpad.net hardy/main Translation-en_US            

Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                

Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            

Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              

Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US    

Hit http://us.archive.ubuntu.com hardy-updates Release.gpg             

Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US

Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US  

Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US

Hit http://packages.medibuntu.org hardy Release.gpg                    

Ign http://packages.medibuntu.org hardy/free Translation-en_US         

Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US

Hit http://us.archive.ubuntu.com hardy-security Release.gpg            

Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US

Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US 

Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             

Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     

Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US   

Hit http://packages.medibuntu.org hardy Release                                

Hit http://us.archive.ubuntu.com hardy-proposed Release.gpg                    

Ign http://us.archive.ubuntu.com hardy-proposed/restricted Translation-en_US   

Ign http://us.archive.ubuntu.com hardy-proposed/main Translation-en_US         

Ign http://us.archive.ubuntu.com hardy-proposed/multiverse Translation-en_US   

Ign http://us.archive.ubuntu.com hardy-proposed/universe Translation-en_US     

Hit http://us.archive.ubuntu.com hardy Release                             

Hit http://us.archive.ubuntu.com hardy-updates Release                         

Hit http://us.archive.ubuntu.com hardy-security Release                        

Hit http://archive.canonical.com hardy/partner Packages                        

Hit http://packages.medibuntu.org hardy/free Packages                          

Hit http://us.archive.ubuntu.com hardy-proposed Release                        

Hit http://archive.canonical.com hardy/partner Sources                         

Hit http://us.archive.ubuntu.com hardy/main Packages                           

Hit http://us.archive.ubuntu.com hardy/restricted Packages                     

Hit http://us.archive.ubuntu.com hardy/universe Packages                       

Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     

Hit http://packages.medibuntu.org hardy/non-free Packages                      

Hit http://packages.medibuntu.org hardy/free Sources                

Hit http://packages.medibuntu.org hardy/non-free Sources            

Get:2 http://ppa.launchpad.net hardy Release [27.6kB]               

Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages  

Hit http://us.archive.ubuntu.com hardy-updates/main Packages

Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources

Hit http://us.archive.ubuntu.com hardy-updates/main Sources

Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources

Hit http://us.archive.ubuntu.com hardy-updates/universe Sources

Ign http://ppa.launchpad.net hardy/main Packages

Hit http://us.archive.ubuntu.com hardy-updates/universe Packages

Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages

Hit http://us.archive.ubuntu.com hardy-security/restricted Packages

Hit http://us.archive.ubuntu.com hardy-security/main Packages

Hit http://us.archive.ubuntu.com hardy-security/restricted Sources

Ign http://ppa.launchpad.net hardy/main Packages

Ign http://ppa.launchpad.net hardy/main Sources

Hit http://us.archive.ubuntu.com hardy-security/main Sources

Hit http://us.archive.ubuntu.com hardy-security/multiverse Sources

Hit http://us.archive.ubuntu.com hardy-security/universe Sources

Hit http://us.archive.ubuntu.com hardy-security/universe Packages

Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages

Hit http://us.archive.ubuntu.com hardy-proposed/restricted Packages

Get:3 http://ppa.launchpad.net hardy/main Packages [23.9kB]

Hit http://us.archive.ubuntu.com hardy-proposed/main Packages

Hit http://us.archive.ubuntu.com hardy-proposed/multiverse Packages

Hit http://us.archive.ubuntu.com hardy-proposed/universe Packages

Hit http://ppa.launchpad.net hardy/main Packages       

Hit http://ppa.launchpad.net hardy/main Sources

Fetched 51.5kB in 1s (45.2kB/s)

Reading package lists... Done

usr@usr-laptop:~$ sudo apt-get upgrade

Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

usr@usr-laptop:~$ sudo apt-get install epiphany-browser

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Some packages could not be installed. This may mean that you have

requested an impossible situation or if you are using the unstable

distribution that some required packages have not yet been created

or been moved out of Incoming.



Since you only requested a single operation it is extremely likely that

the package is simply not installable and a bug report against

that package should be filed.

The following information may help to resolve the situation:



The following packages have unmet dependencies:

  epiphany-browser: Depends: epiphany-gecko but it is not going to be installed or

                             epiphany-webkit but it is not installable

E: Broken packages

usr@usr-laptop:~$ 

```

---

### Post by Julius on 2008-05-25
If neither firefox or konqueror work, why would expect epiphany to? 
Epiphany uses gecko I guess, so if firefox didn't work, this probably wouldn't work either.

Anyway, why dont you try installing epiphany-gecko before installing epiphany? sounds to me like epiphany needs either of those two

Why dont you try opera?

---

### Post by pixel :-) on 2008-05-25
try installing with synaptic

try firefox 2

try [http://getswiftfox.com/]("http://getswiftfox.com/") it's basically firefox 32bit made to work in 64bit.If 3 doesn't work try 2.

---

### Post by Kilz on 2008-05-26
> **pixel :-) said:**
> try installing with synaptic

try firefox 2

try [http://getswiftfox.com/]("http://getswiftfox.com/") it's basically firefox 32bit made to work in 64bit.If 3 doesn't work try 2.

[Swiftweasel may be a better choice]("http://swiftweasel.tuxfamily.org/") as it is free and open sourec. Swiftfox is a proprietary application. Also Swiftfox does not have a 64bit version, the version for 64bit is actually 32bit.

---

### Post by Sef on 2008-05-26
> The following packages have unmet dependencies:

  epiphany-browser: Depends: epiphany-gecko but it is not going to be installed or

                             epiphany-webkit but it is not installable

E: Broken packages



For broken packages, go to System > Administration > Synaptic Package Manager > Edit > Fix Broken Packages (Click on) > then see if you can download epiphany.

---

### Post by soxs on 2008-05-26
In case it is cause by broken packages this should fix it:
To fix broken packages/ dependencies:
```
sudo dpkg --configure -a
sudo apt-get install -f
```Remove all your browsers and try reinstalling them
```
sudo apt-get purge firefox epiphany opera && sudo apt-get install firefox epiphany
```

---

### Post by tooferson5 on 2008-05-26
> **Julius said:**
> If neither firefox or konqueror work, why would expect epiphany to? 
Epiphany uses gecko I guess, so if firefox didn't work, this probably wouldn't work either.

Anyway, why dont you try installing epiphany-gecko before installing epiphany? sounds to me like epiphany needs either of those two

Why dont you try opera?

tried install both dependencies and neither work.  so if it is not a problem with the browsers then it is a problem with the os i guess.  didnt like opera for windows so id doubt id like it for hardy.

used synaptic to fix packages and then tried to install, didnt work.  tried sudo dpkg --configure -a
sudo apt-get install -f
and they did not work.  did not remove my browsers yet, dont know if it is that big of a deal to me.

---

### Post by tooferson5 on 2008-05-30
ive solved my problem.  the culprit was the kde-desktop.  i never used it so i ditched it and cleaned up everything that it leaves behind and then i was able to install epiphany.

---

