---
title: "Wanting to install Wine 4.6 Dev"
date: 2019-04-22
forum: Wine
---

### Post by bionic3epl on 2019-04-22
I'm wanting to install Wine 4.6 Dev & I can't seem to do it. I keep running into this> eddie@eddie-HP-Notebook:~$ sudo apt install --install-recommends winehq-develReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 winehq-devel : Depends: wine-devel (= 4.6~bionic)
E: Unable to correct problems, you have held broken packages.
According to Synaptic, I don't have any Broken Packages.

Btw, I did switch back to Bionic Beaver 18.04.2 LTS.

Please help me fix this.

---

### Post by thenailedone on 2019-04-24
Just install what is missing...

In your case it is *wine-devel*.
```
sudo apt install wine-devel
```

It will more than likely complain about something like wine-devel:i386 being needed... so you install that first. Once it installs OK you install wine-devel. Then you install winehq-devel (not sure why this is happening but anyway...)

Personally I find (especially for gaming) that Wine staging is the way to go... - [Link for what it is worth]("https://wiki.winehq.org/Ubuntu").

---

### Post by bionic3epl on 2019-04-24
I tried what you said but I got this instead:

eddie@eddie-HP-Notebook:~$ sudo apt install wine-devel
[sudo] password for eddie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine-devel : Depends: wine-devel-amd64 (= 4.6~bionic) but it is not going to be installed
              Depends: wine-devel-i386 (= 4.6~bionic)
E: Unable to correct problems, you have held broken packages.

---

### Post by thenailedone on 2019-04-24
As I said in my top post it will most likely give this error...

So start with:
```
sudo apt install wine-devel-i386
```
See the error code says this is missing...

If it gives another error install what ever that error says is pending.

If no errors then:
```
sudo apt install wine-devel
```
Then if no errors:
```
sudo apt install winehq-devel
```

---

### Post by bionic3epl on 2019-04-24
I got the error again & I tried doing what it said & I got this:

eddie@eddie-HP-Notebook:~$ sudo apt install wine-devel-i386
[sudo] password for eddie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine-devel-i386:i386 : Depends: libfaudio0:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.
eddie@eddie-HP-Notebook:~$ sudo apt install libfaudio0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libfaudio0:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libfaudio0:i386' has no installation candidate
eddie@eddie-HP-Notebook:~$ sudo apt-get install libfaudio0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libfaudio0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libfaudio0' has no installation candidate

---

### Post by bionic3epl on 2019-04-24
It keeps saying that I need libfaudio. How do I add it to repository & install it?

---

### Post by thenailedone on 2019-04-25
In my first post I added this [link]("https://wiki.winehq.org/Ubuntu").

In it, at the top as to bring attention to it, it states: **"Beginning with Wine 4.5, the wine-devel packages for Ubuntu 18.04, 18.10, and 19.04 require libfaudio0 as a dependency. Since the distro does not provide it, libfaudio0 packages can be downloaded from the OBS. See [https://forum.winehq.org/viewtopic.php?f=8&t=32192](https://forum.winehq.org/viewtopic.php?f=8&t=32192) for details."**

Going to the link given this post has all the instructions how to add the required repo's and have the needed libfaudio file available when you install wine. But seeing the way this thread has been going I give you the information copy pasted from said post:

Ubuntu 18.04:
Download the [Release.key]("https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/Release.key"). Navigate to the directory you downloaded it to and install it with
```
sudo apt-key add Release.key
```

Add the repository:
```
sudo apt-add-repository 'deb [https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/](https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/) ./'
```

Then update:
```
sudo apt update
```

Now start by installing the wine-devel-i386 and work your way back as per my post just before this one.

---

