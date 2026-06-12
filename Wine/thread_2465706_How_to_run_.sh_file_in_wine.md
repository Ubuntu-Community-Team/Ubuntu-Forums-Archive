---
title: "How to run .sh file in wine?"
date: 2021-08-09
forum: Wine
---

### Post by snype9lives on 2021-08-09
I have a game and idk how to run it in wiine and the only thing the installer came with was a .sh file and since wine was being a bitch I dont know how to run it! so someone please  help

---

### Post by ajgreeny on 2021-08-09
Shell files with an .sh file suffix are Linux shell files and will not, as far as I'm aware, run in Wine or Windows.

Give us more information and someone may be able to help you more.
What is the game and how old is it?
Have a looked in the database at wine-hq at [https://appdb.winehq.org/](https://appdb.winehq.org/) which may help more; if it is lower than Gold or Platinum rated you are probably wasting your time trying to use Wine.

---

### Post by TheFu on 2021-08-09
It is likely that the .sh file (extensions don't actually matter in Unix/Linux) actually runs WINE and the program.  As a first guess, perhaps you need to change the permissions on that file to have execute privileges?

If the file is located in ~/Downloads/foo-foo-foo.sh
then run
```
chmod +x ~/Downloads/foo-foo-foo.sh
```
and to run the command, use
```
~/Downloads/foo-foo-foo.sh
```
It is likely that file would need to be manually modified for your system, but who knows?

There must be 100K different .sh files used to launch random WINE commands and you haven't exactly been clear with any specifics.

---

### Post by wyattwhiteeagle on 2021-08-23
> **snype9lives said:**
> I have a game and idk how to run it in wiine and the only thing the installer came with was a .sh file and since wine was being a bitch I dont know how to run it! so someone please  help

One would think that the builder of that game would give info with that game on how to run that *.sh file...it is a shell file that is, or needs to be, activated to run in a terminal, but not in Windows command prompt, or power shell.

But Windows cmd, cmd (admin), power shell, as mentioned above, I don't believe Wine or Windows can read the information in the sh file.

You might seek a user's manual, how to install, or any command lines that begin with ```
chmod a+x
``` or ```
chmod 700
```

chmod a+x is the exact same as chmod 700. Typing either one, not both, will work.

It's code for the terminal in Ubuntu, not Wine, to activate the sh file.

For Ubuntu, it would look something similar to this...

> In Ubuntu's Terminal, enter chmod 700 /home/__________/... (complete the line with the location of the sh file. then add the complete name of the file at the end of that line.

That only activates the sh file, so now in the terminal, type it in again but without the chmod 700. Only type the path and filename.

In Window's cmd (Admin), if you downloaded the sh file into the Downloads folder, you would enter C:\Users\snype9lives\Downloads\This_Game.sh
In Ubuntu's terminal, it would be /home/snype9lives/downloads/This_Game.sh

so in Ubuntu terminal; type (fill in the blanks with the rest of the path and the name of the file)
> chmod a+x /home/_________/_______.sh

Then in the terminal, type it again but without the chmod a+x
> /home/_________/_______.sh

---

### Post by TheFu on 2021-08-23
wyattwhiteeagle.  Some mistakes in understand are in the post above.

> chmod a+x is the exact same as chmod 700. Typing either one, not both, will work.
This is incorrect.
```

$ chmod 700 file1
$ chmod a+x file2
$ chmod a=x file3
```
results in 
```
-rwx------  Aug 23 11:09 file1*
-rwx--x--x  Aug 23 11:09 file2*
---x--x--x  Aug 23 11:09 file3*
```

If the files are all scripts, then only file1 and file2 can be run and only by the owner. Nobody else (I'm making assumptions about the parent directory permissions).
file3 can only be run if it is a compiled program, but anyone can run it.

To allow everyone on the system to run a script, the permissions need to be 755.
```
-rwxr-xr-x  Aug 23 11:13 file4*
```
Read and Execute are required to run a script.  The script file isn't in the PATH for each userid, then the invocation must point to the file location.  There are many different ways to accomplish that between absolute and relative paths.

usera and userb exist and want to run a script in the other user's script directory.

Let's say that usera puts her scripts in /home/usera/scripts/
and 
usera puts her scripts in /home/usera/bin/.

So, if usera wants to run a script that she wrote, she could use 
```
~/scripts/myscriptA
~usera/scripts/myscriptA
/home/usera/scripts/myscriptA
```
from anywhere on the computer.  If she uses a shell and her PWD is her HOME, then she can use any of those 3 options above or 
```
scripts/myscriptA
```
If her pwd is ~/scripts/, then she'd need to use
```
./myscriptA
```
or any of the first 3 examples above.

If userb wants to run myscriptA in /home/usera/scripts/myscriptA, then 
```
~usera/scripts/myscriptA
/home/usera/scripts/myscriptA

```can be used from anywhere on the system.  While unlikely, userb could also cd into ~/usera and use 
```
scripts/myscriptA
```
or cd into ~/scripts/ and use
```
./myscriptA
``` too.

Similarly, userb's script myscriptB in ~/bin/ of that userid .... what are the ways that script could be run both by userb or usera using relative and absolute paths?

Whether WINE can run a bash script ... well, I don't actually know, but I'd guess that is unlikely, since WINE would need to use a command.com or cmd.exe or powershell.exe interpreter, not bash.  Bash has been ported to Windows, so perhaps a bash environment under WINE could be possible, but it would be odd since WINE provided the C: and D: disk ideas that bash doesn't know about.

---

### Post by wyattwhiteeagle on 2021-08-23
Thank you for the corrections.

Even then, there should be some form of information somewhere for whatever game is made.

The OP doesn't mention the name of the game  

OP may be trying to create a script that is a game script...if that's the case then my info is useless to the OP.

On the other hand...the "game" may not exactly be an sh file

The op doesn't give much detail.

Windows has something called a "god" prompt. If op has Windows installed in Wine's "Local Disk (C:\)", it will explain his situation just a little better.

It's mainly the lack of info that result's in unresolved or all kinds of wrong information.

---

### Post by TheFu on 2021-08-23
If I were scripting to run a Windows program under WINE, I have the script run under bash (probably) and do all the setup there, then call **WINEPREFIX=~/.wine-for-game-A wine name-of-windows-program** from that script.  The WINEPREFIX is how to have completely different setups for each program to work under WINE.  I suppose people will use different tools to accomplish that too - I haven't used wine in over a year and haven't used it weekly since around 2015.  Used to have Quicken running about 80% good under Wine, but an update broke that. A few hours of attempted fixes didn't work, so I switched back to using a virtual machine running Windows.  I still to Quicken stuff that way every week.

Wine is great when things are easy.  That seldom happens anymore. Programs created in 2002 usually run really easy under wine, provide they don't have COM objects - which will never be supported.

---

