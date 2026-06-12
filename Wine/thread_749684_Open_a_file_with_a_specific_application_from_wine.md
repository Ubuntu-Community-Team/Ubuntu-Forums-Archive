---
title: "Open a file with a specific application from wine"
date: 2008-04-08
forum: Wine
---

### Post by ph0nph0n on 2008-04-08
**EDIT**: There's a better way of doing this than I first though when writing this post. Jump to jecogul's post: [http://ubuntuforums.org/showthread.php?t=749684#post9793671]("http://ubuntuforums.org/showthread.php?t=749684#post9793671") .




-------------------------------------------------------------------------
**Ignore the rest of this post**
-------------------------------------------------------------------------


The idea behind the attached script is to be able to double-click on a file to open it with an application running with wine. The idea and the script are based on [luke16 post about associating warcraft 3 replays with wine]("http://ubuntuforums.org/showthread.php?t=633842&highlight=battlenet&page=2#14").


**HOW  IT WORKS**

The script launches an action with based on the type of the file (e.g., its extension). You'll need to write your own actions, as i only write the only one i was interested with. If you have a look at the end of the code, you'll see something like this:

```

#perform action according to file type (e.g. file extension)
#ex: wine "$winePath"drive_c/Program\ Files/Foo/foo.exe "$winTempFile"
case "$ext" in
	w3g)
		#warcraft replay file
		wine "$winePath"drive_c/Program\ Files/Warcraft\ III/war3.exe -loadfile "$winTempFile"
		;;
	*)
		#unknown file type
		wine "$inputFile"
		;;
esac

```

So basically, to start the program foo.exe when opening a .foo file (e.g. bar.foo), you would do something like:

```

#perform action according to file type (e.g. file extension)
#ex: wine "$winePath"drive_c/Program\ Files/Foo/foo.exe "$winTempFile"
case "$ext" in
	w3g)
		#warcraft replay file
		wine "$winePath"drive_c/Program\ Files/Warcraft\ III/war3.exe -loadfile "$winTempFile"
		;;
	foo)
		#foo file
		wine "$winePath"drive_c/Program\ Files/Foo/foo.exe "$winTempFile"
		;;
	*)
		#unknown file type
		wine "$inputFile"
		;;
esac

```

"**foo)**" specifies that an action will be done if the extension of the file is "foo".
"**wine "$winePath"drive_c/Program\ Files/Foo/foo.exe "$winTempFile"**" is the action to execute. Normally, you should only change "**Foo/foo.exe**" to the correct path. Note that some programs will require more arguments. Warcraft for instance, requires the "**-loadfile**" argument before the file name.
"**;;**" terminates the action.
Note that "***)**" is the default action, so don't add anything after that part, or it will never happen!


**HOW TO INSTALL**

1- download the script and unzip it.
2- move the script to appropriate place, say /usr/local/sbin.

```

sudo mv ~/Desktop/wineOpen /usr/local/sbin/

```

3- make the script executable

```

sudo chmod +x /usr/local/sbin/wineOpen

```

4- tell you system to open the desired type of file with "wineOpen". if you are using gnome:
[INDENT]a- right click on the file you wish to open[/INDENT]
[INDENT]b- click on properties[/INDENT]
[INDENT]c- go to the "open with" tab[/INDENT]
[INDENT]d- click "add"[/INDENT]
[INDENT]e- click "use custom command" at the bottom[/INDENT]
[INDENT]f- enter "wineOpen" [/INDENT]
You'll need to do that only once for each type of file. If you're not using gnome... well, sorry, but i guess you'll sort it out :)


Hope that will be of any use.

---

### Post by PeterJCLaw on 2009-04-14
Thanks for this neat script, though as I'm using it to open files in my favourite text editor ([Notepad2]("http://www.flos-freeware.ch/notepad2.html")) I found that having the name of the temporary file opened always being called linuxFileToRead rather than the actual file name (the name shows up in the title bar) a little annoying.

I've therefore thrown together a couple of lines that name the temporary file the same name as the original one:

change (line 42-52):
```
#get file extension and change it to lower case
#(even though windows doesn't care, that'll be handy later in the script)
let "extPos=`echo "$inputFile" | grep -o "\." | wc -l`+1"
ext=`echo "$inputFile" | cut -d"." -f"$extPos" | tr A-Z a-z`
if [ "$extPos" != 1 ]; then
	tempFile="$tempFolder""$tempName"."$ext"
	winTempFile="$winTempPath""$tempName"."$ext"
else
	tempFile="$tempFolder""$tempName"
	winTempFile="$winTempPath""$tempName"
fi
```
to:
```
#get file extension and change it to lower case
#(even though windows doesn't care, that'll be handy later in the script)
let "extPos=`echo "$inputFile" | grep -o "\." | wc -l`+1"
ext=`echo "$inputFile" | cut -d"." -f"$extPos" | tr A-Z a-z`

#get the file name, without the path
let "namePos=`echo "$inputFile" | grep -o "/" | wc -l`+1"
name=`echo "$inputFile" | cut -d"/" -f"$namePos" `

tempFile="$tempFolder""$name"
winTempFile="$winTempPath""$name"
```

I believe this renders the declaration of tempName on line 17 obsolete, and it can be removed.

If there's a more efficient/elegant way to achieve this a solution would be appreciated - this is my first time coding in bash (I've assumed that's what this is).

---

### Post by youarefunny on 2010-01-25
This is not working for me.

I tried to use it to open Microsoft Word documents.

EDIT:  It is now working (i changed Program\ Files/Foo/foo.exe to "Program Files/Foo/foo.exe"

But the temporary name isnt working yet.

---

### Post by ph0nph0n on 2010-01-27
Hi youarefunny,

Not sure what you mean by "the temporary name isn't working"? Can you post your updated file so I can have a look?

@PeterJCLaw: Thanks for sharing that btw ;)

---

### Post by jecogul on 2010-09-01
I solved the problem without using a shellscript by leveraging the drive Z: which points to the Linux file system.

I just entered the following command in the "Open With" dialog of Dolphin 1.3 to open a file with Word 2007:
```
wine "C:\Program Files\Microsoft Office\Office12\WINWORD.EXE" '""Z:%f""'
```

To make this persistent activate the checkbox "Remember application association for this type of file".

---

### Post by ph0nph0n on 2010-09-01
That's interesting and much more clever. Thanks for sharing the tip jecogul. I'll update my first post to link to your answer.

---

### Post by gerdb on 2011-09-20
hi,

and what does '""Z:%f""' the hell mean??

i try to open a filetype (jpg) with 

wine "path/to/irfanview" 

but there is no file opened, just the app.

How do i give wine or irfanview the current filename???

Pls help

thx in advance

---

### Post by ph0nph0n on 2011-09-24
Hi gerdb,

It refers to the current filename you're trying to open, that's why your code only opens Irfanview. I guess that also answers your second question ;)

```
wine "C:\path\to\irfanview" '""Z:%f""'
```


In case you want more details:

Windows uses letters to refers to drives. See the path to the program in jecogul example: "**C:**\Program Files\[...]". Under Wine, because it's an implementation of Windows, you can't access your linux files directly. However they are accessible through a drive mounted in **Z:**.

To make it simple, Wine cannot see your Linux files through the usual Windows path C:, you need to access them from Z:.

The **%f** is a way of referring to the file name. It will be automatically replaced by the name of whichever file you clicked on.

So Z:%f is just a path to the file you're trying to open. It will be completed automatically, so you don't need to change anything about it. I'm not sure why so many quotes are needed though, just leave them be.

---

### Post by PayPaul on 2011-09-26
I have another machine running Ubuntu with the Classic interface. I've tried to install Wine and it does show Wine is installed. However, unlike in my machine running Unity, I don't get right click choice to install a windows exe file with Wine. In my unity version I don't have to use any of the above suggested command lines to open and install a windows program in Wine. How does the right click option get enabled?

---

