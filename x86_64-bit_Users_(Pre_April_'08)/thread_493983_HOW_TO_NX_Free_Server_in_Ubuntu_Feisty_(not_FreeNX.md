---
title: "HOW TO: NX Free Server in Ubuntu Feisty (not FreeNX)"
date: 2007-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by JAmerican on 2007-07-06
I recently was experimenting with the NoMachine NX Free Client and Server and got it to work on my PC running AMD64 Ubuntu Feisty. So I decided to share it with everyone since I couldn't find a straight forward guide. Also, I realized that people were still requesting help in this area.

I am a novice at Ubuntu and Linux but the guides and help at this forum has pushed me along in understanding the basics in getting Ubuntu to work correctly. If I post anything in this guide that you may have issues with, please post it as I am learning as well. Thanks for the help and this is a little contribution to say thanks.

NoMachine offers Free server and client with 64-bit support and it works great. I really wonder why do people struggle with FreeNX?

I downloaded ([http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)) all the following under Linux x86_64 in DEB format:

NX Node
NX Client
NX Free Edition
NX Server Manager (not sure if this is necessary but I installed it anyway)

Double click to install all of these. Do it in this order because NX Free Edition requires the Client and Node before it is installed. 

Follow this : [http://stuffem.wordpress.com/2007/03/13/geek-gal-setting-up-nx-terminal-server-on-ubuntu/](http://stuffem.wordpress.com/2007/03/13/geek-gal-setting-up-nx-terminal-server-on-ubuntu/)

**BUT** before following it exactly, where it says:

> 
Edit the file /etc/nxserver/node.conf
sudo gedit /etc/nxserver/node.conf


*If you are using KDE, replace **gedit** with **kate**.*

Replace **/etc/nxserver/node.conf** with **/usr/NX/etc/node.cfg**

After all that you will need to enable the user and password databases, add an administrative user and enable that user. Use the following commands to do so:

```
sudo gedit /usr/NX/etc/server.cfg
```
*If you are using KDE, replace **gedit** with **kate**.*

In this file, look for:

**#EnableUserDB = "0"** and replace with **EnableUserDB = "1"**

**#EnablePasswordDB = "0"** and replace with **EnablePasswordDB = "1"**

Then close the server.cfg file and run this in the terminal:

```
sudo /usr/NX/bin/nxserver --useradd USERNAME --administrator
```

*where USERNAME is a username you have selected (make sure it has no spaces)*

You should be prompted to provide a password. Enter a password of your choice. Once this is done. 

Enable the user with the following command:

```
sudo /usr/NX/bin/nxserver --userenable USERNAME
```

*where USERNAME is the username you selected above. *

You should be all set. Go to another machine (whether its connected to your network or not) and download the [NoMachine NX client](http://www.nomachine.com/download.php) for that Operating system. 

Open the **NX Connection Wizard**. You should be greeted with a small popup. 

Click Next. 

Enter the session name (preferably something you can distinguish from other sessions you create for other comptuers or operating systems). Then, enter your selected no-ip host information in the host box. For port, enter 22 if you did NOT change the port number in following the Geek Gal guide I linked to above. The speed I selected was LAN because my laptop that I am using to connect to my desktop is using WiFi. Choose WAN if you are using a cell phone signal to connect your desktop machine. Choose MODEM if you have a 56k modem. 

Click Next.

For your desktop select **Unix** and **GNOME**. _This will create a new session from the one that is on your desktop. This meaning, you will not see what is on your desktop screen. To login to the same session, select **Shadow** instead of Unix._ If your remote PC's screen is smaller than your desktop screen (which is true for most laptops), I would suggest you create a new session because shadowing a session will look distorted. Also, a new session prevents anyone that is near your desktop PC from accessing it while shadowing unlocks your desktop system allowing anyone to see what you are doing or interact with what you are doing. For the size of your remote desktop, select what is preferable to you. I selected Fullscreen. Uncheck Disable SSL encryption of all traffic for better security. 

Click Next. 

If you want a shortcut on your desktop, check that option. Also check **Advanced Configuration**.

Click Finish. 

You should see a small dialog box with Username, Password and Session drop-down. Click the **Configure**  button.

In Advanced Tab...
For system, select Grab the keyboard when the client has focus. If you have trouble tying or using your keyboard, you may have to select the correct keyboard when logged into Ubuntu: **Menu > System > Preferences > Keyboard** and choose **Layouts** tab and the correct Keyboard model. I still have trouble with my PowerBook G4 keyboard so you may encounter some problems of your own.

In Services Tab, this is optional as they don't seem to work for me. 

Check **Enable SMB Printing and File Sharing** (I believe this is for Windows only since my Mac can't use these options with Ubuntu). Check **Enable Multimedia Support** (was able to access media player but audio was not sent to my laptop so test this out).
Once that is all done. Click Save and Ok.

Now type in the username, password, select your session and enjoy Remote Desktop Heaven :)

As others have said, it is so much faster than Microsoft's Remote Desktop Protocol. 

If you have any suggestions or problems, let me know. I'll try to help out as much as I can.

One bit of advice for those struggling with 64-bit machines. Not everyone's needs are met in a 64-bit OS software wise or driver wise. But I recommend those who don't require to have applications that are in 32-bit only to hang on and work through it. I've somewhat vowed to go to 64-bit since I spent so much on my own hardware getting ready for Vista (lol). If it doesn't work out, there is always 32-bit. 

[IMG]http://jamerican.net/JJFiles/Ubuntu/NXRemote.jpeg[/IMG]

JAmerican :popcorn:

---

### Post by JAmerican on 2007-07-06
Come on people. At least someone respond. Did people know how to do this already or something?

JAmerican

---

### Post by crush304 on 2007-07-07
what is the advantage of all that vs. X forwarding over ssh? I didn't look into it very much but it looks like it accomplishes the same thing?

---

### Post by Cappy on 2007-07-07
It's highly compressed and uses less bandwidth so you have faster response times and faster screen updates than X forwarding/vnc. Best available remote connection software there is (there is FreeNX too).

---

### Post by JAmerican on 2007-07-07
> **Cappy said:**
> It's highly compressed and uses less bandwidth so you have faster response times and faster screen updates than X forwarding/vnc. Best available remote connection software there is (there is FreeNX too).

FreeNX doesn't support 64-bit to my knowledge. All I can say is that NoMachine's Remote Desktop application really makes you feel liek you are on your computer.

I was able to see videos and TV (although both laggy). Beryl doesn't work but I think its for the best.

The greatest problem I see is the keyboard is not automatically configured for the remote device and once its changed. you will have to change it back on your desktop.

JAmerican

---

### Post by crush304 on 2007-07-07
thanks for the info, I might give it a try

---

### Post by Drock on 2007-07-07
Thanks for the tutorial, worked great!

---

### Post by JAmerican on 2007-07-07
Sorry for the slight attitude in my second post. Was a little anxious for a response. Wanted to make sure it also was a good tutorial. 

JAmerican

---

### Post by booticon on 2007-07-09
Thanks a lot for this HOWTO. This is *fast*.

---

### Post by lexarrow on 2007-07-10
I get an error like "Server not installed or NX access disabled"  and I think it's because I haven't set up SSH correctly. I didn't change the ports because I have a fixed address. I read somewhere it's because of the SSH keys that don't match between the server and the client but I couldn't figure it out.

Here's what I get: 

```
NX> 203 NXSSH running with pid: 5568
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.33 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
```

Please help

---

### Post by JAmerican on 2007-07-10
> **lexarrow said:**
> I get an error like "Server not installed or NX access disabled"  and I think it's because I haven't set up SSH correctly. I didn't change the ports because I have a fixed address. I read somewhere it's because of the SSH keys that don't match between the server and the client but I couldn't figure it out.

Here's what I get: 

```
NX> 203 NXSSH running with pid: 5568
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.33 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
```

Please help

At which step exactly do you get that error? 

JAmerican

---

### Post by lexarrow on 2007-07-11
> **JAmerican said:**
> At which step exactly do you get that error? 

JAmerican

I get that error just after "Connected to 192.168.1.33"

---

### Post by lexarrow on 2007-07-11
I managed to fix it. It wasn't reading the right auth. keys file.

 Thanks for a great howto!

---

### Post by dilidon on 2007-07-11
Can you please elaborate as to how did you get it to read the "right" keys then?
I have the same problem... havent been able to sort it out yet following various guides.

---

### Post by crush304 on 2007-07-12
got it installed, no problems

I think node was dependent on client so I think order should be:
client
node
free server

works great, thanks

---

### Post by lexarrow on 2007-07-13
> **dilidon said:**
> Can you please elaborate as to how did you get it to read the "right" keys then?
I have the same problem... havent been able to sort it out yet following various guides.

I am using webmin and I went to ssh server then authentification. At the User authorized keys file line check default.

Let me know if you need more help.

---

### Post by sstarr on 2007-07-14
I had this NX Free Server setup working on Dapper. I'm now using a fresh install of Feisty. I installed the latest client, node, server and the latest mac client, 3.0.0-68. The Key Mapping is completely wrong, I don't think a single key is correct. In the past I used xmodmap to fix a few broken keys. I'm not sure where to begin trying to fix all of them. Has anybody seen this issue or know where the underlying problem lies?

---

### Post by Pseudo-Morph on 2007-07-14
> **sstarr said:**
> I had this NX Free Server setup working on Dapper. I'm now using a fresh install of Feisty. I installed the latest client, node, server and the latest mac client, 3.0.0-68. The Key Mapping is completely wrong, I don't think a single key is correct. In the past I used xmodmap to fix a few broken keys. I'm not sure where to begin trying to fix all of them. Has anybody seen this issue or know where the underlying problem lies?

I too have this same problem. Just this morning I managed to find a workaround that makes this combination usable but far from perfect.

From my notes:

*When connecting from Mac OS X Gnome k/b layout will need to be changed to Macintosh Old in System|Prefrences|Keyboard|Layouts|Keyboard Model. This is not a complete fix at this point. Ctrl key appears not to work.*

I have not done extensive testing on this yet though I have not encountered this error when connecting using an XP virtual machine running in Parallels.

Please let me know if a better solution is found.

On a side and maybe related note, before setting up NX I tried VNC via an SSH tunnel with very similar results. I could get a gnome desktop working correctly however had key mapping issues. My googling left me with the impression that in the VNC case this was a result of a bug in the Gnome version packaged wtih 7.04. I did not find a fix, nor did I test to see if keyboard type 'Macintosh Old' fixed this issue.

---

### Post by sstarr on 2007-07-14
Thanks, using Macintosh Old made the keyboard usable. 

I used Xmodmap to fix the broken keys that I needed to have working. I can't find a better solution for right now. If you want to apply the mapping...
Copy this text to a file on your linux machine. I called it nxkeymap.
After you log into your linux machine, run xmodmap nxkeymap from the terminal.


!run xmodmap thisfilename
!run xev from the terminal to display keycodes if more mapping is needed.
!Key listings: [http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap](http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap)

clear mod1
clear mod2
clear mod3
clear mod4
clear mod5
clear control

!Mac command key
keycode 63 = Control_L

keycode 67 = Control_L
keycode 58 = grave asciitilde
keycode 49 = semicolon colon 

!arrow keys
keycode 131 = Left
keycode 132 = Right
keycode 133 = Down
keycode 134 = Up

add Control = Control_L

---

### Post by booticon on 2007-07-15
Anybody get sound working? Anything fancy that needs to be configured other than Enabling Multimedia on the client side?

---

### Post by Pseudo-Morph on 2007-07-17
> **sstarr said:**
> Thanks, using Macintosh Old made the keyboard usable. 

I used Xmodmap to fix the broken keys that I needed to have working. I can't find a better solution for right now. If you want to apply the mapping...


Cheers, this is handy as a hack to get things operational.

I'm not a fan of keeping things this way as a perm solution though as I'm getting sick of changing the k/b every time I log in from a different location. I also find it's a hastle if I have both a remote and a local xsession for the same user as a change to the k/b changes it for both users.

---

### Post by AkuKalle on 2007-07-20
i am unable resume suspended session from another computer(it is only possible where i started). Is there possibility to configure NX server allow resume from any computer?

---

### Post by ranish on 2007-08-21
Good and extremely helpful tutorial.
Well dome!:)

---

### Post by jdbartlett on 2007-08-22
Thanks very much for the keys map, sstarr--works great.

Does anyone have sound working?  Like JAmerican, I ticked the multimedia support box but got no sound.  I have the latest NoMachine NX client & server, am connecting to Ubuntu 7.04, and am encrypting all traffic.  My Shorewall configuration blocks most ports; could the multimedia stream require an extra port be opened?

---

### Post by laserjet on 2007-08-23
I installed NS Free Server, on Ubuntu 7.04, and it works fine, great product. But noticed only 2 users can login, for more users to login you have to buy NX server which is costly.

Any idea how to give more users to access Ubuntu GUI remotes desktop?

Thanks

---

### Post by jdbartlett on 2007-08-23
You could try VNC instead.  I can't recommend FreeNX.

---

### Post by laserjet on 2007-08-23
I tried VNC but its not working, I enabled Remote login from System > Administration > Login Window > Remote > Style = same as local. Even open 5900 port in FireStarter, but vncviewer can't connect to Ubuntu. Any idea?

I want multiple users to connect to Ubuntu to open their own session.

Thanks

---

### Post by j.stagner on 2007-09-02
FINALLY!!!!  I've been trying to fix a 'broken' NX installation for almost a week now.  It was working just perfectly, then one day it stopped.  Everything I've tried has been absolutely useless until I ran across this HOW TO and how to enable the user and password db.

Thank you so much for posting this topic.

---

### Post by ashrack on 2007-09-02
On my server I have both Win2k3 server and UBUNTU DAPPER set up.
Although I use Win2k3. But I would like to migrate to UBUNTU DAPPER.
So I've installed Nomachines CLIENT, NODE, SERVER. And set it up.

Then I go to another machine on our lan and install the Nomachine
client for Linux. And thru it I connect to the server using the SHADOW
session. But the thing is that it is quite slow. Much slower than
Windows 2003 RDP. Is it possible to speed things up?

I would really like to start using UBUNTU on the server also but a
fast Remote Desktop is a must and thus far only MS RDP was fast
enough.


The server PCs specs are:
Ubuntu DAPPER
DURON 1600MHZ
512MB RAM
Nvidia TNT2 PRO 32MB with Nvidia binary blob installed.

---

### Post by Debuggern on 2007-09-10
Cheers! Works perfectly, the easiest nx how to I have come acrossed. FreeNX how to's didn't just do it. Finally I can work from school on my linux box.

---

### Post by Barticus on 2007-09-26
Just a quick note from another noob user;

If you're using Feisty Fawn 64 bit AND you want to use a new key pair, the new .pub key that you generate needs to be imported into the  /usr/NX/home/nx/.ssh/authorized_keys2 file, and the private key needs to be imported into your client.

At least if that is incorrect, I'm sure someone will be along to tell me so :)

---

### Post by dad311 on 2007-09-26
I  installed 3 NX files (client,node & server) + the Ubuntu sshd server and everything worked.  

Why edit the /usr/NX/etc/server.cfg or /etc/nxserver/node.conf?

---

### Post by touser on 2007-10-04
I am trying to follow this tutorial but on the download page on nomachines website [http://www.nomachine.com/download-package.php?Prod_Id=2](http://www.nomachine.com/download-package.php?Prod_Id=2)

there is no link to download server, only client + node?

---

### Post by Pseudo-Morph on 2007-10-04
Thats funny, when I vist that page (or navigate to the download page) under the heading "Download NX Free Edition for Linux - x86_64" I can see three orange buttons. "Download Client" "Download Node" "Download Server".

[http://www.users.on.net/~pseudomorph/ScreenCap.png](http://www.users.on.net/~pseudomorph/ScreenCap.png)

---

### Post by Fraoch on 2007-10-04
Thanks for the how-to!  Worked perfectly!

I still prefer TightVNC though, but I couldn't get it working on the Ubuntu machine.

---

### Post by MrGando on 2007-10-04
I am having some problems....

Well I got the server up in my ubuntu box, I have no problems when I try to connect to my ubuntu. ( I use the mac client to connect to NX ... from my mac to my ubuntu Desktop  ( 7,04 i386 ).

I run VMware in ubuntu... with windows Xp. I need that to do some work here at home. The problem is that when I connect to my ubuntu box , and open VMware player. It loads Xp perfectly but the keyboard layout is ALL messed up. ( all the keys work wrong )

Anyone can help me ???

---

### Post by Pseudo-Morph on 2007-10-05
This is a known problem with the Mac client, I have the same issue connecting to my Ubuntu box from my macbook, I also experienced a simillar problem with VNC and have a feeling from my hunting around that the issues may be related and may have something to do with the way the version of Gnome packaged with 7.04 handles mac keyboards.  

Have a read back through this thread, there is a little discussion on it, I also found this NX tutorrial recentlythat deals with how to remap your keybord to get the mac client working. I have not yet had a chance to have a go at this. 

[http://rubric-cube.blogspot.com/feeds/posts/default](http://rubric-cube.blogspot.com/feeds/posts/default)

If you get it working correctly please let us know.

---

### Post by bandoba on 2007-10-08
I have couple of questions.

1. The /usr/NX/etc/server.cfg file has these lines
# If both 'EnableUserDB' and 'EnablePasswordDB' are set to 0, any 
# user being authenticated by SSHD account will be enabled to connect
# to the system.

If I understand that comment correctly, then we **don't **really need to have EnableUserDB = 
"1" and EnablePasswordDB = "1". Instead they should be set to 0 and any user on system who can connect over ssh should be able to connect using NX client as well. Is that correct understand? If not, can you please elaborate why not.

BTW, I tried setting both the settings to 0 and it didn't work.

2. I followed OP's first post and now, I am able to connect to my home Ubuntu Feisty AMD64 box but it shows a gray blank window inside the main window and stops there. Could that be because of Beryl?

See the attachment below.

BTW, I let this window sit there for almost 10 mins and after that I hear the standard Ubuntu login music and see that rectangular window shown everytime you login. But immediately after that the NX client closes down the connection and the window. Has anybody seen this? Any idea what can be wrong?

Thanks

---

### Post by BlkPhoenix on 2007-10-08
First off, thanks to you cheif for trying to make Ubuntu easier for those that are still feeling their way through this maze that is Linux.  I've been tryin gto get this remote desktop to w0rk for weeks and it not work and I'm getting frustrated.  I can connect to my Kubuntu machine when I'm on my local network at home. However I'm unable to connect to my machine from my office. I've gotten a DynDns IP address. I have the ddclient running...my router is port forwarded. Everytime I try to connect to my machine I get a timeout error. What am I doing wrong?  Please help.

---

### Post by dad311 on 2007-10-08
> **BlkPhoenix said:**
> First off, thanks to you cheif for trying to make Ubuntu easier for those that are still feeling their way through this maze that is Linux.  I've been tryin gto get this remote desktop to w0rk for weeks and it not work and I'm getting frustrated.  I can connect to my Kubuntu machine when I'm on my local network at home. However I'm unable to connect to my machine from my office. I've gotten a DynDns IP address. I have the ddclient running...my router is port forwarded. Everytime I try to connect to my machine I get a timeout error. What am I doing wrong?  Please help.

Have you tried doing a simple ssh from the office to home?  Can you ping your home address from the office?

---

### Post by bandoba on 2007-10-12
Here is the update:

I tried logging in as another user who doesn't have desktop effects enabled or have Beryl Manager and I could successfully connect using NX. 

But I was wondering, if there is any way I can update my configuration to detect if it is connecting over NX and disable these apps. Any idea if and how can I do that?

TIA.

> **bandoba said:**
> I have couple of questions.

1. The /usr/NX/etc/server.cfg file has these lines
# If both 'EnableUserDB' and 'EnablePasswordDB' are set to 0, any 
# user being authenticated by SSHD account will be enabled to connect
# to the system.

If I understand that comment correctly, then we **don't **really need to have EnableUserDB = 
"1" and EnablePasswordDB = "1". Instead they should be set to 0 and any user on system who can connect over ssh should be able to connect using NX client as well. Is that correct understand? If not, can you please elaborate why not.

BTW, I tried setting both the settings to 0 and it didn't work.

2. I followed OP's first post and now, I am able to connect to my home Ubuntu Feisty AMD64 box but it shows a gray blank window inside the main window and stops there. Could that be because of Beryl?

See the attachment below.

BTW, I let this window sit there for almost 10 mins and after that I hear the standard Ubuntu login music and see that rectangular window shown everytime you login. But immediately after that the NX client closes down the connection and the window. Has anybody seen this? Any idea what can be wrong?

Thanks

---

### Post by kostin on 2007-10-19
On Ubuntu 7.10 Gutsy Gibbon I have next error in "Detail" of client:

NX> 203 NXSSH running with pid: 7770
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 900 -c, /usr/lib/nx/nxserver, ,  ...
NX> 900 Won't execute arbitrary commands.
NX> 280 Exiting on signal: 15

Can anybody help me?

---

### Post by dad311 on 2007-10-19
> **kostin said:**
> On Ubuntu 7.10 Gutsy Gibbon I have next error in "Detail" of client:

NX> 203 NXSSH running with pid: 7770
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 900 -c, /usr/lib/nx/nxserver, ,  ...
NX> 900 Won't execute arbitrary commands.
NX> 280 Exiting on signal: 15

Can anybody help me?

How did you install NX?  I just installed  NX  after a fresh install of Gusty.  Below are the steps I used:

Download and install the NXClient, NXNode and NXServer in this order from [http://www.nomachine.com/download-package.php?Prod_Id=4](http://www.nomachine.com/download-package.php?Prod_Id=4)

Install ssh server using "sudo apt-get install ssh"

---

### Post by exactopposite on 2007-11-06
> **touser said:**
> I am trying to follow this tutorial but on the download page on nomachines website [http://www.nomachine.com/download-package.php?Prod_Id=2](http://www.nomachine.com/download-package.php?Prod_Id=2)

there is no link to download server, only client + node?


i had the same problem. if i loaded the page in a browser other than firefox the server button showed up, but it wouldn't show in firefox. i realized it was the adblock extension. the name of the image for the button is b_downlo**adServer**.gif. the adblock extension was picking up the last part of that name (which i put in bold) and blocking it.

---

### Post by kostin on 2007-11-07
**dad311**, install  on clean Ubuntu 7.10 works. But not on upgraded from 7.04 :(

---

### Post by dad311 on 2007-11-07
> **kostin said:**
> **dad311**, install  on clean Ubuntu 7.10 works. But not on upgraded from 7.04 :(

Yes, I did install NX just after a clean install of Ubuntu 7.10.  It does not matter what OS you have,  I believe its always better to do clean install instead of a upgrade.  

I have two x64 PCs running Ubuntu 7.10.  I install NX by doing the following steps:

sudo apt-get install ssh

Download and install the NXClient, NXNode and NXServer in this order from: [http://www.nomachine.com/download-package.php?Prod_Id=4](http://www.nomachine.com/download-package.php?Prod_Id=4)

---

### Post by Inxsible on 2007-11-07
I have installed the NXServer and am trying to connect to it from my XP machine but i keep getting this message:

     ```
NX> 203 NXSSH running with pid: 4384
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host *<host-name>* port *<port number>*: Connection refused
```The host-name is my no-ip host name and the port is the one that I used instead of 22. Can someone tell me what's wrong please?

The status on my linux box seems ok
     ```
$sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 110 NX Server is running.
NX> 999 Bye.
```Thanks

---

### Post by Inxsible on 2007-11-08
Can someone help me out with this problem please?

---

### Post by bilbodigi on 2007-11-08
> **Inxsible said:**
> I have installed the NXServer and am trying to connect to it from my XP machine but i keep getting this message:

     ```
NX> 203 NXSSH running with pid: 4384
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host *<host-name>* port *<port number>*: Connection refused
```The host-name is my no-ip host name and the port is the one that I used instead of 22. Can someone tell me what's wrong please?

The status on my linux box seems ok
     ```
$sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 110 NX Server is running.
NX> 999 Bye.
```Thanks

I had the same problem, it was my firewall (F-Secure) on the XP-machine who refused the connection.
Now it runs.

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

### Post by dlstyley on 2007-11-20
very interested in amd_64 version.  

many thanks!

---

### Post by wilbur.harvey on 2007-11-24
Yes, I would like them as well.

I have followed the instructions to build and install, but I get the following error

NX> 105 /usr/lib/nx/nxserver: line 465: -pi: command not found

Any ideas?

I am using Gutsy amd_64

Thanks

---

### Post by dlstyley on 2007-11-29
On a whim, I went here and installed the x86_64 deb package and it "just worked".  I have Gutsy on AMD64, so maybe I just got lucky?  Isn't x86_64 somewhat different than AMD64?  

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

---

### Post by daflame on 2007-11-30
> **dlstyley said:**
> On a whim, I went here and installed the x86_64 deb package and it "just worked".  I have Gutsy on AMD64, so maybe I just got lucky?  Isn't x86_64 somewhat different than AMD64?  

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

Again those are NOT FreeNX, they are NX Server Free Edition.  They are very different.  The free version on their site is limited to only 2 connections and is commercial.  FreeNX is eactly that free as in open source and unlimited except by your computer's hardware.  If you want current FreeNX packages go to:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

### Post by daflame on 2007-11-30
> **wilbur.harvey said:**
> Yes, I would like them as well.

I have followed the instructions to build and install, but I get the following error

NX> 105 /usr/lib/nx/nxserver: line 465: -pi: command not found

Any ideas?

I am using Gutsy amd_64

Thanks

As I posted earlier, you can get current packages here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

You may want the Debian source path updates, since the paths in the version supplied are not correct for Debian.  I can supply the sources that I receieved these from if you want on that site as well.  Just let me know.

---

### Post by daflame on 2007-11-30
> **dlstyley said:**
> On a whim, I went here and installed the x86_64 deb package and it "just worked".  I have Gutsy on AMD64, so maybe I just got lucky?  Isn't x86_64 somewhat different than AMD64?  

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

Again those are NOT FreeNX, they are NX Server Free Edition.  They are very different.  The free version on their site is limited to only 2 connections and is commercial.  FreeNX is eactly that free as in open source and unlimited except by your computer's hardware.  If you want current FreeNX packages go to:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

