---
title: "Help installing CoD2"
date: 2013-05-03
forum: Wine
---

### Post by krunoman on 2013-05-03
[CENTER][SIZE=2][COLOR=#ff0000][FONT=arial black][I][B][SIZE=4]Call Of Duty 2 HELP[/SIZE]
[/B][/I][/FONT][/COLOR][/SIZE]
Hello, me and my friend are new in our VPS that uses UBUNTU but our VPS is located in Germany but we are in Croatia, and we can't install call of duty 2 on VPS, how do we install it? We are beginners and sorry if i posted wrong but can you help us? How is the second way to install cod2 files on VPS without paying ticket to go to Germany -.-? Thanks![/CENTER]

---

### Post by TheFu on 2013-05-03
Call of Duty appears to work well in WINE according to [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2609](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2609) .  Follow the instructions there for the winetricks to be installed **before** installing CoD2.

However, VPS is not meant to be used for graphical gaming.  Usually a remote desktop is not included and the steps to get a functioning desktop for something like LibreOffice is about the limit for any desktop accessed over the internet.  That doesn't mean it is impossible to get "something" working - look into whether your VPS supports the "spice" protocol to see if higher-end graphics can be supported at all.

For non-gaming remote desktops on a VPS, I use FreeNX as the server and NoMachine's NX-client on my local desktop - MS-Windows or Linux clients work well from around the world, but I would never try gaming with them.  I have and do use the remote desktop from 9000 miles away - Nepal, Korea, Turkey, and Europe back to a private cloud in the USA. NX is the best, secure, solution that I've found for this. It is based on ssh, so get your ssh-keys working on the VPS and follow these FreeNX setup instructions: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)  Should take 10 minutes if you are new, 5 minutes if you've setup FreeNX before.

Again, I doubt the performance you want for CoD will be possible on a remote machine anywhere - even on the same subnet/LAN segment.

Good luck!

---

### Post by krunoman on 2013-05-03
I'm sorry but i wanted to say ubuntu server edition and CoD2 server.. HELP!

---

### Post by Microrobot on 2013-05-04
Try contacting the VPS company that you are paying for, try asking them for information on this.

---

