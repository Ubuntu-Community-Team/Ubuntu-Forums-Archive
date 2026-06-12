---
title: "Running .exe files"
date: 2014-06-13
forum: Wine
---

### Post by liam13 on 2014-06-13
Hi,

Just brought this new lapptop and it loaded up with this Ubuntu software, i really dont have much of a clue about it.

All i want to do is download my poker sites so i can continue playing, however i can't seem to download anything from the internet. All is get is this error message.

Archive:  /home/liam/Downloads/PartyPokerSetup(2).exe
[/home/liam/Downloads/PartyPokerSetup(2).exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/liam/Downloads/PartyPokerSetup(2).exe or
           /home/liam/Downloads/PartyPokerSetup(2).exe.zip, and cannot find  /home/liam/Downloads/PartyPokerSetup(2).exe.ZIP, period.

Can't download anything, no idea whats going on, any help would be great!

---

### Post by kc1di on 2014-06-13
Hi liam13  and welcome to Ubuntu,

Ubuntu is Linux and linux is** not windows.** and will not run .exe files natively.  You'll have to use a program called Wine. or Playon Linux to run your Poker game. 

You can install both of them from the software center. 
good Luck.

---

### Post by /ADM on 2014-06-13
It is because Ubuntu is a Linux distribution, it cannot read and execute Windows '.exe' files.  It is throwing an error because to Ubuntu, this .exe is not executable and it does not know what it is.

Hit CTRL+ALT+T and type in the Terminal 'sudo apt-get install wine' then hit y for yes and it will download a whole bunch of stuff for WINE to work.  You can also follow the above suggestion and install via the ubuntu software center.  WINE is a program which can execute Windows programs.  There are a bunch of tutorials for learning about how to use it on the web.

Somebody more knowledgable about WINE and it's usage can hopefully comment, though I am not sure if your Poker apps would run on it (it is not a Windows Replacement program).

---

### Post by Mark Phelps on 2014-06-13
The link is to the WineHQ site page for PartyPoker -- maybe there's some useful info there:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1567]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1567")

---

