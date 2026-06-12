---
title: "Wine not opening .exe files"
date: 2008-10-11
forum: Wine
---

### Post by Tomanderland on 2008-10-11
Heya,

I just installed wine onto Hardy and I have wine tricks and all that but when i try opening a exe files by double clicking it or using terminal it just doesnt open.

I am trying to install macromedia studio 8, ive tried creative suite (it worked when I used to use ubuntu a few months ago but not now) and photoshop cs2.

The following comes up in terminal
maitland@maitland-laptop:/media/cdrom0$ wine install studio 8.exe
wine: could not load L"C:\\windows\\system32\\install.exe": Module not found

But sometimes it doesnt come up with an error but still nothing happens.. and there have been other times where it says something about windows installer..

Anyone have any idea? I'm not very experienced with Wine

Thanks!

---

### Post by Patb on 2008-10-11
Tomanderland, in the terminal try:
```
wine "full_name_of_the_exe_file"
```
I'm not sure of the exact name of your exe file.  Include the inverted commas to avoid confusion over the spaces. 

Cheers, Pat.

---

### Post by ajackson on 2008-10-11
Try right-clicking on it and seeing what the default open with is, it might be mono or it might be nothing at all but you can select open with and choose wine.

---

### Post by SunnyRabbiera on 2008-10-11
did you try to configure wine?
There is a tool in your menu called configure wine, it might help.

---

### Post by Tomanderland on 2008-10-11
Thanks for everyone's help

Pat, I tried that it came up with this, still no result.
```
maitland@maitland-laptop:/media/cdrom0$ wine "install studio 8.exe"
wine: could not load L"D:\\install studio 8.exe": Module not found
```


Also, the right click menu opens with wine windows emulator, clicked it nothing happened and I havent been able to find anything in the config thing that might help.. Am i missing a wine file or something?

Tom

---

### Post by jacksaff on 2008-10-11
> **Tomanderland said:**
> Heya,

maitland@maitland-laptop:/media/cdrom0$ wine install studio 8.exe
wine: could not load L"C:\\windows\\system32\\install.exe": Module not found



Your syntax is wrong. You are telling wine to run a program called "install". 
You don't need an install command for wine. Just run the .exe file (from the correct location of course).

wine studio8.exe

You might also have problems with the spaces. In the command above you have studio 8.exe
The shell interprets this as two things, studio and 8.exe, which is why you shouldn't use spaces in file names in unix. If the file is actually called studio 8.exe (with a space) then try:
wine 'studio 8.exe'
This will tell the shell to treat the space as part of the text rather than as a separator between commands.

---

### Post by hmygf on 2008-10-11
paypal  cheaper  china wholesaler  Air Force one 25th  women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler  Air Force one 25th  women trainers  shoes (paypal accept)(www clothes-sneaker-wholesale
com ) 
paypal  cheaper  china wholesaler  Air Force one 25th  women trainers  shoes (paypal accept)(www clothes-sneaker-wholesale
com ) 
paypal  cheaper  china wholesaler  Air Force one 25th  women trainers  shoes (paypal accept)(www clothes-sneaker-wholesale
com ) 
paypal  cheaper  china wholesaler  Air Force one 25th  women trainers  shoes (paypal accept)(www clothes-sneaker-wholesale
com )

---

### Post by Tomanderland on 2008-10-11
> **jacksaff said:**
> Your syntax is wrong. You are telling wine to run a program called "install". 
You don't need an install command for wine. Just run the .exe file (from the correct location of course).

wine studio8.exe

You might also have problems with the spaces. In the command above you have studio 8.exe
The shell interprets this as two things, studio and 8.exe, which is why you shouldn't use spaces in file names in unix. If the file is actually called studio 8.exe (with a space) then try:
wine 'studio 8.exe'
This will tell the shell to treat the space as part of the text rather than as a separator between commands.

Thanks jacksaff,

the install there is actually part of the exe file name (install studio 8.exe).. I've tried putting the quotations around it a few times and i just keep getting the message i posted above.. should i try copy the whole cd onto my hard drive so i can rename the setup file with no spaces?

---

### Post by hmygf on 2008-10-11
paypal  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com) ) 
paypal  cheaper  china wholesaler Air Max 360  90  LTD 2003  87 95  97 91 89 mans  women  trainers  shoes (paypal accept)
([www.lothes-sneaker-wholesale.com](www.lothes-sneaker-wholesale.com))
paypal  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com) ) 
paypal  cheaper  china wholesaler Air Max 360  90  LTD 2003  87 95  97 91 89 mans  women  trainers  shoes (paypal accept)
([www.lothes-sneaker-wholesale.com](www.lothes-sneaker-wholesale.com))
paypal  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com) ) 
paypal  cheaper  china wholesaler Air Max 360  90  LTD 2003  87 95  97 91 89 mans  women  trainers  shoes (paypal accept)
([www.lothes-sneaker-wholesale.com](www.lothes-sneaker-wholesale.com))
paypal  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com) ) 
paypal  cheaper  china wholesaler Air Max 360  90  LTD 2003  87 95  97 91 89 mans  women  trainers  shoes (paypal accept)
([www.lothes-sneaker-wholesale.com)paypal](www.lothes-sneaker-wholesale.com)paypal)  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com) ) 
paypal  cheaper  china wholesaler Air Max 360  90  LTD 2003  87 95  97 91 89 mans  women  trainers  shoes (paypal accept)
([www.lothes-sneaker-wholesale.com](www.lothes-sneaker-wholesale.com))

---

### Post by hmygf on 2008-10-11
paypal  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler Air Max Tnwomen trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler Air Max Tnwomen trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler Air Max Tnwomen trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler Air Max Tnwomen trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler Air Max Tnwomen trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) paypal  cheaper  china wholesaler Air Jordans (1-23)  DMP women trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com ) 
paypal  cheaper  china wholesaler Air Max Tnwomen trainers  shoes (paypal accept)([www.clothes-sneaker-wholesale](www.clothes-sneaker-wholesale).
com )

---

### Post by ugm6hr on 2008-10-11
Might be easiest to try the GUI way: Right-click the .exe file and select open with Wine.

Did you use the Ubuntu repo version of wine?

If that doesn't work - use terminal, but make sure you have configured your CD drive (/media/cdrom0) as D: (in configure Wine menu).

---

### Post by Tomanderland on 2008-10-11
> **ugm6hr said:**
> Might be easiest to try the GUI way: Right-click the .exe file and select open with Wine.

Did you use the Ubuntu repo version of wine?

If that doesn't work - use terminal, but make sure you have configured your CD drive (/media/cdrom0) as D: (in configure Wine menu).

Ive tried right-clicking.. nothing happens not even an error message. Wine is configured right too, cd drive =D: and ive tried terminal and it just comes up with an error message saying it cant find the module.

---

### Post by Patb on 2008-10-11
> **Tomanderland said:**
> should i try copy the whole cd onto my hard drive so i can rename the setup file with no spaces?
Worth a try Tomerland, just in case the location on your CD is the source of the problem. But I would have expected the thing to work with several of the methods you've tried already. 

Good luck, Pat.

---

### Post by sh_son on 2008-10-11
I think if you have space/gap between words on the file name,
wine recognizes the first word and ignores the second word.

Well, I think :)

---

### Post by david_kt on 2008-10-11
> **Tomanderland said:**
> Ive tried right-clicking.. nothing happens not even an error message. Wine is configured right too, cd drive =D: and ive tried terminal and it just comes up with an error message saying it cant find the module.

Please try below method:

1. Open terminal and type 
```
wine <space>
```

but DO NOT press <enter> yet.

2. Open nautilus and browse to the exe file you want to run. Drag and drop that exe file to the terminal, and it would become:

```
wine '/path/to/your/exe/file/exe_file.exe'
```

and then press <enter>.

DK

---

### Post by directhex on 2008-10-11
note: the correct procedure is to either escape spaces (using "\ ") or use speech marks:

```
directhex@mortos:/tmp$ wine copy\ of\ sol.exe 
directhex@mortos:/tmp$ wine "copy of sol.exe"
```

---

### Post by robopaul9 on 2009-01-26
Go to the Applications menu -> Wine -> Browse C:\ Drive. Then copy your file to this location. Right click the file, and select Open with Wine.

---

### Post by pwnflakes on 2009-01-27
hello
first of all i am really new with ubuntu 
i have same problem like Tomanderland
im trying to install Garena.exe with wine but it says Garena.exe is running already huh
i try with other exe files but they wont start
when i try to start them with double click or right click -> open with wine just nothing happen no error
when i try to start it by terminal it says 

wine: could not load L"C:\\windows\\system32\\Garena.exe": Module not found
[email]whatever@whatever-desktop:~/.wine[/email]/drive_c$ 

i try everything what i understand in this thread but no1 helps

sry for my bad english
and pls dont blame me this is my first try with linux :)

---

### Post by ugm6hr on 2009-01-27
> **pwnflakes said:**
> im trying to install Garena.exe with wine 

I suspect it won't work:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13086&iTestingId=28925](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13086&iTestingId=28925)
[http://www.garena.com/forum/redirect.php?tid=166599&goto=lastpost](http://www.garena.com/forum/redirect.php?tid=166599&goto=lastpost)

---

### Post by directhex on 2009-01-27
> **julian5 said:**
> If you are facing problem to open .exe file by Wine, you can use VirtualBox.

It is easily retrievable from the repository.

--Julian

And buy a retail Windows license

---

### Post by webbdawg on 2009-11-09
I have been fighting trying to get my Studio 8 to install. I got my older version of DW installed but I cannot get Studio 8 going.

SO I installed the latest version of Wine and now I get an Access Denied error when I try to open the exe with wine.

The more I try to work with Linux it is More obvious why it is not being adopted as an OS.

Programmers do not write mainstream programs for it so it is virtually unusable by those who need programs to work.

---

### Post by david_kt on 2009-11-09
> **webbdawg said:**
> I have been fighting trying to get my Studio 8 to install. I got my older version of DW installed but I cannot get Studio 8 going.

SO I installed the latest version of Wine and now I get an Access Denied error when I try to open the exe with wine.

The more I try to work with Linux it is More obvious why it is not being adopted as an OS.

Programmers do not write mainstream programs for it so it is virtually unusable by those who need programs to work.

Try below instruction:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11368&iTestingId=38624](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11368&iTestingId=38624)

DK

---

### Post by directhex on 2009-11-09
> **webbdawg said:**
> I have been fighting trying to get my Studio 8 to install. I got my older version of DW installed but I cannot get Studio 8 going.

SO I installed the latest version of Wine and now I get an Access Denied error when I try to open the exe with wine.

The more I try to work with Linux it is More obvious why it is not being adopted as an OS.

Programmers do not write mainstream programs for it so it is virtually unusable by those who need programs to work.

You're complaining that apps designed for one OS don't work in another

You've bought a Tesla Roadster, and are now complaining because you can't find the petrol intake

---

### Post by webbdawg on 2009-11-09
> **directhex said:**
> You're complaining that apps designed for one OS don't work in another

You've bought a Tesla Roadster, and are now complaining because you can't find the petrol intake

No, I said why can't mainstream programs be written for all the OS's

All computers have a hard drive, either an intel or amd cpu and memory.

Microsoft, Apple and the Linux community will end up destroying personal computing because of all the stupid incompatibility.

---

### Post by hikaricore on 2009-11-09
> **webbdawg said:**
> No, I said why can't mainstream programs be written for all the OS's

All computers have a hard drive, either an intel or amd cpu and memory.

Microsoft, Apple and the Linux community will end up destroying personal computing because of all the stupid incompatibility.

Uhhh.... :lolflag: welcome to the Internet.

---

