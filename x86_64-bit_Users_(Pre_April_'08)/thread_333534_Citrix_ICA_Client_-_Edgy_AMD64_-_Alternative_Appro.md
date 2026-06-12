---
title: "Citrix ICA Client - Edgy AMD64 - Alternative Approach"
date: 2007-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by dbw6993 on 2007-01-07
**[SIZE="4"]UPDATED: Added installation of common 32-bit Libraries (If you've already installed Firefox32, you've got these)[/SIZE]**

[COLOR="Red"]***WARNING: I possess just enough linux/Ubuntu knowledge to be dangerous, so **please use discretion when following these instructions!**
Any feedback you can provide on the long-term viability or unintended consequences of this approach would be much appreciated.

Note: Also, due to the configuration of my company's Citrix server I use a custom Program Manager connection and cannot validate the efficacy of this approach when using a website portal. However, the mozilla/firefox plugin is installed and I see no reason for it not to work.[/COLOR]


[SIZE="5"]**Install working Citrix ICA Client in Edgy AMD64 Environment**[/SIZE]


[SIZE="3"]**Step 1: Install basic missing Citrix dependencies**[/SIZE]
[INDENT]```
sudo aptitude install libxaw7 libmotif3
```[/INDENT]


[SIZE="3"]**Step 2: Install Common 32-bit libraries   [COLOR="Red"](Update)[/COLOR]**[/SIZE]
[INDENT]
Install 32-bit compatibility libraries (if you've installed firefox32 already, skip this step)
[INDENT]```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32
```[/INDENT][/INDENT]


[SIZE="3"]**Step 3: Install Needed 32-bit Open Motif libraries to /usr/lib32**[/SIZE]

[INDENT]Setup a temporary environment
[INDENT]```
mkdir -p ~/tmp/Citrix
cd ~/tmp/Citrix
```[/INDENT]

Download a recent i386 libmotif3 .deb package to the above folder
[INDENT]```
wget http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-1.4_i386.deb
```[/INDENT]

Use dpkg to extract the package
[INDENT]```
dpkg -x libmotif3*i386.deb libmotif
```[/INDENT]

Copy the libraries to /usr/lib32
[INDENT]```
sudo cp libmotif/usr/lib/*.so.* /usr/lib32/
sudo cp -r libmotif/usr/lib/X11/bindings /usr/lib32/X11/
```[/INDENT][/INDENT]


**[SIZE="3"]Step 4: Download and Install Citrix Client[/SIZE]**

[INDENT]Setup a temporary environment
[INDENT]```
mkdir -p ~/tmp/Citrix/Client
cd ~/tmp/Citrix/Client
```[/INDENT]

Download the GZipped (.tar.gz) client to folder created above: [http://www.citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186#top]("http://www.citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186#top")

Unpack and run install script
[INDENT]```
tar -xvf linuxx86.tar.gz 
sudo ./setupwfc 
```[/INDENT]

Select Option 1 when prompted
[INDENT]```
Select a setup option:

 1. Install Citrix ICA Client 9.0
 2. Remove Citrix ICA Client 9.0
 3. Quit Citrix ICA Client 9.0 setup

Enter option number 1-3 [1]: **[COLOR="Red"]1[/COLOR]**
```[/INDENT]

Enter preferred installation location 
[INDENT]```
Please enter the directory in which Citrix ICA Client is to be installed.
[default /usr/lib/ICAClient] 
or type "quit" to abandon the installation: 
```
*Note: You can safely ignore the warning about setting an environment variable for a non-standard location, the shortcut created will accommodate the path you specify*[/INDENT]

Select Option 3 to exit the Installation Script
[INDENT]```
Select a setup option:

 1. Install Citrix ICA Client 9.0
 2. Remove Citrix ICA Client 9.0
 3. Quit Citrix ICA Client 9.0 setup

Enter option number 1-3 [1]: **[COLOR="Red"]3[/COLOR]**
Quitting Citrix ICA Client 9.0 setup.
```[/INDENT][/INDENT]


[SIZE="3"]**Step 5 (Optional): Clean up temporary environment**[/SIZE]
[INDENT]The installation files are not needed anymore, and the setwupwfc script can be found in the installation path you specified
[INDENT]```
cd ~ && rm -rf ~/tmp/Citrix/
```[/INDENT][/INDENT]


:-D **[SIZE="3"]Step 6: Congratulations, Enjoy your Citrix ICA Client![/SIZE]**
[INDENT]A shortcut will be located in the 'Applications' --> 'Internet' Menu for those who need to change global ICA settings and create custom connections
[/INDENT]

---

### Post by jkroto on 2007-01-11
dbw,
nice guide.  I can confirm that I was able to get this working with FF32 installed using the citrix web interface to my work.

The only thing in your guide that confused me for a second is the location of the install.  You mention to ignore the warning about the location/path but don't tell users what the path should be.  I assumed you meant the 'lib32' path but others might not understand.

> 
Enter preferred installation location 
[INDENT]```
Please enter the directory in which Citrix ICA Client is to be installed.
[default /usr/lib/ICAClient] 
or type "quit" to abandon the installation: 
```
*Note: You can safely ignore the warning about setting an environment variable for a non-standard location, the shortcut created will accommodate the path you specify*[/INDENT]


Also, for FF32 users, FF will not know how to open the link so you have to either set it in the preferences for FF before, or when the pop up asks, browse to the lib32 -> ICAClient and select 'wfica'

Thanks again for the info, this is much easier than what I was doing before.

---

### Post by dbw6993 on 2007-01-11
Thanks jkroto,

Glad to know this worked for someone else as well. Also glad to know the web client works as well, and thanks for the note on how to configure Firefox to use wfica. 

With regard to the installation location, the Citrix client itself won't care where you install it. The default (/usr/lib/ICAClient) will work just fine. I personally installed it to /opt/local/ICAClient, being a former Gentoo user and in the habit of dumping manual installations into /opt/local.

---

### Post by juanhunglow on 2007-03-05
> **dbw6993 said:**
> **[SIZE="4"]UPDATED: Added installation of common 32-bit Libraries (If you've already installed Firefox32, you've got these)[/SIZE]**


dbw6993,
Don't know if you are still keeping up with this thread.  I started a new thread [**here**]("http://www.ubuntuforums.org/showthread.php?p=2250944#post2250944") with respect to the new Citrix client version 10.

I can't get version 10 to work.  version 9 worked using your instructions. 
don't know if you have version 10 or have it working.  Any chance you still have the version 9 of the citrix client download? I can't find anywhere to download v. 9 from.

Now I know why to save stuff like that!!!

---

### Post by toupeiro on 2008-04-04
I can confirm this method still works in 8.04 beta!  great guide!!

---

### Post by matogrosso on 2008-05-12
Not working for me.

When try the Menus icon I get :
Couldn't find "/home/oscar/.ICAClient/pna_menu_items".

And when I try the Citrix client icon it hangs.

Please help

---

