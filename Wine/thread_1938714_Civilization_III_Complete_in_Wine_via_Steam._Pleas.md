---
title: "Civilization III Complete in Wine via Steam. Please Help!"
date: 2012-03-10
forum: Wine
---

### Post by MuseOD on 2012-03-10
When I run my game, I get a dialogue box saying  "Error Code 13"   and the game stops working and closes. When I looked on the ubuntu/wine page for advice, it gave me this, and I don't understand what it wants me to do. 
"
For the game to run, the following must be done:  copy the file: .wine/dosdevices/c:/Program Files/Steam/steamapps/common/sid meier's civilization iii complete/Conquests/LSANS.TTF  to: .wine/dosdevices/c:/Program Files/Steam/steamapps/common/sid meier's civilization iii complete/Conquests/LSANS.fot  then open a console and browse to: .wine/dosdevices/c:/Program Files/Steam/steamapps/common/sid meier's civilization iii complete/Conquests/  and type the following command: sudo chown root LSANS.*  This prevents the following two errors: Error loading font (Error code 13) Error loading font (Error code 28)  With this the game should now run. Then to remove graphical glitches, uncheck "Allow the window manager to control the windows" in winecfg.  From there, everything should work perfectly. But the music pops a little, that can probably be tweaked."

I've tried doing what it says, despite not understanding it and it still won't work. I also have a disk version, but that doens't work either. 

Any ideas? 
PS. I am using natty narwhal.

---

### Post by mcagr81 on 2012-03-12
I am also having the same problem with the terminal in ubuntu 11.04.I have installed wine and steam and civ III thru steam.According to instructions on wine forum in order to play civ some font files need to be moved within the wine folder which i have done but it also informs to do the following: 

then open a console and browse to:
.wine/dosdevices/c:/Program Files/Steam/steamapps/common/sid meier's civilization iii complete/Conquests/

and type the following command:
sudo chown root LSANS.*

when I open the terminal I am able to change directoy to .wine/dosdevices/c but when I try to change to the next "program files" I get message in terminal not found. I type in ls command and does list "program files"  why am I NOT able to change to directoy "program files"

below is actual steps in termial I have done

mike@ubuntu:~$ cd .wine
[email]mike@ubuntu:~/.wine[/email]$ cd dosdevices
[email]mike@ubuntu:~/.wine[/email]/dosdevices$ cd c:
[email]mike@ubuntu:~/.wine[/email]/dosdevices/c:$ ls
Program Files  users  windows
[email]mike@ubuntu:~/.wine[/email]/dosdevices/c:$ cd program files
bash: cd: program: No such file or directory
[email]mike@ubuntu:~/.wine[/email]/dosdevices/c:$

---

### Post by Toz on 2012-03-12
Put the directory name in quotes:
```

$ cd "~/.wine/dosdevices/c:/Program Files/Steam/steamapps/common/sid meier's civilization iii complete/Conquests/"
$ sudo chown root LSANS.*
```

The reason is that Linux interprets the space as a separation of commands and needs to be escaped. The easy way is to enclose the directory name in quotes. The other option is to escape every space with a backslash ala:
```
cd ~/.wine/dosdevices/c\:/Program\ Files/Steam/steamapps/common/sid\ meier\'s\ civilization\ iii\ complete/Conquests/
```
...note that the ' and the : also needed to be escaped.

---

