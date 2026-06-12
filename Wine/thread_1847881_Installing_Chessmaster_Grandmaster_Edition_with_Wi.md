---
title: "Installing Chessmaster Grandmaster Edition with Wine"
date: 2011-09-21
forum: Wine
---

### Post by ualpar on 2011-09-21
I got Chessmaster Grandmaster Edition (latest one),ubuntu 11.04 and Wine 1.2.
I can't install the game on my computer. When I try, an error message comes. Can you please help me?

---

### Post by Toz on 2011-09-21
Hello and welcome to the forums.

Exactly what error message are you getting?

According to: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10198]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10198"), this game should work. However, in both instances where the game is rated Gold, it is running wine version 1.3.

You can try updating to a more recent version of wine ([https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa")). The basic procedure, from the command line, is:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine
```

---

### Post by ualpar on 2011-09-22
Firstly thank you for your help.
I updated wine 1.2 to wine 1.3 as you said but I have the same error message (error code 1627) with the installation stopped before it starts.

Forgive me for my poor English,thank you :)

---

### Post by Toz on 2011-09-22
No worries. I installed this game last night so I know it works. Is there anymore information about the error message other than "error code 1627"? Any other text accompanying the error message?

Also, how are you installing the game? Are you installing from a command line terminal or double-clicking setup.exe? Do you have the CD or are you installing from an .iso?

---

### Post by Enigmapond on 2011-09-22
I would also suggest installing playonlinux and install the game through there.

---

### Post by ualpar on 2011-09-22
> **Toz said:**
> No worries. I installed this game last night so I know it works. Is there anymore information about the error message other than "error code 1627"? Any other text accompanying the error message?

Also, how are you installing the game? Are you installing from a command line terminal or double-clicking setup.exe? Do you have the CD or are you installing from an .iso?


   No, there is no other text that accompanies the error message. I try to install the game by double-clicking setup.exe.
 In fact, I installed the game 3 days ago with wine 1.2, but the game does not start after installation. Then uninstalled the game to start over the installation process, but now I am faced with this error message.

---

### Post by ualpar on 2011-09-22
> **Enigmapond said:**
> I would also suggest installing playonlinux and install the game through there.

Thank you,I'm trying it right now. :)

---

### Post by ualpar on 2011-09-22
Thank you very much to you two :) Finally I could install the game with PlayOnLinux :) Thank you :)

---

