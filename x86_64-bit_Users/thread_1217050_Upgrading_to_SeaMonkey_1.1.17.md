---
title: "Upgrading to SeaMonkey 1.1.17"
date: 2009-07-19
forum: x86 64-bit Users
---

### Post by cybrsaylr on 2009-07-19
I completely forgot how to do an upgrade using tar.gz format.
Been doing all with terminal or Synaptic package manager.

Here's what they recommend;

Download Now
SeaMonkey 1.1.17

    * Windows, English (13 MB)
    * Linux GTK2, English (14 MB)

Can someone help me out here?

---

### Post by timgood on 2009-07-19
This is taken from the installation files:

Installation Instructions
-------------------------------

Note: If you install in the default directory (which is usually /usr/local/seamonkey), or any other directory where only the root user normally has write-access, you must start SeaMonkey first as root before other users can start the program. Doing so generates a set of files required for later use by other users.  However, do not use sudo to run the installer as root because that can damage your profile.


To install SeaMonkey by downloading the SeaMonkey installer, follow these steps:

1. Create a directory named seamonkey (mkdir seamonkey) and change to that directory (cd seamonkey).
	
2. Click the link on the site you're downloading SeaMonkey from to download the installer file (called seamonkey-x.xx.en-US.linux-i686.installer.tar.gz or similar) to your machine.

3. Change to the seamonkey directory (cd seamonkey) and decompress the archive with the following command:

  tar zxvf sea*.tar.gz

The installer is now located in a subdirectory of seamonkey named seamonkey-installer.

4. Change to the seamonkey-installer directory (cd seamonkey-installer) and run the installer with the ./seamonkey-installer command.

5. Follow the instructions in the install wizard for installing SeaMonkey.

Note: If you have a slower machine, be aware that the installation may take some time. In this case, the installation progress may appear to hang indefinitely, even though the installation is still in process.

6. To start SeaMonkey, change to the directory where you installed it and run the ./seamonkey command.

---

### Post by chiques on 2009-07-23
Hey timgood,
I tried to use those installation instructions but SeaMonkey did not update after the GUI finished. 

I installed SeaMonkey using the Package Manager and I ran the update using the terminal. I have a feeling they are in different directories.

---

### Post by cybrsaylr on 2009-07-23
I also had problems upgrading using timgood's directions.

Does anyone have the code to run this upgrade in terminal?

---

### Post by ken78724 on 2009-08-02
The installation question is beyond me; I'd like to use Seamonkey; its composer does what I need to create web sites using XP on another PC. 

So how do we install Seamonkey?   Ken

---

### Post by ken78724 on 2009-08-02
does this do it? 
  1) Open terminal
  2) enter - tar xjf wbar-1.3.3.tbz2.tar.bz
cd wbar-1.3.3
make
sudo make install
  3) specify seamonkey 1.1.17 and password
This gives you an option to a direct download with no follow through

---

### Post by ken78724 on 2009-08-02
But I don't have Seamonkey working. Do you?

---

### Post by cybrsaylr on 2009-08-02
I use SeaMonkey 1.1.13 without any problems. It renders video very well IMO.

I just wanted to upgrade to 1.1.17 because of those security warnings but haven't been able to figure out how as yet.

---

### Post by cybrsaylr on 2009-08-13
Looks like not many people are using SeaMonkey.

---

### Post by Yellow Pasque on 2009-08-14
Try the x86-64 version: [http://www.seamonkey-project.org/releases/#contrib](http://www.seamonkey-project.org/releases/#contrib)

---

### Post by cybrsaylr on 2009-08-20
I just did the updates to kernel 2.6.28-15 a few minutes ago and it included updates to the SeaMonkey 1.1.17 version! I now have the newer version of SeaMonkey 1.1.17 I was looking for in the OP.

So that problem is solved LOL.
But unfortunately I'm still running the older kernel 2.6.28-13 instead of the newer 2.6.28-15 kernel. But that bug is in another thread.
[http://ubuntuforums.org/showthread.php?t=1241599&page=2](http://ubuntuforums.org/showthread.php?t=1241599&page=2)

---

### Post by ken78724 on 2009-09-05
Q: since I'm installing for the 1st time, not updating, I extracted & ended up with this home/k78724/Desktop/seamonkey... what should be my next steps? What ought to be done? 

oh yes, I checked this morning in the synaptic file manager and saw I am running the newest kernel

---

### Post by cybrsaylr on 2009-09-05
I really didn't do anything.
I watched while the updates were being installed to kernel 2.6.28-15 and noticed in the updates SeaMonkey 1.1.17 was included in those updates and it auto upgraded SeaMonkey. When updates finished I rebooted and after launching SeaMonkey, saw the 1.1.17 version was running now.

---

