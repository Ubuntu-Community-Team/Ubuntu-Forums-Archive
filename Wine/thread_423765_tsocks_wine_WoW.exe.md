---
title: "tsocks wine WoW.exe"
date: 2007-04-26
forum: Wine
---

### Post by DezSP on 2007-04-26
Hi all. This is my first post here, having managed to get most of Ubuntu up and running through the endless knowlege of Goodle, but the problem I'm facing now is so obscure (I think) that there's very little to be found about it.

Basically, in order to play WoW on my connection, I need to tunnel it through a SSH connection via SOCKS 5 (in order to bypass the firewall). I can set up the tunnel using ssh and tsocks just fine, and it works for most applications, but when I try to run WoW with it, things become less kind.

WoW simply gives me a "Disconnected from server" message less than a second after it starts trying to connect. Running from Terminal, the following error(s) come up:

```
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
11:48:35 libtsocks(16084): IP (0.0.0.0) & 11:48:35 libtsocks(16084): SUBNET (255.255.255.0) != IP on line 19 in configuration file, ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
```

No idea if they're related or not. Any ideas?

Oh yes, and my tsocks configuration:

```
local = 192.168.0.0/255.255.255.0
local = 127.0.0.1/255.255.255.0

server = 127.0.0.1
server_type = 5
server_port = 1080
```

---

### Post by RobEvans89 on 2007-11-22
Sorry to resurrect an old thread, but any news on this?

---

### Post by RandyRyan00 on 2007-11-23
I am having a similar issue.  Whenver I attempt to connect to the game, I am kicked immediately with the "Disconnected from Server" message.  I managed to get it to work earlier, but now it seems to never want to let me on.

I'm not going through any tunneling, just straight through a NAT, even with DMZ setup, still same issue, so I don't think it's on the network side.  Seems to be something to do with the software configs in Wine.  

I'm fairly new to Linux so still learning but I've tried all the suggestions I can find and none seem to help at all.

If anyone has some help would be really appreciated.

Randy

---

### Post by hikaricore on 2007-11-23
Randy, be aware that since around 9pm EST this evening here in the states there have been trouble with the world ,authentication, and web servers.  As it is a holiday these issues have just been coming and going with no info posted in the ugent news box ingame.  Everytime they seem to be fixed, someone else in my girl's guild can't connect.  Hopefully this is your only problem.

---

### Post by duncan_nz on 2007-12-16
I managed to get wow running via a ssh tunnel using a program called 
Freecap.

I think tsocks is just plain buggy and it won't work with wine.

I could write a howto if you like :)

---

### Post by DezSP on 2007-12-17
I gave up on this issue quite a while ago and it's no longer needed for me. Isn't Freecap proprietary though?

---

### Post by duncan_nz on 2007-12-17
Its free and open source :)

---

### Post by trebor147 on 2008-01-07
> **duncan_nz said:**
> I managed to get wow running via a ssh tunnel using a program called 
Freecap.

I think tsocks is just plain buggy and it won't work with wine.

I could write a howto if you like :)

Think you could write up that howto?  I find myself in the same situation.

Thanks

---

### Post by Erik765 on 2010-05-26
... Guess not. I'll try to figure it out I guess.

---

### Post by cariboo on 2010-05-26
This thread is over 2 years old. Closed

---

