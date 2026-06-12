---
title: "[SOLVED] warcraft 3 replays"
date: 2007-12-07
forum: Wine
---

### Post by luke16 on 2007-12-07
In the win version of warcraft 3, when you patch it to the latest version via battlenet, it auto associates replays for the game so that when you download them from your browser, it will launch the game and you will start viewing the replay. Of course, this never happens in linux. Trying to right click on a downloaded replay file and select open with other application and then selecting war3.exe doesn't work either, as wine just launches the game and it goes to the main menu.

Has anyone ever dealt with this or know what to do to fix this?

---

### Post by dethredic on 2007-12-09
I need to know this too. anyone?

---

### Post by dethredic on 2007-12-10
can anyone help us?

---

### Post by karth on 2007-12-10
The windows' .exe files are just regular files for linux, meaning they can't be executed alone.
You must use Wine to launch war3.exe.

That said, there must be a way to feed the war3.exe launch command with a replay file, Windows' way, i.e. "C:\Program Files\Warcraft3\war3.exe replay.ext" (of course, it may not be the correct syntax, but that's the idea). All you'd have to do is to tell the shell prompt
```
**wine** "C:\Program Files\Warcraft3\war3.exe replay.ext"
```

As for your specific problem, you might have to write a script that takes the path to your replay file, and builds a wine command line, and then runs it. Mark that script executable and tell ubuntu to open the replays with that script, which hopefully will take care of everything.

---

### Post by dethredic on 2007-12-10
Now to make the script... I have no ideas.

Got an idea as to where to start?

---

### Post by luke16 on 2007-12-10
> **karth said:**
> The windows' .exe files are just regular files for linux, meaning they can't be executed alone.
You must use Wine to launch war3.exe.

That said, there must be a way to feed the war3.exe launch command with a replay file, Windows' way, i.e. "C:\Program Files\Warcraft3\war3.exe replay.ext" (of course, it may not be the correct syntax, but that's the idea). All you'd have to do is to tell the shell prompt
```
**wine** "C:\Program Files\Warcraft3\war3.exe replay.ext"
```

As for your specific problem, you might have to write a script that takes the path to your replay file, and builds a wine command line, and then runs it. Mark that script executable and tell ubuntu to open the replays with that script, which hopefully will take care of everything.
The correct syntax would put the second " right after war3.exe i think, otherwise you end up getting file not found error. Even after I put the replay name and path after the initial command, it still war3 still doesn't want to load the replay when it loads.

I think it might be more complex than just putting the replay name after the command. In the windows version, I recall it not being a matter of simple file association, ie, telling windows to launch the replay with war3.exe wouldn't work, so I'm not sure exactly what the patch that enables this operation to occur in windows did to make it work right. That's where the problem lies.

I sent an email to blizzard tech support for this (not naming my OS of course), so maybe through them I can get some light shed on how the win version does this.

---

### Post by dethredic on 2007-12-10
Thanks Luke, keep me up to date on this.

---

### Post by luke16 on 2007-12-14
Success! Thanks to [email]jond.support@blizzard.com[/email], I now know that the key argument to use is "loadfile".

So the actual command would be:
```
wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -loadfile "C:\Program Files\Warcraft III\replays\replay.w3g"
```


Now comes the hard part, which is figuring out how to make the os use that argument when it encounters .w3g files and launch war3 with them. For this, I will need help from someone more experienced with ubuntu than I am, as I am unfamiliar with exactly how the os currently launches programs with files.

---

### Post by karth on 2007-12-15
So, given these news, I have written this script...
I'm still having some trouble with it, since it seems the paths are incorrectly handled by the shell when the script is run.

Basically, it's a script in which you modify the variables at the top to match your setup. The you run it as "./wa3_replay replay.w3g" and it builds the wine command line with wineprefix (if any) with proper args

i.e. " ./war3_replay replay.w3g " outputs
```
env WINEPREFIX="/home/whatever/.winesth" wine "C:\Program Files\Warcraft3\war3.exe" -loadfile "C:\Program Files\Warcraft3\replay\replay.w3g
```

here is the code for my script (also attached). Since I'm not very familiar with bash scripting, it may not be functionnal yet, but that's the idea. If anybody could fix it...

```
#!/bin/bash

MAX_ARGS=1
WAR3DIR_PATH_WIN="C:\\Program Files\\Warcraft3"
WAR3DIR_PATH_LINUX="/home/karth/.winewar3/drive_c/Program Files/Warcraft3"
WAR3EXE_NAME="war3.exe"
WAR3_WINEPREFIX="/home/karth/.winewar3"


if  [ $# != $MAX_ARGS ];
then
	echo "Syntax: war3_replay replay_file";
else
	if [ -e "${WAR3DIR_PATH_LINUX}/${WAR3EXE_NAME}" ];
	then
		echo "war3.exe found.............. yes";
	else	
		echo "war3.exe found.............. no";
		echo "Fatal error: war3.exe not found.";
		echo "Fatal error: ${WAR3DIR_PATH_LINUX}/${WAR3EXE_NAME}: no such file or directory.";
		exit;
	fi
	
	if [ -e "${WAR3DIR_PATH_LINUX}/replay/${1}" ];
	then
		WINECOMMAND="env WINEPREFIX=\"${WAR3_WINEPREFIX}\" wine \"${WAR3DIR_PATH_WIN}\\${WAR3EXE_NAME}\" -loadfile \"${WAR3DIR_PATH_WIN}\\replay\\${1}\"";
		${WINECOMMAND}
	else
		echo "Fatal error: There is no such file: $1.";
		echo "Fatal error: Please verify the path to the replay file";
	fi
fi
```

---

### Post by luke16 on 2007-12-16
> **karth said:**
> 
here is the code for my script (also attached). Since I'm not very familiar with bash scripting, it may not be functionnal yet, but that's the idea. If anybody could fix it...

```
#!/bin/bash

MAX_ARGS=1
WAR3DIR_PATH_WIN="C:\\Program Files\\Warcraft3"
WAR3DIR_PATH_LINUX="/home/karth/.winewar3/drive_c/Program Files/Warcraft3"
WAR3EXE_NAME="war3.exe"
WAR3_WINEPREFIX="/home/karth/.winewar3"


if  [ $# != $MAX_ARGS ];
then
	echo "Syntax: war3_replay replay_file";
else
	if [ -e "${WAR3DIR_PATH_LINUX}/${WAR3EXE_NAME}" ];
	then
		echo "war3.exe found.............. yes";
	else	
		echo "war3.exe found.............. no";
		echo "Fatal error: war3.exe not found.";
		echo "Fatal error: ${WAR3DIR_PATH_LINUX}/${WAR3EXE_NAME}: no such file or directory.";
		exit;
	fi
	
	if [ -e "${WAR3DIR_PATH_LINUX}/replay/${1}" ];
	then
		WINECOMMAND="env WINEPREFIX=\"${WAR3_WINEPREFIX}\" wine \"${WAR3DIR_PATH_WIN}\\${WAR3EXE_NAME}\" -loadfile \"${WAR3DIR_PATH_WIN}\\replay\\${1}\"";
		${WINECOMMAND}
	else
		echo "Fatal error: There is no such file: $1.";
		echo "Fatal error: Please verify the path to the replay file";
	fi
fi
```

Hmmm. I know next to nothing about scripts, so please bear with me:
The "-loadfile \"${WAR3DIR_PATH_WIN}\\replay\\${1}\"";
part of the script would mean that the directory that you launch the replays from would have to remain static due to the WAR3DIR_PATH_WIN being an constant? And also, the ${1} part of it would be the replay name itself? Would there be any way to make the folder location that leads to the replay itself dynamic, ie you can launch the replays from anywhere, have the os call on the script, and have the script know what the location of the script and that part of itself accordingly?

---

### Post by dethredic on 2007-12-19
anyone else done work on this?

---

### Post by luke16 on 2008-01-04
I had a friend make this for me.

```
#!/bin/bash
wine /home/userdir/.wine/drive_c/Program\ Files/Warcraft\ III/war3.exe -loadfile "$*"
```This should work. I can now just double click on a replay and have the game load the replay. Much simpler than I thought possible for this sorta thing.

Change the user dir and any thing else in the path to make it work. It works when its in any directory in program files of the wine directory, but no where else. I think it has to do with warcraft not knowing linux directories or somesuch thing.

EDIT:
A quick fix is just to modify the script to copy the thing to a place that war3 does understand. Thus, I have modified the script to:
```
#!/bin/bash
cp "$*" /home/userdir/.wine/drive_c/Program\ Files/Warcraft\ III/replay/currentreplay.w3g
wine /home/userdir/.wine/drive_c/Program\ Files/Warcraft\ III/war3.exe -loadfile "C:/Program Files/Warcraft III/replay/currentreplay.w3g"
```
I'd prefer to not have to make a copy as it's inefficient, but am not skilled enough to try to translate native linux directories to win ones.

---

### Post by Melhisedek on 2008-02-05
Please excuse me for my ignorance folks. I have made the script and made it executable. When I run it Warcraft starts with an error message saying "Replay file could not be loaded" When I double click on some replay file I get the message "no application suitable has been found for opening this file"

So can anyone explain to me in a few steps, where do I put this script and how do I start replays afterwards... Judging from posts here people can just doubleclick them and it works...

---

### Post by luke16 on 2008-02-05
> **Melhisedek said:**
> Please excuse me for my ignorance folks. I have made the script and made it executable. When I run it Warcraft starts with an error message saying "Replay file could not be loaded" When I double click on some replay file I get the message "no application suitable has been found for opening this file"

So can anyone explain to me in a few steps, where do I put this script and how do I start replays afterwards... Judging from posts here people can just doubleclick them and it works...

Generally, you should put your own scripts in ~/bin i think, but I don't think ubuntu recognizes that path by default, so for now, put the script below in a file using a text editor, lets call the file "war3", then from the terminal, go to the directory where you made the file, then:

```
chmod +x war3
sudo mv war3 /usr/local/sbin
```Then, right click on the replay itself, go to properties, then the "open with" tab, then click add, then under "use custom command", type in "war3" or whatever you named the file and hit enter/ok.

This puts the script to a place where ubuntu will look for it. "echo $PATH" command will tell you where ubuntu looks for commands. Editing the path involves changing your .bashrc by adding something like PATH=/home/user/bin+allotherpaths to it.

EDIT: Use this for the file instead, I've made it a bit more efficient by using links instead of physically copying the file. Don't forget to put in your username where necessary:
```
#!/bin/bash
ln -fs "$*" /home/USERDIRECTORY/.wine/drive_c/Program\ Files/Warcraft\ III/replay/currentreplay.w3g
wine /home/USERDIRECTORY/.wine/drive_c/Program\ Files/Warcraft\ III/war3.exe -loadfile "C:/Program Files/Warcraft III/replay/currentreplay.w3g"


```

---

### Post by Melhisedek on 2008-02-05
I think I'm almost there... 

I did as you said. When I doubleclick on any replay now, a new file called currentreplay.w3g gets created in warcraft III/replay folder. It is the same size as the original replay as well. Sadly nothing more happens :/ 
Perhaps I'm still doing something wrong

---

### Post by Melhisedek on 2008-02-05
Sorry, sorry, false alarm :) 
It works flawlessly now !!! Mate I LOVE the ground you walk on !!!

---

### Post by ph0nph0n on 2008-04-08
Thanks for that trick Luke!
I worked a little bit on your code, so that it can work with applications other than warcraft: [Open a file with a specific application from wine]("http://ubuntuforums.org/showthread.php?t=749684").

---

