---
title: "Does Wine recognize .bat files?"
date: 2007-12-03
forum: Wine
---

### Post by s3a on 2007-12-03
Does it?? Because if it doesn't, I can't run this game...

---

### Post by hikaricore on 2007-12-03
I've had mixed results.

Why don't you just run the commands in the batch files manually?
I'm not entirely sure why a ***dows based game would need a batch file, but eh it happens.

---

### Post by cogadh on 2007-12-03
If you run "wineconsole" in the terminal, it opens a Windows command prompt. You might have some luck running a .bat in that.

---

### Post by LaRoza on 2007-12-03
> **s3a said:**
> Does it?? Because if it doesn't, I can't run this game...

Post the contents of this file.

---

### Post by hikaricore on 2007-12-03
5 bucks says it's an lzh decryption script for a scene packed game...

lol

but seriously if it is, don't bother posting it.  ^_^
otherwise, go for it.

---

### Post by s3a on 2007-12-30
> **cogadh said:**
> If you run "wineconsole" in the terminal, it opens a Windows command prompt. You might have some luck running a .bat in that.

After doing wineconsole, what do I do in order to start the .bat? I already tried right clicking on the file and selecting open with winefile and wineconsole. Does this mean I won't be able to start the file without Windows?!?

---

### Post by s3a on 2007-12-30
I think that downloading DOSBOX will help me run this. I will post results...

---

### Post by s3a on 2007-12-30
Unfortunately, I don't know how to use DOSBOX...:'(, help?

---

### Post by b0rka7a on 2007-12-31
Open wineconsole and navigate to the directory where the .bat file is. Start it by typing "start bat-file.bat" (for example "start test.bat"), but I'm not sure that the command is "start". Tell me if it worked.

---

### Post by darkenigma02 on 2008-02-05
Ok. I'm sorry to have revived this thread, but this seems to be the only thing working for me.

When I run my .bat with start, it needs to open another program, and it doesnt work when I do the start.

The code in the .bat is this-
```

@title Sinscape Client

@java -cp ./SinScape.jar -Xmx500m client

@pause

```

The CMD For the Client will open, but the sinscape.jar thing wont.

[code]
Z:\home\kyle\Desktop\Sinscape2.1>start run.bat
fixme:exec:SHELL_execute flags ignored: 0x00000500
Z:\home\kyle\Desktop\Sinscape2.1>

---

### Post by doorknob60 on 2008-02-05
Sounds like a 3rd party Moparscape/Runescape type thing to me :P You don't need the batch file, try just right clicking the .jar file in nautilus and opening it with Java Runtime. (Meaning not using WINE)

---

### Post by darkenigma02 on 2008-02-06
> **doorknob60 said:**
> Sounds like a 3rd party Moparscape/Runescape type thing to me :P You don't need the batch file, try just right clicking the .jar file in nautilus and opening it with Java Runtime. (Meaning not using WINE)

You guess right.

But, I dont understand what to do.. can anybody PLEASE walk me through it?

---

### Post by vonranke on 2009-09-17
Yes it does, and here is how to run whatever you want to run (or at least how I did it).

```
wineconsole cmd
```Then navigate to your directory (instead of ls, use dir to see what is in your current directory).

Then to run the .bat file

```
foo.bat
```

---

### Post by The Question on 2009-10-23
Ok, so I was having the same problem and I did that.  However, it seems to run the batch file and exit immediately when it is supposed to give me a choice of 1,2,3 or X.

Here is snip of batch file:

```
echo Please choose from the list below:

echo.

echo 1. Part 1

echo 2. Part 2

echo 3. Part 3

echo X. Exit without Loading

echo.

choice /c:123X Enter your selection



if errorlevel 10 goto done

if errorlevel 9 goto done

if errorlevel 8 goto done

if errorlevel 7 goto done

if errorlevel 6 goto done

if errorlevel 5 goto done

if errorlevel 4 goto done

if errorlevel 3 goto Three

if errorlevel 2 goto Two

if errorlevel 1 goto One



:One

echo.

echo Part 1

copy events1.txt events.txt

copy rules1.txt rules.txt

copy game1.txt game.txt

copy labels1.txt labels.txt

copy title1.gif title.gif

copy units1.gif units.gif

DELEVENT game1.sav

goto done
```

I can do the copying myself of course, but not sure about the DELEVENT command.

So anybody know how to get this batch file working?

---

### Post by hikaricore on 2009-10-23
Is there some reason you can't just make a bash script out of this?
It doesn't seem too terrribly complex.

---

### Post by sub.mesa on 2009-11-15
The answer is so simple, people finding this using google just want to know how to run .bat files using Wine, so here goes:

wineconsole start file.bat

Replace file.bat with the name of the batch file, make sure you are in the right directory where the file is located.

---

### Post by chaoman on 2009-12-06
make a bash script that says

<application used for running java> filename.jar


where, of course, you erase "<application used for running java>" with your application's name recognized by the command line. then you can just run that OR you can just run the .jar, duh.



edit reason: misspellings

---

### Post by joes7 on 2009-12-07
Sometimes, if you are lucky. Why don't you install Virtual Machine with Windows? It will be much easier.

---

### Post by lisati on 2009-12-07
> **joes7 said:**
> Sometimes, if you are lucky. Why don't you install Virtual Machine with Windows? It will be much easier.

Why a virtual machine? If I read the post that [this post]("http://ubuntuforums.org/showpost.php?p=4284164&postcount=12") is a response to correctly, there's a simpler solution, for which instructions were **clearly** given and apparently not understood.

---

### Post by ozzman47274 on 2013-04-22
try to right click on it and open with wine.....

---

### Post by wildmanne39 on 2013-04-22
Thread closed. Please do not post in old threads.

---

