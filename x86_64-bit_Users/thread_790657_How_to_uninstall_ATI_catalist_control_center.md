---
title: "How to uninstall ATI catalist control center"
date: 2008-05-11
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-05-11
I installed Ati control center today in this way :
```
mkdir ATI
cd ATI
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-4-x86.x86_64.run
```

```
chmod +x ati-driver-installer-8-4-x86.x86_64.run
sudo ./ati-driver-installer-8-4-x86.x86_64.run
```
and after restart all is wrong :(
my scrolling and maximizing and minimize are slow and everything is bad

can I uninstall ati control center ?

---

### Post by Kilz on 2008-05-11
> **DachaArh said:**
> I installed Ati control center today in this way :
```
mkdir ATI
cd ATI
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-4-x86.x86_64.run
```

```
chmod +x ati-driver-installer-8-4-x86.x86_64.run
sudo ./ati-driver-installer-8-4-x86.x86_64.run
```
and after restart all is wrong :(
my scrolling and maximizing and minimize are slow and everything is bad

can I uninstall ati control center ?

Odds are you installed more than the control center, more likly the driver also. But you didn't do any of the things that setup and configure the driver. I recommend you install the driver you have [according to this howto.]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---

### Post by DachaArh on 2008-05-11
thanks mate, but I'm not shur can I do this and not have problems again.
What do you think, should I do this ?
I have only 2 problems without these drivers :
1.When I go to System/Administration/Hardware drivers I have this :
see this image 
[http://i26.tinypic.com/14aykcl.jpg](http://i26.tinypic.com/14aykcl.jpg)
and 2.
When I minimize and maximize windows with effects I have for about a second these lines that should not be there.

---

### Post by DachaArh on 2008-05-11
I did install it and all is well, but again I can not start TV time after installing these drivers 

why is that, I realy need TVtime application ? :(

---

### Post by MaindotC on 2008-05-11
Hey, Kilz, what if I'm using Gutsy instead of bug-plagued Hardy?  This is what happens when I try and follow the tutorial:

```

311-laptop:~$ sudo apt-get install build-essential 
[sudo] password for 311:
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
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
311-laptop:~$ sudo apt-get install libc6
libc6            libc6-amd64      libc6-dev-amd64  libc6-prof
libc6.1          libc6-dbg        libc6-i686       libc6-xen
libc6.1-pic      libc6-dev        libc6-pic        
311-laptop:~$ sudo apt-get install libc6-dev
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
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is to be installed
E: Broken packages

```

---

### Post by Yellow Pasque on 2008-05-11
> what if I'm using Gutsy instead of bug-plagued Hardy? 
That's cute. You called Hardy "bug-plagued" while complaing of a bug in Gutsy. Gutsy had its fair share of bugs and the packages are relatively old now. Hardy has just been released, so the packages are the latest, and of course, that includes the inevitable bugs that come with the latest and greatest features. I suggest you try Hardy (you can repartition alongside your current Gutsy install) before knocking it.

---

### Post by Kilz on 2008-05-11
> **DachaArh said:**
> I did install it and all is well, but again I can not start TV time after installing these drivers 

why is that, I realy need TVtime application ? :(

I wish I could help, but Im not sure about that application.

> **strAlan said:**
> Hey, Kilz, what if I'm using Gutsy instead of bug-plagued Hardy?  This is what happens when I try and follow the tutorial:

```

311-laptop:~$ sudo apt-get install build-essential 
[sudo] password for 311:
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
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
311-laptop:~$ sudo apt-get install libc6
libc6            libc6-amd64      libc6-dev-amd64  libc6-prof
libc6.1          libc6-dbg        libc6-i686       libc6-xen
libc6.1-pic      libc6-dev        libc6-pic        
311-laptop:~$ sudo apt-get install libc6-dev
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
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is to be installed
E: Broken packages

```
I hope you didnt folow the link in my post, that is to a Hardy howto, not a Gutsy howto. It looks like you have broken packages in your system.

---

### Post by MaindotC on 2008-05-11
You know what it's disrespectful to developers for me to refer to Hardy as that.  I apologize.  I was thinking of putting Hardy on a different partition and contributing to the bug-reporting process but I've not done that yet.  However, from my personal experience, I never had any problems with Gutsy.  Again, I apologize for the criticism of Hardy.

---

### Post by Yellow Pasque on 2008-05-11
> Again, I apologize for the criticism of Hardy
Ah, good man. I used Gutsy from the Alpha4 release, and ripped it all apart with custom kernels and all kinds of software from source. It was a great release, but the old girl's getting a bit long in the tooth :P

---

### Post by MaindotC on 2008-05-20
Bump - can someone help me fix this dependency issue?  I've done all sorts of updates and installed programs and such but I'm still getting this message if I try and install libc6-dev.

---

### Post by Kilz on 2008-05-20
> **strAlan said:**
> Bump - can someone help me fix this dependency issue?  I've done all sorts of updates and installed programs and such but I'm still getting this message if I try and install libc6-dev.

I did a package search it looks like its looking for the Gutsy version of libc6. Did you upgrade this install from Gutsy or was it a clean install?

---

### Post by MaindotC on 2008-05-20
I'm still using Gutsy and frankly I've no desire to upgrade to Hardy.

---

### Post by MaindotC on 2008-05-24
I resolved my issue by using aptitude instead of apt.  You can see the ouput in [this thread]("http://ubuntuforums.org/showthread.php?t=804294").  Man it felt good when aptitude just kicked that dependency issue in the ***.

---

